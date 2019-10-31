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
ms.openlocfilehash: 393ac8c119f111b645e7ccdb6ea94efee7207fa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128797"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="da58f-102">ICorDebugProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da58f-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="da58f-103">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="da58f-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="da58f-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="da58f-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da58f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="da58f-105">Methods</span></span>  
  
|<span data-ttu-id="da58f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-106">Method</span></span>|<span data-ttu-id="da58f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="da58f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da58f-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="da58f-109">Vymaže aktuální nespravovanou výjimku na daném vlákně.</span><span class="sxs-lookup"><span data-stu-id="da58f-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="da58f-110">EnableLogMessages – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="da58f-111">Povolí nebo zakáže odesílání zpráv protokolu do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="da58f-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="da58f-112">EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="da58f-113">Vytvoří výčet všech aplikačních domén v procesu.</span><span class="sxs-lookup"><span data-stu-id="da58f-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="da58f-114">EnumerateObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="da58f-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="da58f-115">Not implemented.</span></span>|  
|[<span data-ttu-id="da58f-116">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="da58f-117">Získá popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="da58f-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="da58f-118">GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="da58f-119">Získá ID vlákna operačního systému (OS) pro interní pomocné vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="da58f-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="da58f-120">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="da58f-121">Získá ID operačního systému (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="da58f-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="da58f-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="da58f-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="da58f-123">Not implemented.</span></span>|  
|[<span data-ttu-id="da58f-124">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="da58f-125">Získá instanci ICorDebugThread, která má zadané ID vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="da58f-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="da58f-126">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="da58f-127">Získá kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="da58f-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="da58f-128">IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="da58f-129">Určuje, zda bylo vlákno pozastaveno v důsledku zastavení procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="da58f-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="da58f-130">IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="da58f-131">Určuje, zda je adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="da58f-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="da58f-132">ModifyLogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="da58f-133">Nastaví úroveň závažnosti určeného přepínače protokolu.</span><span class="sxs-lookup"><span data-stu-id="da58f-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="da58f-134">ReadMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="da58f-135">Přečte z procesu paměť.</span><span class="sxs-lookup"><span data-stu-id="da58f-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="da58f-136">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="da58f-137">Nastaví kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="da58f-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="da58f-138">ThreadForFiberCookie – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="da58f-139">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da58f-139">Deprecated.</span></span>|  
|[<span data-ttu-id="da58f-140">WriteMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="da58f-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="da58f-141">Zapisuje data do oblasti paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="da58f-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da58f-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da58f-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da58f-143">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="da58f-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da58f-144">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da58f-144">Requirements</span></span>  
 <span data-ttu-id="da58f-145">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da58f-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da58f-146">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="da58f-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da58f-147">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="da58f-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da58f-148">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da58f-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da58f-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da58f-149">See also</span></span>

- [<span data-ttu-id="da58f-150">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da58f-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="da58f-151">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="da58f-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
