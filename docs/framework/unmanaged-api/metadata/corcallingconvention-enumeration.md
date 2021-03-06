---
title: CorCallingConvention – výčet
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 310319e8fefe80017c58706e2beaee5eb1e78422
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007899"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention – výčet
Obsahuje hodnoty, které popisují typy konvencí volání, které jsou vytvořeny ve spravovaném kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Označuje výchozí konvenci volání.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Označuje, že metoda přebírá proměnný počet parametrů.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Označuje, že volání je na pole.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Označuje, že volání je místní metoda.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Označuje, že volání je na vlastnost.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Indikuje, že volání je nespravované.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Označuje instanci generické metody.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Označuje 64 volání PInvoke do metody, která přebírá proměnný počet parametrů.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Popisuje neplatnou hodnotu 4 bitů.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Označuje, že konvence volání je popsána v dolních čtyřech bitech.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Označuje, že horní bit popisuje `this` parametr.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Označuje, že `this` parametr je explicitně popsán v signatuře.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Označuje podpis obecné metody s explicitním počtem argumentů typu. Předchází běžný počet parametrů.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
