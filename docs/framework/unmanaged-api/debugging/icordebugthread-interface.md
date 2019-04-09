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
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184701"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="7e431-102">ICorDebugThread – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e431-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="7e431-103">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="7e431-103">Represents a thread in a process.</span></span> <span data-ttu-id="7e431-104">Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.</span><span class="sxs-lookup"><span data-stu-id="7e431-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e431-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7e431-105">Methods</span></span>  
  
|<span data-ttu-id="7e431-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-106">Method</span></span>|<span data-ttu-id="7e431-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7e431-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e431-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="7e431-109">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="7e431-109">This method is not implemented.</span></span> <span data-ttu-id="7e431-110">Nepoužívejte ho.</span><span class="sxs-lookup"><span data-stu-id="7e431-110">Do not use it.</span></span>|  
|[<span data-ttu-id="7e431-111">CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="7e431-112">Vytvoří objekt icordebugeval –, který funguje na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-113">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="7e431-114">Vytvoří objekt icordebugstepper –, který umožňuje procházení aktivní rámec v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-115">EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="7e431-116">Získá ukazatel rozhraní k enumerátoru icordebugchainenum –, který obsahuje všechny řetězů zásobníku v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-117">GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="7e431-118">Získá ukazatel rozhraní k aktivní icordebugchain – v tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-119">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="7e431-120">Získá ukazatel rozhraní k aktivní ICorDebugFrame na tomto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-121">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="7e431-122">Získá ukazatel rozhraní aplikační doménu, ve které `ICorDebugThread` právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="7e431-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="7e431-123">GetCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="7e431-124">Získá ukazatel rozhraní na ICorDebugValue objekt, který představuje výjimku vyvolanou aktuálně ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="7e431-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="7e431-125">GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="7e431-126">Získá cordebugthreadstate – hodnota, která popisuje aktuální stav ladění této `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-127">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="7e431-128">Získá aktuální popisovač pro aktivní součást této `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-129">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="7e431-130">Získá identifikátor aktuálního operačního systému active součástí této `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-131">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="7e431-132">Získá ukazatel rozhraní k společným pojítkem language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7e431-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="7e431-133">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="7e431-134">Získá ukazatel rozhraní k procesu, které bude tato `ICorDebugThread` součástí.</span><span class="sxs-lookup"><span data-stu-id="7e431-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="7e431-135">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="7e431-136">Získá ukazatel rozhraní k sadě register přidružený k tomuto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-137">GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="7e431-138">Získá bitová kombinace hodnot cordebuguserstate –, které popisují aktuální stav tohoto `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="7e431-139">SetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="7e431-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="7e431-140">Nastaví bitová kombinace hodnot `CorDebugThreadState` hodnot, které popisují ladění stav `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7e431-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e431-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e431-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e431-142">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="7e431-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e431-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e431-143">Requirements</span></span>  
 <span data-ttu-id="7e431-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e431-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e431-145">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e431-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e431-146">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e431-146">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7e431-147">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7e431-147">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e431-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e431-148">See also</span></span>

- [<span data-ttu-id="7e431-149">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e431-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
