---
title: ICorDebugThread::SetDebugState – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: 1b2f3feca15bb8add17c9fe70805347b7c6a48ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133422"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState – metoda
Nastaví příznaky, které popisují stav ladění tohoto ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `state`  
 pro Bitová kombinace hodnot výčtu CorDebugThreadState –, která určuje stav ladění tohoto vlákna.  
  
## <a name="remarks"></a>Poznámky  
 `SetDebugState` nastaví aktuální stav ladění vlákna. (Stav "aktuální ladění" představuje stav ladění, pokud proces pokračoval v pokračování, nikoli aktuálním aktuálním stavem.) Normální hodnota tohoto pole je THREAD_RUN. Pouze ladicí program může ovlivnit stav ladění vlákna. Stavy ladění trvají v průběhu několika instancí, takže pokud chcete, aby se THREAD_SUSPENDed vlákno více pokračovalo, můžete ho nastavit jednou a pak se na něj nemusíte starat. Pozastavení vláken a obnovení procesu může způsobit zablokování, i když je obvykle nepravděpodobné. Toto je vnitřní kvalita vláken a procesů a je záměrné. Ladicí program může asynchronně poškodit a obnovit vlákna pro přerušení zablokování. Pokud stav uživatele vlákna zahrnuje USER_UNSAFE_POINT, vlákno může zablokovat uvolňování paměti (GC). To znamená, že pozastavené vlákno má mnohem větší šanci na způsob zablokování. To nemusí mít vliv na události ladění, které jsou už ve frontě. Proto by měl ladicí program Vyprázdnit celou frontu událostí (voláním [ICorDebugController:: HasQueuedCallbacks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) před přerušením nebo pokračováním v vláknech. V opačném případě může obdržet události pro vlákno, u kterého se domnívá, že již byla pozastavena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
