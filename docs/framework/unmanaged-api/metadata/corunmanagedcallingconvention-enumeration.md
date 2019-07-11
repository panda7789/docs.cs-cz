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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9206fbde13f457d4b2e2941ee744d645c6df9774
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782000"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention – výčet
Určuje konvence volání nespravovaného kódu.  
  
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
  
|Člen|Popis|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|C jazykové konvence volání.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|Standardní konvence volání.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|"Tento" konvence volání.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|"Rychlé" konvence volání.|  
|`IMAGE_CEE_CS_CALLCONV_C`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Nepoužívá se.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Nepoužívá se.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR nepodporuje "rychlé" konvence volání v rozhraní .NET Framework verze 1.0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
