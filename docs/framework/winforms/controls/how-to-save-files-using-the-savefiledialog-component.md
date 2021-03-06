---
title: "如何：使用 SaveFileDialog 组件保存文件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70301cd3d357ab90ac6e7ed6d76a902107ef5e4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>如何：使用 SaveFileDialog 组件保存文件
<xref:System.Windows.Forms.SaveFileDialog>组件，用户可以浏览文件系统并选择要保存文件。 对话框返回用户在对话框中所选的文件路径和名称。 但是必须编写代码才能真正地将文件写入磁盘。  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a>使用 SaveFileDialog 组件保存文件  
  
-   显示“保存文件”对话框，并调用来方法保存用户选择的文件。  
  
     使用<xref:System.Windows.Forms.SaveFileDialog>组件的<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法以将保存该文件。 此方法提供<xref:System.IO.Stream>可以写入的对象。  
  
     下面的示例使用<xref:System.Windows.Forms.DialogResult>属性来获取该文件的名称和<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法以将保存该文件。 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法提供写入到文件流。  
  
     在下面的示例中，没有<xref:System.Windows.Forms.Button>控件分配给它的映像。 当你单击按钮，<xref:System.Windows.Forms.SaveFileDialog>与允许的类型.gif、.jpeg 和.bmp 文件的筛选器实例化组件。 如果在“保存文件”对话框中选择了此类型的文件，那么按钮的图像将会保存。  
  
    > [!IMPORTANT]
    >  要获取或设置<xref:System.Windows.Forms.FileDialog.FileName%2A>属性，您的程序集需要特权级别授予通过<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>类。 如果在部分信任上下文中运行，该进程可能会因特权不足而引发异常。 有关详细信息，请参阅[代码访问安全性基础知识](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
     该示例假定你的窗体具有<xref:System.Windows.Forms.Button>使用来控制其<xref:System.Windows.Forms.ButtonBase.Image%2A>属性设置为的类型.gif、.jpeg 或.bmp 文件。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog>类的<xref:System.Windows.Forms.FileDialog.FilterIndex%2A>属性 (它，由于继承，属于<xref:System.Windows.Forms.SaveFileDialog>类) 使用基于 1 的索引。 如果要通过编写代码以特定格式保存数据（例如，以纯文本或二进制格式保存文件），那么这一点很重要。 以下示例介绍了该属性。  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     （[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]）将以下代码放在窗体构造函数中以注册事件处理程序。  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     有关编写文件流的详细信息，请参阅<xref:System.IO.FileStream.BeginWrite%2A>和<xref:System.IO.FileStream.Write%2A>。  
  
    > [!NOTE]
    >  某些控件，如<xref:System.Windows.Forms.RichTextBox>控制，必须保存文件的功能。 有关详细信息，请参阅 MSDN 联机库技术文章 [Windows 窗体对话框的基本代码](http://go.microsoft.com/fwlink/?LinkID=102575)中的“SaveFileDialog 组件”部分。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog 组件](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
