---
title: ICorDebugMutableDataTarget – rozhraní
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: 682e927388d3392d970338314f97d46c9e57e760
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139339"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget – rozhraní
Rozšiřuje rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) pro podporu proměnlivých datových cílů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ContinueStatusChanged – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Změní stav pokračování pro nedokončenou událost ladění v zadaném vlákně.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Nastaví kontext (hodnoty registru) pro vlákno.|  
|[WriteVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Zapíše paměť do cílového adresního prostoru procesu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) může být implementováno pomocí ladicích nástrojů, které chtějí upravit cílový proces (například pro provádění živých invazivních ladění).  
  
 Všechny tyto metody jsou nepovinné v tom smyslu, že nedojde ke ztrátě žádné základní funkce ladění založené na kontrole tím, že neimplementuje toto rozhraní nebo nezpůsobí volání těchto metod.  Jakékoli selhání `HRESULT` z těchto metod bude rozšířeno jako `HRESULT` z volání metody ICorDebug.  
  
 Všimněte si, že jedno volání metody ICorDebug může mít za následek vícenásobné mutace a že neexistuje žádný mechanismus pro zajištění souvisejících mutací, které jsou prováděny jako transakční (vše-nebo-None).  To znamená, že pokud po úspěšném pokusu o provedení jiné (pro stejné volání ICorDebug) dojde k chybě, cílový proces může být ponechán v nekonzistentním stavu a ladění může být nespolehlivé.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
