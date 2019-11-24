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
Specifies the calling conventions for unmanaged code.  
  
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
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|The C language calling convention.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|The standard calling convention.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|The "this" calling convention.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|The "fast" calling convention.|  
|`IMAGE_CEE_CS_CALLCONV_C`|Not used.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Not used.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Not used.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Not used.|  
  
## <a name="remarks"></a>Poznámky  
 The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
