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
ms.openlocfilehash: 230488201b637c5a53f41dd4c3f204b37e8984fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411467"
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="1f38d-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="1f38d-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="1f38d-103">Představuje obor, buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu se dá řídit kontextu.</span><span class="sxs-lookup"><span data-stu-id="1f38d-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f38d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1f38d-104">Methods</span></span>  
  
|<span data-ttu-id="1f38d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-105">Method</span></span>|<span data-ttu-id="1f38d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1f38d-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="1f38d-107">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1f38d-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="1f38d-108">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1f38d-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="1f38d-109">Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="1f38d-110">Pokračuje v provádění spravovaných vláknech po volání [icordebugcontroller::stop –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="1f38d-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="1f38d-111">Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="1f38d-112">Umožňuje odpojit ladicí program z domény procesů nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f38d-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="1f38d-113">EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="1f38d-114">Získá enumerátor pro aktivní spravovaných vláken v procesu.</span><span class="sxs-lookup"><span data-stu-id="1f38d-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="1f38d-115">HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="1f38d-116">Získá hodnotu, která určuje, zda všechny spravované zpětná volání jsou aktuálně ve frontě pro zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="1f38d-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="1f38d-117">IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="1f38d-118">Získá hodnotu, která určuje, zda vláken v procesu jsou aktuálně spuštěny volně.</span><span class="sxs-lookup"><span data-stu-id="1f38d-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="1f38d-119">SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="1f38d-120">Nastaví ladění stav všech spravovaných vláken v procesu.</span><span class="sxs-lookup"><span data-stu-id="1f38d-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="1f38d-121">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="1f38d-122">Provede spolupráci zastavení všech vláken, které jsou spuštěny spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="1f38d-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="1f38d-123">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="1f38d-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="1f38d-124">Ukončí proces uvedený ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="1f38d-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f38d-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f38d-125">Remarks</span></span>  
 <span data-ttu-id="1f38d-126">Pokud `ICorDebugController` je proces řízení, oboru zahrnuje všechny podprocesy procesu.</span><span class="sxs-lookup"><span data-stu-id="1f38d-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="1f38d-127">Pokud `ICorDebugController` je řízení doménu aplikace, rozsah obsahuje pouze vláken této domény konkrétní aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f38d-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f38d-128">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1f38d-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f38d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f38d-129">Requirements</span></span>  
 <span data-ttu-id="1f38d-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f38d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f38d-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f38d-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f38d-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f38d-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f38d-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f38d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f38d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f38d-134">See Also</span></span>  
 [<span data-ttu-id="1f38d-135">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1f38d-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
