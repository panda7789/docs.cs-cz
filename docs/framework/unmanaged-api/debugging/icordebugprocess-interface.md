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
ms.openlocfilehash: ee526a79d89a9e4e3483daa07a512b6b7f920e70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="1c560-102">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="1c560-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="1c560-103">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1c560-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="1c560-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="1c560-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c560-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1c560-105">Methods</span></span>  
  
|<span data-ttu-id="1c560-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-106">Method</span></span>|<span data-ttu-id="1c560-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1c560-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c560-108">Clearcurrentexception – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="1c560-109">Vymaže aktuální nespravované výjimky na dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="1c560-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="1c560-110">Enablelogmessages – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="1c560-111">Povolí nebo zakáže odesílání zpráv protokolu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1c560-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="1c560-112">Enumerateappdomains – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="1c560-113">Zobrazí všechny domény aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="1c560-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="1c560-114">Enumerateobjects – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="1c560-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="1c560-115">Not implemented.</span></span>|  
|[<span data-ttu-id="1c560-116">Gethandle – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="1c560-117">Získá popisovač pro proces.</span><span class="sxs-lookup"><span data-stu-id="1c560-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="1c560-118">Gethelperthreadid – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="1c560-119">Získá ID vlákna operační systém (OS) pro vlákno interní pomocná ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1c560-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="1c560-120">Getid – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="1c560-121">Získá ID operační systém (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="1c560-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="1c560-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="1c560-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="1c560-123">Not implemented.</span></span>|  
|[<span data-ttu-id="1c560-124">Getthread – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="1c560-125">Získá ID instance ICorDebugThread, který má zadaný vlákno operačního systému</span><span class="sxs-lookup"><span data-stu-id="1c560-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="1c560-126">Getthreadcontext – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="1c560-127">Získá kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="1c560-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1c560-128">Isossuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="1c560-129">Určuje, zda bylo pozastaveno vlákno v důsledku ladicí program ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="1c560-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="1c560-130">Istransitionstub – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="1c560-131">Určuje, zda adresu uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1c560-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="1c560-132">Modifylogswitch – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="1c560-133">Nastaví úroveň závažnosti zadaného protokolu přepínače.</span><span class="sxs-lookup"><span data-stu-id="1c560-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="1c560-134">Readmemory – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="1c560-135">Přečte paměti z procesu.</span><span class="sxs-lookup"><span data-stu-id="1c560-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="1c560-136">Setthreadcontext – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="1c560-137">Nastaví kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="1c560-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1c560-138">Threadforfibercookie – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="1c560-139">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="1c560-139">Deprecated.</span></span>|  
|[<span data-ttu-id="1c560-140">Writememory – metoda</span><span class="sxs-lookup"><span data-stu-id="1c560-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="1c560-141">Zapisuje data do oblast paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="1c560-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c560-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c560-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c560-143">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1c560-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c560-144">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c560-144">Requirements</span></span>  
 <span data-ttu-id="1c560-145">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c560-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c560-146">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c560-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c560-147">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c560-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c560-148">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c560-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c560-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c560-149">See Also</span></span>  
 [<span data-ttu-id="1c560-150">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c560-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="1c560-151">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c560-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
