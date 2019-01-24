---
title: ICorDebugController Interface1
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
ms.openlocfilehash: c0651f8cd63f2ebdc6b81e92c0b55d94fe51316b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645298"
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="3b2ea-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="3b2ea-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="3b2ea-103">Představuje rozsah buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu lze ovládat kontext.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b2ea-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3b2ea-104">Methods</span></span>  
  
|<span data-ttu-id="3b2ea-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-105">Method</span></span>|<span data-ttu-id="3b2ea-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3b2ea-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="3b2ea-107">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="3b2ea-108">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="3b2ea-109">Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="3b2ea-110">Pokračuje v provádění spravovaná vlákna po volání [icordebugcontroller::stop –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="3b2ea-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="3b2ea-111">Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="3b2ea-112">Odpojí ladicí program z domény, procesu nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="3b2ea-113">EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="3b2ea-114">Získá enumerátor pro aktivní spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="3b2ea-115">HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="3b2ea-116">Získá hodnotu určující, zda všechny spravované zpětná volání jsou právě ve frontě pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="3b2ea-117">IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="3b2ea-118">Získá hodnotu, která označuje, zda vlákna v procesu jsou aktuálně spuštěna bez omezení.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="3b2ea-119">SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="3b2ea-120">Nastaví stav ladění všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="3b2ea-121">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="3b2ea-122">Provádí kooperativní stop na všech vláknech, na kterých běží spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="3b2ea-123">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2ea-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="3b2ea-124">Ukončí proces s uvedený ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b2ea-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b2ea-125">Remarks</span></span>  
 <span data-ttu-id="3b2ea-126">Pokud `ICorDebugController` je proces řízení, oborem, který zahrnuje všechna vlákna procesu.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="3b2ea-127">Pokud `ICorDebugController` je řízení doménu aplikace, oborem, který zahrnuje pouze vlákna této konkrétní aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b2ea-128">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="3b2ea-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b2ea-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b2ea-129">Requirements</span></span>  
 <span data-ttu-id="3b2ea-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b2ea-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b2ea-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b2ea-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b2ea-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b2ea-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b2ea-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b2ea-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b2ea-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b2ea-134">See also</span></span>
- [<span data-ttu-id="3b2ea-135">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3b2ea-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
