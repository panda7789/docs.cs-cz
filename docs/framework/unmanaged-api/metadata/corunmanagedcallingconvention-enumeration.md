---
title: CorUnmanagedCallingConvention – výčet
ms.date: 03/30/2017
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
ms.openlocfilehash: 58d30e71929d314ee36adb9f83270858ff8a161b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442448"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention – výčet
Určuje konvence volání pro nespravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|Člen|Popis|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|Konvence volání jazyka C.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|Standardní konvence volání.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|Konvence volání "This".|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|Konvence volání "Fast".|  
|`IMAGE_CEE_CS_CALLCONV_C`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Nepoužívá se.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR nepodporuje konvenci volání "Fast" v .NET Framework verze 1,0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
