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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 576fb8632818a6b8ffc3e2c0acc50eaafd074de3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766964"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention – výčet
Obsahuje hodnoty, které popisují typy konvence volání, které probíhají ve spravovaném kódu.  
  
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
  
|Člen|Popis|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Určuje výchozí konvenci volání.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Označuje, že tato metoda přebírá proměnný počet parametrů.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Označuje, že volání je k poli.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Označuje, že volání místní metody.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Označuje, že volání na vlastnost.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Označuje, že je volání nespravovaných.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Určuje instance obecné metody.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Označuje volání PInvoke 64-bit na metodu, která přijímá proměnný počet parametrů.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Popisuje neplatnou hodnotu 4-bit.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Určuje, zda konvence volání je popsán dolní čtyři bity.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Označuje, že popisuje hlavní verze `this` parametru.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Označuje, že `this` parametr je explicitně je popsáno v podpisu.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Označuje signaturu obecné metody pomocí explicitní počet argumentů typu. To předchází počet běžných parametrů.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
