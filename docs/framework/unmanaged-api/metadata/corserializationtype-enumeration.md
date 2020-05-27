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
ms.openlocfilehash: 649a9159f99afa64615c40c23a98a80318ae0d7f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009168"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType – výčet
Určuje, jak je objekt serializován modulem CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
|Člen|Description|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|Serializace objektu není definována.|  
|`SERIALIZATION_TYPE_BOOLEAN`|Objekt je serializován jako typ Boolean.|  
|`SERIALIZATION_TYPE_CHAR`|Objekt je serializován jako typ znaku.|  
|`SERIALIZATION_TYPE_I1`|Objekt je serializován jako celé číslo se znaménkem na 1 bajt.|  
|`SERIALIZATION_TYPE_U1`|Objekt je serializován jako celé číslo s nepodepsaným 1 bajtem.|  
|`SERIALIZATION_TYPE_I2`|Objekt je serializován jako celé číslo se znaménkem na dvou bajtech.|  
|`SERIALIZATION_TYPE_U2`|Objekt je serializován jako celé číslo bez znaménka 2 bajt.|  
|`SERIALIZATION_TYPE_I4`|Objekt je serializován jako celé číslo se znaménkem na 4 bajt.|  
|`SERIALIZATION_TYPE_U4`|Objekt je serializován jako celé číslo bez znaménka 4 bajty.|  
|`SERIALIZATION_TYPE_I8`|Objekt je serializován jako přihlášené celé číslo se znaménkem na 8 bajtů.|  
|`SERIALIZATION_TYPE_U8`|Objekt je serializován jako celé číslo bez znaménka na 8 bajtů.|  
|`SERIALIZATION_TYPE_R4`|Objekt je serializován jako plovoucí desetinná čárka (4 bajt).|  
|`SERIALIZATION_TYPE_R8`|Objekt je serializován jako plovoucí desetinná čárka (8 bajtů).|  
|`SERIALIZATION_TYPE_STRING`|Objekt je serializován jako typ System. String.|  
|`SERIALIZATION_TYPE_SZARRAY`|Objekt je serializován jako jednorozměrné, nulové pole s nižším rozsahem.|  
|`SERIALIZATION_TYPE_TYPE`|Objekt je serializován jako obecný typ.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Objekt je serializován jako objekt s příznakem.|  
|`SERIALIZATION_TYPE_FIELD`|Objekt je serializován jako pole.|  
|`SERIALIZATION_TYPE_PROPERTY`|Objekt je serializován jako vlastnost.|  
|`SERIALIZATION_TYPE_ENUM`|Objekt je serializován jako výčet.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
