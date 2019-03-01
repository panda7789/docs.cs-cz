---
title: ICorDebugThread – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f2223230b18f175427bfbfeaa46bf1406d8c7e5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976353"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="50428-102">ICorDebugThread – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50428-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="50428-103">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="50428-103">Represents a thread in a process.</span></span> <span data-ttu-id="50428-104">Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.</span><span class="sxs-lookup"><span data-stu-id="50428-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50428-105">Metody</span><span class="sxs-lookup"><span data-stu-id="50428-105">Methods</span></span>  
  
|<span data-ttu-id="50428-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="50428-106">Method</span></span>|<span data-ttu-id="50428-107">Popis</span><span class="sxs-lookup"><span data-stu-id="50428-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50428-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="50428-109">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="50428-109">This method is not implemented.</span></span> <span data-ttu-id="50428-110">Nepoužívejte ho.</span><span class="sxs-lookup"><span data-stu-id="50428-110">Do not use it.</span></span>|  
|[<span data-ttu-id="50428-111">CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="50428-112">Vytvoří objekt icordebugeval –, který funguje na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-113">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="50428-114">Vytvoří objekt icordebugstepper –, který umožňuje procházení aktivní rámec v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-115">EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="50428-116">Získá ukazatel rozhraní k enumerátoru icordebugchainenum –, který obsahuje všechny řetězů zásobníku v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-117">GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="50428-118">Získá ukazatel rozhraní k aktivní icordebugchain – v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-119">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="50428-120">Získá ukazatel rozhraní k aktivní ICorDebugFrame na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-121">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="50428-122">Získá ukazatel rozhraní aplikační doménu, ve které `ICorDebugThread` právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="50428-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="50428-123">GetCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="50428-124">Získá ukazatel rozhraní na ICorDebugValue objekt, který představuje výjimku vyvolanou aktuálně ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="50428-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="50428-125">GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="50428-126">Získá cordebugthreadstate – hodnota, která popisuje aktuální stav ladění této `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-127">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="50428-128">Získá aktuální popisovač pro aktivní součást této `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-129">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="50428-130">Získá identifikátor aktuálního operačního systému active součástí této `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-131">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="50428-132">Získá ukazatel rozhraní k společným pojítkem language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="50428-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="50428-133">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="50428-134">Získá ukazatel rozhraní k procesu, které bude tato `ICorDebugThread` součástí.</span><span class="sxs-lookup"><span data-stu-id="50428-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="50428-135">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="50428-136">Získá ukazatel rozhraní k sadě register přidružený k tomuto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-137">GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="50428-138">Získá bitová kombinace hodnot cordebuguserstate –, které popisují aktuální stav tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="50428-139">SetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="50428-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="50428-140">Nastaví bitová kombinace hodnot `CorDebugThreadState` hodnot, které popisují ladění stav `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="50428-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50428-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50428-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50428-142">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="50428-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50428-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50428-143">Requirements</span></span>  
 <span data-ttu-id="50428-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50428-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50428-145">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50428-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50428-146">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50428-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50428-147">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50428-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50428-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50428-148">See also</span></span>
- [<span data-ttu-id="50428-149">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="50428-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
