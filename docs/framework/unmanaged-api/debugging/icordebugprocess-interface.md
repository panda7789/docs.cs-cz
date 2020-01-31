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
ms.openlocfilehash: b2429052173a187297b67c756213e5d27a79298b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792595"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="975a5-102">ICorDebugProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="975a5-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="975a5-103">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="975a5-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="975a5-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="975a5-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="975a5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="975a5-105">Methods</span></span>  
  
|<span data-ttu-id="975a5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-106">Method</span></span>|<span data-ttu-id="975a5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="975a5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="975a5-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-108">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="975a5-109">Vymaže aktuální nespravovanou výjimku na daném vlákně.</span><span class="sxs-lookup"><span data-stu-id="975a5-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="975a5-110">EnableLogMessages – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-110">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="975a5-111">Povolí nebo zakáže odesílání zpráv protokolu do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="975a5-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="975a5-112">EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-112">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="975a5-113">Vytvoří výčet všech aplikačních domén v procesu.</span><span class="sxs-lookup"><span data-stu-id="975a5-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="975a5-114">EnumerateObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-114">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="975a5-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="975a5-115">Not implemented.</span></span>|  
|[<span data-ttu-id="975a5-116">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-116">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="975a5-117">Získá popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="975a5-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="975a5-118">GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-118">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="975a5-119">Získá ID vlákna operačního systému (OS) pro interní pomocné vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="975a5-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="975a5-120">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-120">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="975a5-121">Získá ID operačního systému (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="975a5-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="975a5-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-122">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="975a5-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="975a5-123">Not implemented.</span></span>|  
|[<span data-ttu-id="975a5-124">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-124">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="975a5-125">Získá instanci ICorDebugThread, která má zadané ID vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="975a5-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="975a5-126">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-126">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="975a5-127">Získá kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="975a5-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="975a5-128">IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-128">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="975a5-129">Určuje, zda bylo vlákno pozastaveno v důsledku zastavení procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="975a5-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="975a5-130">IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-130">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="975a5-131">Určuje, zda je adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="975a5-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="975a5-132">ModifyLogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-132">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="975a5-133">Nastaví úroveň závažnosti určeného přepínače protokolu.</span><span class="sxs-lookup"><span data-stu-id="975a5-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="975a5-134">ReadMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-134">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="975a5-135">Přečte z procesu paměť.</span><span class="sxs-lookup"><span data-stu-id="975a5-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="975a5-136">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-136">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="975a5-137">Nastaví kontext pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="975a5-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="975a5-138">ThreadForFiberCookie – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-138">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="975a5-139">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="975a5-139">Deprecated.</span></span>|  
|[<span data-ttu-id="975a5-140">WriteMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="975a5-140">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="975a5-141">Zapisuje data do oblasti paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="975a5-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="975a5-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="975a5-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="975a5-143">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="975a5-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975a5-144">Požadavky</span><span class="sxs-lookup"><span data-stu-id="975a5-144">Requirements</span></span>  
 <span data-ttu-id="975a5-145">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="975a5-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="975a5-146">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="975a5-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="975a5-147">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="975a5-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="975a5-148">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="975a5-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975a5-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="975a5-149">See also</span></span>

- [<span data-ttu-id="975a5-150">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="975a5-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="975a5-151">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="975a5-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
