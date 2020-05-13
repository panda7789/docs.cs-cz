---
title: ICorDebugILCode::GetEHClauses – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: e1fd68cd079b381d941d416831133c54e49ac48a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210381"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Vrátí ukazatel na seznam klauzulí zpracování výjimek (EH), které jsou definovány pro tento převodní jazyk (IL).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cClauses`  
 pro Kapacita úložiště `clauses` pole. Další informace naleznete v části Poznámky.  
  
 `pcClauses`  
 mimo Počet klauzulí, o které se zapisují informace do `clauses` pole  
  
 platný  
 mimo Pole objektů [CorDebugEHClause](cordebugehclause-structure.md) , které obsahují informace o klauzulích zpracování výjimek definovaných pro tento Il.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `cClauses` je 0 a `pcClauses` není**null**, `pcClauses` je nastaveno na počet dostupných klauzulí zpracování výjimek. Pokud `cClauses` je hodnota nenulová, představuje kapacitu úložiště `clauses` pole. Když metoda vrátí, `clauses` obsahuje maximální počet `cClauses` položek a `pcClauses` je nastaven na počet klauzulí, které jsou ve skutečnosti zapsány do `clauses` pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugILCode](icordebugilcode-interface.md)
- [Struktura CorDebugEHClause](cordebugehclause-structure.md)
- [Debugging – rozhraní](debugging-interfaces.md)
