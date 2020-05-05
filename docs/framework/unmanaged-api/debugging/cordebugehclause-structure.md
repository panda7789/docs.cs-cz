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
ms.openlocfilehash: a889d6ba00c4a0eb96a9923a7dbe52f3b93aaba5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795958"
---
# <a name="cordebugehclause-structure"></a>Struktura CorDebugEHClause
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Představuje klauzuli zpracování výjimek (EH) pro danou část kódu přestupného jazyka (IL).  
  
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
|`Flags`|Bitové pole, které popisuje informace o výjimce v klauzuli EH. Další informace najdete v části poznámky.|  
|`TryOffset`|Posun `try` bloku v bajtech od začátku těla metody.|  
|`TryLength`|Délka `try` bloku v bajtech.|  
|`HandlerOffset`|Umístění obslužné rutiny pro tento `try` blok.|  
|`HandlerLength`|Velikost kódu obslužné rutiny v bajtech|  
|`ClassToken`|Token metadat pro obslužnou rutinu výjimky založené na typu.|  
|`FilterOffset`|Posun v bajtech od začátku těla metody pro obslužnou rutinu výjimky na základě filtru.|  
  
## <a name="remarks"></a>Poznámky  
 Pole `CoreDebugEHClause` hodnot je vráceno metodou [GetEHClauses –](icordebugilcode-getehclauses-method.md) .  
  
 Informace o klauzuli EH jsou definovány specifikací CLI. Další informace naleznete v tématu [Standard ECMA-355: Common Language Infrastructure (CLI), 6. verze](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 `flags` Pole může obsahovat následující příznaky. Všimněte si, že nejsou definovány v CorDebug. idl nebo CorDebug. h.  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Typová klauzule Exception|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Filtr výjimky a klauzule obslužné rutiny.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|`finally` Klauzule.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Klauzule Fault ( `finally` klauzule, která je volána pouze v případě, že je vyvolána výjimka).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetEHClauses – metoda](icordebugilcode-getehclauses-method.md)
- [Struktury pro ladění](debugging-structures.md)
