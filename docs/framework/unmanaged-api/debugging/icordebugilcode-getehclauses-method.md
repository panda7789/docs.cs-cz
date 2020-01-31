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
ms.openlocfilehash: ac9a4e4b54b302afeae4ede1dd574c15ded3ff12
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788604"
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
 pro Kapacita úložiště pole `clauses`. Další informace naleznete v části Poznámky.  
  
 `pcClauses`  
 mimo Počet klauzulí, o které se zapisují informace do pole `clauses`.  
  
 platný  
 mimo Pole objektů [CorDebugEHClause](cordebugehclause-structure.md) , které obsahují informace o klauzulích zpracování výjimek definovaných pro tento Il.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je `cClauses` 0 a `pcClauses` není**null**, `pcClauses` je nastaveno na počet dostupných klauzulí zpracování výjimek. Pokud `cClauses` není nula, představuje kapacitu úložiště `clauses` pole. Když metoda vrátí, `clauses` obsahuje maximálně `cClauses` položek a `pcClauses` je nastaveno na počet klauzulí vlastněných v poli `clauses`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILCode – rozhraní](icordebugilcode-interface.md)
- [CorDebugEHClause – struktura](cordebugehclause-structure.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
