---
title: ICorDebugThread Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread
helpviewer_keywords: ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2df43a35e510695d7af0c38cbb8fb3b051f5f354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread-interface1"></a><span data-ttu-id="fd423-102">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="fd423-102">ICorDebugThread Interface1</span></span>
<span data-ttu-id="fd423-103">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="fd423-103">Represents a thread in a process.</span></span> <span data-ttu-id="fd423-104">Životnost `ICorDebugThread` instance je stejný jako životnost vlákno reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="fd423-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd423-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fd423-105">Methods</span></span>  
  
|<span data-ttu-id="fd423-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-106">Method</span></span>|<span data-ttu-id="fd423-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fd423-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd423-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="fd423-109">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="fd423-109">This method is not implemented.</span></span> <span data-ttu-id="fd423-110">Nepoužívejte ho.</span><span class="sxs-lookup"><span data-stu-id="fd423-110">Do not use it.</span></span>|  
|[<span data-ttu-id="fd423-111">CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="fd423-112">Vytvoří objekt ICorDebugEval, který funguje na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-113">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="fd423-114">Vytvoří objekt ICorDebugStepper, který umožňuje procházení active rámečku v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-115">EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="fd423-116">Získá ukazatele rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-117">GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="fd423-118">Získá ukazatele rozhraní k active ICorDebugChain na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-119">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="fd423-120">Získá ukazatele rozhraní k active ICorDebugFrame na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-121">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="fd423-122">Získá ukazatele rozhraní do domény aplikace, v němž je tato `ICorDebugThread` právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="fd423-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="fd423-123">GetCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="fd423-124">Získá ukazatele rozhraní ICorDebugValue objektu, která představuje výjimku aktuálně hlášeny ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="fd423-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="fd423-125">GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="fd423-126">Získá hodnotu CorDebugThreadState, která popisuje aktuální stav ladění tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-127">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="fd423-128">Získá aktuální popisovač pro aktivní součást tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-129">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="fd423-130">Získá identifikátor operační systém aktuální aktivní součást tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-131">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="fd423-132">Získá ukazatele rozhraní pro běžné vlákno language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fd423-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="fd423-133">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="fd423-134">Získá ukazatele rozhraní, které tento proces `ICorDebugThread` součástí.</span><span class="sxs-lookup"><span data-stu-id="fd423-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="fd423-135">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="fd423-136">Získá ukazatele rozhraní do sady registrace, který je přidružený k tomuto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-137">GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="fd423-138">Získá bitovou kombinaci hodnot CorDebugUserState, které popisují aktuální stav tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fd423-139">SetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="fd423-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="fd423-140">Nastaví bitovou kombinaci `CorDebugThreadState` hodnoty, které popisují ladění stav tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fd423-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd423-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd423-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd423-142">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="fd423-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd423-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd423-143">Requirements</span></span>  
 <span data-ttu-id="fd423-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd423-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd423-145">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd423-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd423-146">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd423-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd423-147">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd423-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd423-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd423-148">See Also</span></span>  
 [<span data-ttu-id="fd423-149">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fd423-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
