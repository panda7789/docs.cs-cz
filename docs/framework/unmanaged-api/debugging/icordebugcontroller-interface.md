---
title: ICorDebugController – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: e494bbb24e8f2245593e7945625e72e70ae1dde5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892770"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="79a02-102">ICorDebugController – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79a02-102">ICorDebugController Interface</span></span>

<span data-ttu-id="79a02-103">Představuje obor, buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve kterém lze ovládat kontext provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="79a02-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79a02-104">Metody</span><span class="sxs-lookup"><span data-stu-id="79a02-104">Methods</span></span>  
  
|<span data-ttu-id="79a02-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-105">Method</span></span>|<span data-ttu-id="79a02-106">Popis</span><span class="sxs-lookup"><span data-stu-id="79a02-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="79a02-107">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="79a02-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="79a02-108">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="79a02-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="79a02-109">Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-109">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="79a02-110">Obnoví provádění spravovaných vláken po volání metody [ICorDebugController:: stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="79a02-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="79a02-111">Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-111">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="79a02-112">Odpojí ladicí program od domény procesu nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="79a02-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="79a02-113">EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-113">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="79a02-114">Získá enumerátor pro aktivní spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="79a02-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="79a02-115">HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-115">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="79a02-116">Získá hodnotu, která označuje, zda jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="79a02-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="79a02-117">IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-117">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="79a02-118">Získá hodnotu, která označuje, zda jsou vlákna v procesu aktuálně spuštěna volně.</span><span class="sxs-lookup"><span data-stu-id="79a02-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="79a02-119">SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-119">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="79a02-120">Nastaví stav ladění pro všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="79a02-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="79a02-121">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-121">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="79a02-122">Provede kooperativní zastavení na všech vláknech, na kterých běží spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="79a02-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="79a02-123">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="79a02-123">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="79a02-124">Ukončí proces se zadaným ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="79a02-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79a02-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79a02-125">Remarks</span></span>  
 <span data-ttu-id="79a02-126">Pokud `ICorDebugController` řízení procesu řídí, obor zahrnuje všechna vlákna procesu.</span><span class="sxs-lookup"><span data-stu-id="79a02-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="79a02-127">Pokud `ICorDebugController` aplikace řídí doménu aplikace, zahrnuje obor pouze vlákna této konkrétní aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="79a02-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79a02-128">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="79a02-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79a02-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79a02-129">Requirements</span></span>  
 <span data-ttu-id="79a02-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79a02-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a02-131">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79a02-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79a02-132">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="79a02-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79a02-133">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a02-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a02-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="79a02-134">See also</span></span>

- [<span data-ttu-id="79a02-135">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79a02-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
