---
title: ICorDebugProcess – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dc732a8e3419a7ca42f5180d1bd32128ec33417
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967513"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="306de-102">ICorDebugProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="306de-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="306de-103">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="306de-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="306de-104">Toto rozhraní je podtřídou třídy icordebugcontroller –.</span><span class="sxs-lookup"><span data-stu-id="306de-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="306de-105">Metody</span><span class="sxs-lookup"><span data-stu-id="306de-105">Methods</span></span>  
  
|<span data-ttu-id="306de-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="306de-106">Method</span></span>|<span data-ttu-id="306de-107">Popis</span><span class="sxs-lookup"><span data-stu-id="306de-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="306de-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="306de-109">Vymaže aktuální nespravované výjimky na dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="306de-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="306de-110">EnableLogMessages – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="306de-111">Povolí nebo zakáže zasílání zpráv protokolu v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="306de-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="306de-112">EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="306de-113">Vytvoří výčet všech doménách aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="306de-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="306de-114">EnumerateObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="306de-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="306de-115">Not implemented.</span></span>|  
|[<span data-ttu-id="306de-116">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="306de-117">Získá popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="306de-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="306de-118">GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="306de-119">Získá ID vlákna operačního systému (OS) pro interní pomocné vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="306de-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="306de-120">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="306de-121">Získá ID operačního systému (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="306de-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="306de-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="306de-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="306de-123">Not implemented.</span></span>|  
|[<span data-ttu-id="306de-124">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="306de-125">Získá ID instance icordebugthread –, který má zadaný vlákna operačního systému</span><span class="sxs-lookup"><span data-stu-id="306de-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="306de-126">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="306de-127">Získá kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="306de-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="306de-128">IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="306de-129">Určuje, zda vlákna se pozastavilo, v důsledku ukončení procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="306de-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="306de-130">IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="306de-131">Určuje, zda je adresa uvnitř zástupnou proceduru, která způsobí, že s přechodem na spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="306de-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="306de-132">ModifyLogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="306de-133">Nastaví úroveň závažnosti přepínače zadaný protokol.</span><span class="sxs-lookup"><span data-stu-id="306de-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="306de-134">ReadMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="306de-135">Přečte paměti z procesu.</span><span class="sxs-lookup"><span data-stu-id="306de-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="306de-136">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="306de-137">Nastaví kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="306de-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="306de-138">ThreadForFiberCookie – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="306de-139">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="306de-139">Deprecated.</span></span>|  
|[<span data-ttu-id="306de-140">WriteMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="306de-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="306de-141">Zapíše data do oblasti paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="306de-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="306de-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="306de-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="306de-143">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="306de-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="306de-144">Požadavky</span><span class="sxs-lookup"><span data-stu-id="306de-144">Requirements</span></span>  
 <span data-ttu-id="306de-145">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="306de-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="306de-146">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="306de-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="306de-147">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="306de-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="306de-148">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="306de-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306de-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="306de-149">See also</span></span>
- [<span data-ttu-id="306de-150">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="306de-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="306de-151">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="306de-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
