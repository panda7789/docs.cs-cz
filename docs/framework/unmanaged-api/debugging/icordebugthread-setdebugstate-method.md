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
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987139"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="93d77-102">ICorDebugThread::SetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="93d77-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="93d77-103">Sets flags that describe the debugging state of this ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="93d77-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93d77-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93d77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93d77-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="93d77-106">[in] Bitová kombinace hodnot cordebugthreadstate – výčet, které určují stav ladění tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="93d77-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93d77-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93d77-107">Remarks</span></span>  
 <span data-ttu-id="93d77-108">`SetDebugState` Nastaví aktuální stav ladění vlákna.</span><span class="sxs-lookup"><span data-stu-id="93d77-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="93d77-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) Běžné hodnoty je THREAD_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="93d77-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="93d77-110">Pouze ladicí program může ovlivnit stav ladění vlákna.</span><span class="sxs-lookup"><span data-stu-id="93d77-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="93d77-111">Ladění stavy poslední napříč bude pokračovat, pokud chcete zachovat vlákno pokračuje THREAD_SUSPENDed přes více, abyste mohli nastavit jednou a po tomto datu není nutné se starat o něm.</span><span class="sxs-lookup"><span data-stu-id="93d77-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="93d77-112">Pozastavení vlákna a procesu obnovení může způsobit zablokování, když je nepravděpodobné, že by obvykle.</span><span class="sxs-lookup"><span data-stu-id="93d77-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="93d77-113">Toto je vnitřní kvalitu vláken a procesů a podle návrhu.</span><span class="sxs-lookup"><span data-stu-id="93d77-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="93d77-114">Ladicí program můžete asynchronně přerušit a pokračování vláken pro přerušení zablokování.</span><span class="sxs-lookup"><span data-stu-id="93d77-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="93d77-115">Pokud je stav vlákna uživatele USER_UNSAFE_POINT, může zablokovat vlákno uvolňování paměti (GC).</span><span class="sxs-lookup"><span data-stu-id="93d77-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="93d77-116">To znamená, že pozastaveného vlákna má mnohem vyšší pravděpodobnost způsobit zablokování.</span><span class="sxs-lookup"><span data-stu-id="93d77-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="93d77-117">To nemusí ovlivnit ladění, které už ve frontě událostí.</span><span class="sxs-lookup"><span data-stu-id="93d77-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="93d77-118">Proto by měl ladicí program vyprázdnění fronty celá událost (voláním [icordebugcontroller::hasqueuedcallbacks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) před pozastavování a obnovování vláken.</span><span class="sxs-lookup"><span data-stu-id="93d77-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="93d77-119">Jinak se může zobrazit události na vlákně, které se domnívá, že již byla pozastavena.</span><span class="sxs-lookup"><span data-stu-id="93d77-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d77-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93d77-120">Requirements</span></span>  
 <span data-ttu-id="93d77-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93d77-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d77-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93d77-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93d77-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93d77-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93d77-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d77-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
