---
title: "AssemblyBindInfo 结构"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdf76b95e80d5d4d96d2b5ed8236018147167905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo 结构
提供有关引用程序集的详细的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`dwAppDomainId`|唯一标识符`IStream`返回通过调用[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)，从引用的程序集即要加载。|  
|`lpReferencedIdentity`|引用的程序集的唯一标识符。|  
|`lpPostPolicyIdentity`|之后的任何绑定策略值的应用程序引用的程序集标识符。|  
|`ePolicyLevel`|之一[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，用于指示哪些版本控制策略，如果有的话，应该应用于引用的程序集。|  
  
## <a name="remarks"></a>备注  
 主机提供的唯一标识符`dwAppDomainId`公共语言运行时 (CLR)。 调用了`IHostAssemblyStore::ProvideAssembly`返回时，运行时使用标识符来确定是否的内容`IStream`已映射。 如果是这样，则运行时将加载现有的副本，而不是无需重新映射流。 运行时还使用此标识符作为查找键以从返回的流调用[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)。 因此，标识符必须是唯一为模块请求和程序集请求。  
  
## <a name="requirements"></a>惠?  
 **平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.idl  
  
 **库：**作为 MSCorEE.dll 中的资源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅  
 [承载结构](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [ICLRAssemblyIdentityManager 接口](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList 接口](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager 接口](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore 接口](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [ModuleBindInfo 结构](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
