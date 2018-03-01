---
title: "CorCallingConvention – výčet"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 154fbcc393bb56ab2c249a4928a4451dced9761a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention – výčet
Obsahuje hodnoty, které popisují typy pravidel pro volání, které jsou vytvářeny ve spravovaném kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Označuje, že metoda přijímá proměnný počet parametrů.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Označuje, že volání je pro pole.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Označuje, že volání je místní metodě.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Označuje, že volání je na vlastnost.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Označuje, že je volání nespravovaného.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Určuje, vytváření instancí obecná metoda.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Označuje volání PInvoke 64-bit metodu, která přebírá proměnné počet parametrů.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Popisuje neplatnou hodnotu 4 bitů.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Označuje, že konvence volání je popsán dolní čtyři bits.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Určuje, zda popisuje hlavní verze `this` parametr.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Určuje, že `this` parametr je explicitně popsáno v podpis.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Určuje podpis obecná metoda s explicitní počet argumentů typu. To předchází počet obyčejnou parametrů.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
