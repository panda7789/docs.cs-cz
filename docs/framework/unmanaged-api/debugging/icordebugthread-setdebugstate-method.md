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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66f60b2342b6ff64f1329cbe57032291d5139384
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770599"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState – metoda
Sets flags that describe the debugging state of this ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `state`  
 [in] Bitová kombinace hodnot cordebugthreadstate – výčet, které určují stav ladění tohoto vlákna.  
  
## <a name="remarks"></a>Poznámky  
 `SetDebugState` Nastaví aktuální stav ladění vlákna. (The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) Běžné hodnoty je THREAD_RUNNING. Pouze ladicí program může ovlivnit stav ladění vlákna. Ladění stavy poslední napříč bude pokračovat, pokud chcete zachovat vlákno pokračuje THREAD_SUSPENDed přes více, abyste mohli nastavit jednou a po tomto datu není nutné se starat o něm. Pozastavení vlákna a procesu obnovení může způsobit zablokování, když je nepravděpodobné, že by obvykle. Toto je vnitřní kvalitu vláken a procesů a podle návrhu. Ladicí program můžete asynchronně přerušit a pokračování vláken pro přerušení zablokování. Pokud je stav vlákna uživatele USER_UNSAFE_POINT, může zablokovat vlákno uvolňování paměti (GC). To znamená, že pozastaveného vlákna má mnohem vyšší pravděpodobnost způsobit zablokování. To nemusí ovlivnit ladění, které už ve frontě událostí. Proto by měl ladicí program vyprázdnění fronty celá událost (voláním [icordebugcontroller::hasqueuedcallbacks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) před pozastavování a obnovování vláken. Jinak se může zobrazit události na vlákně, které se domnívá, že již byla pozastavena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
