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
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008947"
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
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
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
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
