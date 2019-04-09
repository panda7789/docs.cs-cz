---
title: ICorDebugMutableDataTarget – rozhraní
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8b33b07e7c9f83f5874dea1455cd70dcc3206de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105934"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget – rozhraní
Rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro podporu proměnlivé datové cíle.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ContinueStatusChanged – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Změní stav pokračování pro zbývající ladění události u zadaného vlákna.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Nastaví kontext (hodnot registru) pro vlákno.|  
|[WriteVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Zapíše paměti do adresového prostoru cílového procesu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní může být implementována ladicí nástroje, které chcete upravit Cílový proces (například k provádění invazivní ladění).  
  
 Všechny tyto metody jsou volitelné v tom smyslu, že žádná základní na základě kontroly ladění funkce je ztraceny bez implementace tohoto rozhraní nebo selhání volání těchto metod.  Jakékoli neúspěchy `HRESULT` z těchto metod bude šířit jako `HRESULT` z volání metody ICorDebug.  
  
 Mějte na paměti, že jedním voláním metody ICorDebug může vést k více mutace a že neexistuje žádný mechanismus pro zajištění související mutace použijí transakčně (all-or-none).  To znamená, že pokud mutaci selže po jiné (pro stejné volání ICorDebug) byly úspěšné, Cílový proces se může stát zůstane v nekonzistentním stavu a ladění může být nespolehlivá.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
