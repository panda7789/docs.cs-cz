---
title: "ICorDebugThread::SetDebugState – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.SetDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 01f84c7126a4017a8d3b199f94eb497fae8e1a49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState – metoda
Nastaví příznaky, které popisují ladění stav této ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `state`  
 [v] Bitové kombinace hodnot výčtu CorDebugThreadState, které určují ladění stav tohoto podprocesu.  
  
## <a name="remarks"></a>Poznámky  
 `SetDebugState`Nastaví aktuální stav ladění vlákno. ("Aktuální ladění stavu" představuje stav ladění Pokud proces dál, nikoli skutečné aktuální stav.) Normální hodnota pro tento je THREAD_RUNNING. Pouze ladicí program může ovlivnit stav ladění vlákna. Ladění stavy poslední napříč pokračuje, takže pokud chcete zachovat vlákno THREAD_SUSPENDed přes více dál, můžete nastavit jednou a následně není nutné se obávat ho. Pozastavení vláken a proces obnovení může způsobit zablokování, když je obvykle nepravděpodobné. Toto je vnitřní kvalita vláken a procesů a podle návrhu. Ladicí program můžete asynchronně přerušení a obnovit vláken pro přerušení k zablokování. Pokud stav uživatele vlákna zahrnuje USER_UNSAFE_POINT, může blokovat vlákno uvolnění paměti (GC). To znamená, že pozastavené vlákno nemá mnohem vyšší možnost, že vzájemné zablokování. To nemusí ovlivnit ladění, které už ve frontě událostí. Ladicí program by měl proto vyprazdňování celá událost fronty (voláním [icordebugcontroller::hasqueuedcallbacks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) před přechodem do režimu spánku nebo obnovování vláken. Jinak obdržet události na vlákno, které dochází k závěru, že je již pozastaveno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
