---
title: CorSerializationType – výčet
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b1f6be2dac6bc7566852791ac22e495949521c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992638"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType – výčet
Určuje, jak je objekt serializován modul common language runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|Serializace objektu není definováno.|  
|`SERIALIZATION_TYPE_BOOLEAN`|Objekt serializován jako typ Boolean|  
|`SERIALIZATION_TYPE_CHAR`|Objekt serializován jako typ znaku.|  
|`SERIALIZATION_TYPE_I1`|Objekt serializován jako celé číslo se znaménkem 1 bajt.|  
|`SERIALIZATION_TYPE_U1`|Objekt serializován jako celé číslo bez znaménka 1 bajt.|  
|`SERIALIZATION_TYPE_I2`|Objekt serializován jako celé číslo se znaménkem 2 bajtů.|  
|`SERIALIZATION_TYPE_U2`|Objekt serializován jako celé číslo bez znaménka 2 bajtů.|  
|`SERIALIZATION_TYPE_I4`|Objekt serializován jako celé číslo se znaménkem na 4 bajty.|  
|`SERIALIZATION_TYPE_U4`|Objekt serializován jako celé číslo bez znaménka na 4 bajty.|  
|`SERIALIZATION_TYPE_I8`|Objekt serializován jako celé číslo se znaménkem 8 bajtů.|  
|`SERIALIZATION_TYPE_U8`|Objekt serializován jako 8bitové celé číslo bez znaménka.|  
|`SERIALIZATION_TYPE_R4`|Objekt serializován jako plovoucí desetinnou čárkou na 4 bajty.|  
|`SERIALIZATION_TYPE_R8`|Objekt serializován jako plovoucí desetinnou čárkou 8 bajtů.|  
|`SERIALIZATION_TYPE_STRING`|Objekt serializován jako typu System.String.|  
|`SERIALIZATION_TYPE_SZARRAY`|Objekt serializován jako jednorozměrné, nula dolní mez pole.|  
|`SERIALIZATION_TYPE_TYPE`|Objekt serializován jako obecného typu.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Objekt serializován jako objekt příznakem.|  
|`SERIALIZATION_TYPE_FIELD`|Objekt serializován jako pole.|  
|`SERIALIZATION_TYPE_PROPERTY`|Objekt serializován jako vlastnost.|  
|`SERIALIZATION_TYPE_ENUM`|Objekt serializován jako výčet.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
