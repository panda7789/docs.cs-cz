---
title: Struktura CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 839e698c8921f916fad174bae4f4cc8bb4d02994
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157323"
---
# <a name="cordebugehclause-structure"></a>Struktura CorDebugEHClause
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Představuje výjimku zpracování – klauzule (EH) pro danou část kódu (IL intermediate language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`Flags`|Bitové pole, která popisuje informace o výjimce v klauzuli EH. Další informace najdete v části poznámky.|  
|`TryOffset`|Posun v bajtech, nástroje `try` bloku od samého začátku tělo metody.|  
|`TryLength`|Délka v bajtech, nástroje `try` bloku.|  
|`HandlerOffset`|Umístění obslužné rutiny pro tuto `try` bloku.|  
|`HandlerLength`|Velikost v bajtech kód obslužné rutiny.|  
|`ClassToken`|Token metadat pro obslužnou rutinu na základě typu výjimky.|  
|`FilterOffset`|Posun v bajtech od začátku tělo metody obslužné rutiny na základě filtru výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 Pole `CoreDebugEHClause` hodnoty vrácené [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) metody.  
  
 Klauzule informace EH je definován specifikací CLI. Další informace najdete v tématu [Standard ECMA-355: Common Language Infrastructure (CLI), 6 Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 `flags` Pole může obsahovat následující příznaky. Všimněte si, že nejsou definovány v CorDebug.idl nebo CorDebug.h.  
  
|Příznak|Value|Popis|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Klauzule typovou výjimku.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Výjimka filtr a obslužné rutiny klauzuli.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|A `finally` klauzuli.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Klauzule fault ( `finally` klauzuli, která je volána, pouze když je vyvolána výjimka).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetEHClauses – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
