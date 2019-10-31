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
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="bb04c-102">ICorDebugThread::SetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="bb04c-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="bb04c-103">Nastaví příznaky, které popisují stav ladění tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="bb04c-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb04c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb04c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb04c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb04c-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="bb04c-106">pro Bitová kombinace hodnot výčtu CorDebugThreadState –, která určuje stav ladění tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="bb04c-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb04c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb04c-107">Remarks</span></span>  
 <span data-ttu-id="bb04c-108">`SetDebugState` nastaví aktuální stav ladění vlákna.</span><span class="sxs-lookup"><span data-stu-id="bb04c-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="bb04c-109">(Stav "aktuální ladění" představuje stav ladění, pokud proces pokračoval v pokračování, nikoli aktuálním aktuálním stavem.) Normální hodnota tohoto pole je THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="bb04c-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="bb04c-110">Pouze ladicí program může ovlivnit stav ladění vlákna.</span><span class="sxs-lookup"><span data-stu-id="bb04c-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="bb04c-111">Stavy ladění trvají v průběhu několika instancí, takže pokud chcete, aby se THREAD_SUSPENDed vlákno více pokračovalo, můžete ho nastavit jednou a pak se na něj nemusíte starat.</span><span class="sxs-lookup"><span data-stu-id="bb04c-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="bb04c-112">Pozastavení vláken a obnovení procesu může způsobit zablokování, i když je obvykle nepravděpodobné.</span><span class="sxs-lookup"><span data-stu-id="bb04c-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="bb04c-113">Toto je vnitřní kvalita vláken a procesů a je záměrné.</span><span class="sxs-lookup"><span data-stu-id="bb04c-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="bb04c-114">Ladicí program může asynchronně poškodit a obnovit vlákna pro přerušení zablokování.</span><span class="sxs-lookup"><span data-stu-id="bb04c-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="bb04c-115">Pokud stav uživatele vlákna zahrnuje USER_UNSAFE_POINT, vlákno může zablokovat uvolňování paměti (GC).</span><span class="sxs-lookup"><span data-stu-id="bb04c-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="bb04c-116">To znamená, že pozastavené vlákno má mnohem větší šanci na způsob zablokování.</span><span class="sxs-lookup"><span data-stu-id="bb04c-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="bb04c-117">To nemusí mít vliv na události ladění, které jsou už ve frontě.</span><span class="sxs-lookup"><span data-stu-id="bb04c-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="bb04c-118">Proto by měl ladicí program Vyprázdnit celou frontu událostí (voláním [ICorDebugController:: HasQueuedCallbacks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) před přerušením nebo pokračováním v vláknech.</span><span class="sxs-lookup"><span data-stu-id="bb04c-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="bb04c-119">V opačném případě může obdržet události pro vlákno, u kterého se domnívá, že již byla pozastavena.</span><span class="sxs-lookup"><span data-stu-id="bb04c-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb04c-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb04c-120">Requirements</span></span>  
 <span data-ttu-id="bb04c-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb04c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb04c-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bb04c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb04c-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bb04c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb04c-124">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb04c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
