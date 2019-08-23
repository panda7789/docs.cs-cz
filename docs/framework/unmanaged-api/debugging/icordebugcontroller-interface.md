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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2a083f46f24d6f3f24c63dd2415b85f975cfa29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912853"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="dceff-102">ICorDebugController – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dceff-102">ICorDebugController Interface</span></span>

<span data-ttu-id="dceff-103">Představuje obor, buď <xref:System.Diagnostics.Process> <xref:System.AppDomain>nebo, ve kterém lze ovládat kontext provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="dceff-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dceff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dceff-104">Methods</span></span>  
  
|<span data-ttu-id="dceff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-105">Method</span></span>|<span data-ttu-id="dceff-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dceff-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="dceff-107">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="dceff-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="dceff-108">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="dceff-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="dceff-109">Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="dceff-110">Obnoví provádění spravovaných vláken po volání metody [ICorDebugController:: stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="dceff-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="dceff-111">Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="dceff-112">Odpojí ladicí program od domény procesu nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceff-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="dceff-113">EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="dceff-114">Získá enumerátor pro aktivní spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="dceff-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="dceff-115">HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="dceff-116">Získá hodnotu, která označuje, zda jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="dceff-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="dceff-117">IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="dceff-118">Získá hodnotu, která označuje, zda jsou vlákna v procesu aktuálně spuštěna volně.</span><span class="sxs-lookup"><span data-stu-id="dceff-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="dceff-119">SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="dceff-120">Nastaví stav ladění pro všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="dceff-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="dceff-121">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="dceff-122">Provede kooperativní zastavení na všech vláknech, na kterých běží spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="dceff-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="dceff-123">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="dceff-124">Ukončí proces se zadaným ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="dceff-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dceff-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dceff-125">Remarks</span></span>  
 <span data-ttu-id="dceff-126">Pokud `ICorDebugController` řízení procesu řídí, obor zahrnuje všechna vlákna procesu.</span><span class="sxs-lookup"><span data-stu-id="dceff-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="dceff-127">Pokud `ICorDebugController` aplikace řídí doménu aplikace, zahrnuje obor pouze vlákna této konkrétní aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="dceff-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dceff-128">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="dceff-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dceff-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dceff-129">Requirements</span></span>  
 <span data-ttu-id="dceff-130">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dceff-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dceff-131">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dceff-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dceff-132">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dceff-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dceff-133">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dceff-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dceff-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dceff-134">See also</span></span>

- [<span data-ttu-id="dceff-135">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dceff-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
