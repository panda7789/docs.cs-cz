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
ms.openlocfilehash: f35e979a5107064d2987a385a989075ef71283ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098862"
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
|`TryOffset`|Posun v bajtech `try` bloku od začátku těla metody.|  
|`TryLength`|Délka bloku `try` v bajtech.|  
|`HandlerOffset`|Umístění obslužné rutiny pro tento blok `try`.|  
|`HandlerLength`|Velikost kódu obslužné rutiny v bajtech|  
|`ClassToken`|Token metadat pro obslužnou rutinu výjimky založené na typu.|  
|`FilterOffset`|Posun v bajtech od začátku těla metody pro obslužnou rutinu výjimky na základě filtru.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [GetEHClauses –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) vrací pole hodnot `CoreDebugEHClause`.  
  
 Informace o klauzuli EH jsou definovány specifikací CLI. Další informace naleznete v tématu [Standard ECMA-355: Common Language Infrastructure (CLI), 6. verze](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Pole `flags` může obsahovat následující příznaky. Všimněte si, že nejsou definovány v CorDebug. idl nebo CorDebug. h.  
  
|příznaků|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Typová klauzule Exception|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Filtr výjimky a klauzule obslužné rutiny.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|Klauzule `finally`.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Klauzule Fault (`finally` klauzule, která je volána pouze v případě, že je vyvolána výjimka).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetEHClauses – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
