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
ms.openlocfilehash: ada120b9cb4100bfadff83d96e0226f911958bf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420762"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="dd7a3-102">ICorDebugThread::SetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="dd7a3-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="dd7a3-103">Nastaví příznaky, které popisují ladění stav této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd7a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd7a3-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd7a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd7a3-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="dd7a3-106">[v] Bitové kombinace hodnot výčtu CorDebugThreadState, které určují ladění stav tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd7a3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd7a3-107">Remarks</span></span>  
 <span data-ttu-id="dd7a3-108">`SetDebugState` Nastaví aktuální stav ladění vlákno.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="dd7a3-109">("Aktuální ladění stavu" představuje stav ladění Pokud proces dál, nikoli skutečné aktuální stav.) Normální hodnota pro tento je THREAD_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="dd7a3-110">Pouze ladicí program může ovlivnit stav ladění vlákna.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="dd7a3-111">Ladění stavy poslední napříč pokračuje, takže pokud chcete zachovat vlákno THREAD_SUSPENDed přes více dál, můžete nastavit jednou a následně není nutné se obávat ho.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="dd7a3-112">Pozastavení vláken a proces obnovení může způsobit zablokování, když je obvykle nepravděpodobné.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="dd7a3-113">Toto je vnitřní kvalita vláken a procesů a podle návrhu.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="dd7a3-114">Ladicí program můžete asynchronně přerušení a obnovit vláken pro přerušení k zablokování.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="dd7a3-115">Pokud stav uživatele vlákna zahrnuje USER_UNSAFE_POINT, může blokovat vlákno uvolnění paměti (GC).</span><span class="sxs-lookup"><span data-stu-id="dd7a3-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="dd7a3-116">To znamená, že pozastavené vlákno nemá mnohem vyšší možnost, že vzájemné zablokování.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="dd7a3-117">To nemusí ovlivnit ladění, které už ve frontě událostí.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="dd7a3-118">Ladicí program by měl proto vyprazdňování celá událost fronty (voláním [icordebugcontroller::hasqueuedcallbacks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) před přechodem do režimu spánku nebo obnovování vláken.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="dd7a3-119">Jinak obdržet události na vlákno, které dochází k závěru, že je již pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="dd7a3-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd7a3-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd7a3-120">Requirements</span></span>  
 <span data-ttu-id="dd7a3-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd7a3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd7a3-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd7a3-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd7a3-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd7a3-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd7a3-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd7a3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
