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
ms.openlocfilehash: 27f991c12ea7786d6146b5731848ca5ad3a37e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125373"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="0fb44-102">ICorDebugController – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0fb44-102">ICorDebugController Interface</span></span>

<span data-ttu-id="0fb44-103">Představuje obor, buď <xref:System.Diagnostics.Process>, nebo <xref:System.AppDomain>, ve kterém lze ovládat kontext provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="0fb44-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0fb44-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0fb44-104">Methods</span></span>  
  
|<span data-ttu-id="0fb44-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-105">Method</span></span>|<span data-ttu-id="0fb44-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0fb44-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="0fb44-107">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0fb44-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="0fb44-108">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0fb44-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="0fb44-109">Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="0fb44-110">Obnoví provádění spravovaných vláken po volání metody [ICorDebugController:: stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="0fb44-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="0fb44-111">Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="0fb44-112">Odpojí ladicí program od domény procesu nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="0fb44-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="0fb44-113">EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="0fb44-114">Získá enumerátor pro aktivní spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="0fb44-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="0fb44-115">HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="0fb44-116">Získá hodnotu, která označuje, zda jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="0fb44-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="0fb44-117">IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="0fb44-118">Získá hodnotu, která označuje, zda jsou vlákna v procesu aktuálně spuštěna volně.</span><span class="sxs-lookup"><span data-stu-id="0fb44-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="0fb44-119">SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="0fb44-120">Nastaví stav ladění pro všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="0fb44-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="0fb44-121">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="0fb44-122">Provede kooperativní zastavení na všech vláknech, na kterých běží spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="0fb44-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="0fb44-123">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="0fb44-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="0fb44-124">Ukončí proces se zadaným ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="0fb44-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fb44-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fb44-125">Remarks</span></span>  
 <span data-ttu-id="0fb44-126">Pokud `ICorDebugController` řídí proces, zahrnuje obor všechny podprocesy procesu.</span><span class="sxs-lookup"><span data-stu-id="0fb44-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="0fb44-127">Pokud `ICorDebugController` řídí doménu aplikace, obor obsahuje pouze vlákna této konkrétní aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="0fb44-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fb44-128">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0fb44-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fb44-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0fb44-129">Requirements</span></span>  
 <span data-ttu-id="0fb44-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fb44-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fb44-131">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0fb44-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fb44-132">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0fb44-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fb44-133">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fb44-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb44-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fb44-134">See also</span></span>

- [<span data-ttu-id="0fb44-135">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0fb44-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
