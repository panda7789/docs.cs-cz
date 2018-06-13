---
title: ICorDebugMutableDataTarget rozhraní
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 677db647320ff4014b791502b7ac1b261378c8dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419527"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget rozhraní
Rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro podporu měnitelný datový cíle.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ContinueStatusChanged – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Změní stav pokračování události nezpracovaných ladění na zadané vlákno.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Nastaví kontext (hodnot registru) vlákna.|  
|[WriteVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Zapíše paměti do adresního prostoru procesu cíl.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření pro [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní může být implementováno pomocí ladicích nástrojů, které chcete upravit Cílový proces (například k provedení invazivní ladění).  
  
 Všechny tyto metody jsou volitelné v tom smyslu, že žádné jádra na základě kontroly ladění funkce budou ztraceny není implementace tohoto rozhraní nebo selhání volání těchto metod.  Jakákoli chyba `HRESULT` z těchto metod rozšíří na jako `HRESULT` z volání metody ICorDebug.  
  
 Všimněte si, že jednoho volání metody ICorDebug může mít za následek více mutací a že neexistuje žádný mechanismus pro zajištění související mutací použijí transakčně (all-or-none).  To znamená, že pokud mutace selže po jiné (pro stejné volání ICorDebug) proběhlo úspěšně, tento cílový proces může být ponecháno v nekonzistentním stavu a ladění stane nespolehlivou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
