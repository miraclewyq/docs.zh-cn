---
title: "WAITORTIMERCALLBACK 函数指针"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAITORTIMERCALLBACK
api_location: mscoree.dll
api_type: COM
f1_keywords: WAITORTIMERCALLBACK
helpviewer_keywords: WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 873d2ff489085ec2a0c37be2feeb3e15f61c9227
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="0e95b-102">WAITORTIMERCALLBACK 函数指针</span><span class="sxs-lookup"><span data-stu-id="0e95b-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="0e95b-103">指向通知等待句柄的主机的函数 (<xref:System.Threading.WaitHandle>) 已发出信号或超时。</span><span class="sxs-lookup"><span data-stu-id="0e95b-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="0e95b-104">中已弃用此函数指针[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e95b-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e95b-105">语法</span><span class="sxs-lookup"><span data-stu-id="0e95b-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e95b-106">参数</span><span class="sxs-lookup"><span data-stu-id="0e95b-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="0e95b-107">[in]指向包含在主机定义的信息的对象的指针。</span><span class="sxs-lookup"><span data-stu-id="0e95b-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="0e95b-108">[in]`true`等待句柄操作已超时，如果或`false`如果它已终止。</span><span class="sxs-lookup"><span data-stu-id="0e95b-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e95b-109">备注</span><span class="sxs-lookup"><span data-stu-id="0e95b-109">Remarks</span></span>  
 <span data-ttu-id="0e95b-110">到函数`WAITORTIMERCALLBACK`点是一个回调函数，必须在承载应用程序的编写器实现。</span><span class="sxs-lookup"><span data-stu-id="0e95b-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e95b-111">要求</span><span class="sxs-lookup"><span data-stu-id="0e95b-111">Requirements</span></span>  
 <span data-ttu-id="0e95b-112">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e95b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e95b-113">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e95b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e95b-114">**库：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="0e95b-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0e95b-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e95b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e95b-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e95b-116">See Also</span></span>  
 [<span data-ttu-id="0e95b-117">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="0e95b-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)