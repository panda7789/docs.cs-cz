---
title: COR_FIELD – struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
ms.openlocfilehash: 78e34d9d33d34047e3ebd2effb4894bc7b709585
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132359"
---
# <a name="cor_field-structure"></a>COR_FIELD – struktura
Poskytuje informace o poli v objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`token`|Token `mdFieldDef`, který lze použít k získání informací o poli.|  
|`offset`|Posun v bajtech k datům pole v objektu.|  
|`id`|Hodnota [COR_TYPEID](cor-typeid-structure.md) , která identifikuje typ tohoto pole.|  
|`fieldType`|Hodnota výčtu CorElementType –, která určuje typ pole.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
