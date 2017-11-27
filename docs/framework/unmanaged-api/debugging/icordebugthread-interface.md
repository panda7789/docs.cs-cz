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
ms.openlocfilehash: 25b5c8f0720402cce56c69394c6fbe2fb70a6177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread-interface1"></a><span data-ttu-id="5c49c-102">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="5c49c-102">ICorDebugThread Interface1</span></span>
<span data-ttu-id="5c49c-103">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="5c49c-103">Represents a thread in a process.</span></span> <span data-ttu-id="5c49c-104">Životnost `ICorDebugThread` instance je stejný jako životnost vlákno reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="5c49c-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c49c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5c49c-105">Methods</span></span>  
  
|<span data-ttu-id="5c49c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-106">Method</span></span>|<span data-ttu-id="5c49c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5c49c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c49c-108">Clearcurrentexception – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="5c49c-109">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="5c49c-109">This method is not implemented.</span></span> <span data-ttu-id="5c49c-110">Nepoužívejte ho.</span><span class="sxs-lookup"><span data-stu-id="5c49c-110">Do not use it.</span></span>|  
|[<span data-ttu-id="5c49c-111">Createeval – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="5c49c-112">Vytvoří objekt ICorDebugEval, který funguje na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-113">Createstepper – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="5c49c-114">Vytvoří objekt ICorDebugStepper, který umožňuje procházení active rámečku v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-115">Enumeratechains – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="5c49c-116">Získá ukazatele rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-117">Getactivechain – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="5c49c-118">Získá ukazatele rozhraní k active ICorDebugChain na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-119">Getactiveframe – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="5c49c-120">Získá ukazatele rozhraní k active ICorDebugFrame na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-121">Getappdomain – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="5c49c-122">Získá ukazatele rozhraní do domény aplikace, v němž je tato `ICorDebugThread` právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="5c49c-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="5c49c-123">Getcurrentexception – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="5c49c-124">Získá ukazatele rozhraní ICorDebugValue objektu, která představuje výjimku aktuálně hlášeny ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="5c49c-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="5c49c-125">Getdebugstate – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="5c49c-126">Získá hodnotu CorDebugThreadState, která popisuje aktuální stav ladění tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-127">Gethandle – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="5c49c-128">Získá aktuální popisovač pro aktivní součást tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-129">Getid – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="5c49c-130">Získá identifikátor operační systém aktuální aktivní součást tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-131">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="5c49c-132">Získá ukazatele rozhraní pro běžné vlákno language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5c49c-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="5c49c-133">Getprocess – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="5c49c-134">Získá ukazatele rozhraní, které tento proces `ICorDebugThread` součástí.</span><span class="sxs-lookup"><span data-stu-id="5c49c-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="5c49c-135">Getregisterset – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="5c49c-136">Získá ukazatele rozhraní do sady registrace, který je přidružený k tomuto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-137">Getuserstate – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="5c49c-138">Získá bitovou kombinaci hodnot CorDebugUserState, které popisují aktuální stav tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5c49c-139">Setdebugstate – metoda</span><span class="sxs-lookup"><span data-stu-id="5c49c-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="5c49c-140">Nastaví bitovou kombinaci `CorDebugThreadState` hodnoty, které popisují ladění stav tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="5c49c-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c49c-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c49c-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c49c-142">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5c49c-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c49c-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c49c-143">Requirements</span></span>  
 <span data-ttu-id="5c49c-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c49c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c49c-145">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c49c-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c49c-146">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c49c-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c49c-147">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c49c-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c49c-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c49c-148">See Also</span></span>  
 [<span data-ttu-id="5c49c-149">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c49c-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
