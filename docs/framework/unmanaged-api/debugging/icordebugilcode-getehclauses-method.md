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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8eca550130a22532cb781e09ec59c60c11a5ba33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416033"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Vrací ukazatel na seznam klauzule (EH), které jsou definované pro tento zprostředkující jazyk (IL) zpracování výjimek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cClauses`  
 [v] Úložnou kapacitu `clauses` pole. Další informace naleznete v části Poznámky.  
  
 `pcClauses`  
 [out] Číslo, pro které informace jsou zapsány do klauzule `clauses` pole.  
  
 klauzule  
 [out] Pole [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objekty, které obsahují informace o zpracování klauzule definované pro tento IL výjimek.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `cClauses` je 0 a `pcClauses` jinou hodnotu než**null**, `pcClauses` je nastaven na počet dostupných zpracování klauzule výjimek. Pokud `cClauses` je nulová, představuje kapacitu úložiště `clauses` pole. Po návratu metody `clauses` obsahuje maximálně `cClauses` položky, a `pcClauses` je nastaven na počet klauzulí ve skutečnosti zapsána do `clauses` pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugILCode – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [CorDebugEHClause – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
