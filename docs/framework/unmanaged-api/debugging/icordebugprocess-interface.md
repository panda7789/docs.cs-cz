---
title: ICorDebugProcess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6fa95d17e7ff6f857765ea2dd48f61b047a47b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="8c551-102">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="8c551-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="8c551-103">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="8c551-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="8c551-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="8c551-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c551-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8c551-105">Methods</span></span>  
  
|<span data-ttu-id="8c551-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-106">Method</span></span>|<span data-ttu-id="8c551-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8c551-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c551-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="8c551-109">Vymaže aktuální nespravované výjimky na dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="8c551-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="8c551-110">EnableLogMessages – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="8c551-111">Povolí nebo zakáže odesílání zpráv protokolu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="8c551-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="8c551-112">EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="8c551-113">Zobrazí všechny domény aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="8c551-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="8c551-114">EnumerateObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="8c551-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="8c551-115">Not implemented.</span></span>|  
|[<span data-ttu-id="8c551-116">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="8c551-117">Získá popisovač pro proces.</span><span class="sxs-lookup"><span data-stu-id="8c551-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="8c551-118">GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="8c551-119">Získá ID vlákna operační systém (OS) pro vlákno interní pomocná ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="8c551-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="8c551-120">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="8c551-121">Získá ID operační systém (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="8c551-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="8c551-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="8c551-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="8c551-123">Not implemented.</span></span>|  
|[<span data-ttu-id="8c551-124">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="8c551-125">Získá ID instance ICorDebugThread, který má zadaný vlákno operačního systému</span><span class="sxs-lookup"><span data-stu-id="8c551-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="8c551-126">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="8c551-127">Získá kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="8c551-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="8c551-128">IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="8c551-129">Určuje, zda bylo pozastaveno vlákno v důsledku ladicí program ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="8c551-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="8c551-130">IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="8c551-131">Určuje, zda adresu uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="8c551-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="8c551-132">ModifyLogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="8c551-133">Nastaví úroveň závažnosti zadaného protokolu přepínače.</span><span class="sxs-lookup"><span data-stu-id="8c551-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="8c551-134">ReadMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="8c551-135">Přečte paměti z procesu.</span><span class="sxs-lookup"><span data-stu-id="8c551-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="8c551-136">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="8c551-137">Nastaví kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="8c551-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="8c551-138">ThreadForFiberCookie – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="8c551-139">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="8c551-139">Deprecated.</span></span>|  
|[<span data-ttu-id="8c551-140">WriteMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="8c551-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="8c551-141">Zapisuje data do oblast paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="8c551-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c551-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c551-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c551-143">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8c551-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c551-144">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c551-144">Requirements</span></span>  
 <span data-ttu-id="8c551-145">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c551-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c551-146">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c551-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c551-147">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c551-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c551-148">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c551-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c551-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c551-149">See Also</span></span>  
 [<span data-ttu-id="8c551-150">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c551-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="8c551-151">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8c551-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
