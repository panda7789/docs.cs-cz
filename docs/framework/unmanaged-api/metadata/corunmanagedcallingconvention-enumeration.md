---
title: "CorUnmanagedCallingConvention – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 446a948c8809d9f098ede8fbb9b426f6169ce812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention – výčet
Určuje konvencí volání nespravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|Jazyk C volání konvence.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|Standardní konvence volání.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|"Tato" konvence volání.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|"Rychlé" konvence volání.|  
|`IMAGE_CEE_CS_CALLCONV_C`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Nepoužívá se.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR nepodporuje "rychlé" konvence volání v rozhraní .NET Framework verze 1.0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
