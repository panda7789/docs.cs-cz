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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379823"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="e8649-102">ICorDebugThread – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8649-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="e8649-103">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="e8649-103">Represents a thread in a process.</span></span> <span data-ttu-id="e8649-104">Doba života `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.</span><span class="sxs-lookup"><span data-stu-id="e8649-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8649-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e8649-105">Methods</span></span>  
  
|<span data-ttu-id="e8649-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-106">Method</span></span>|<span data-ttu-id="e8649-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e8649-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8649-108">ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-108">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="e8649-109">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="e8649-109">This method is not implemented.</span></span> <span data-ttu-id="e8649-110">Nepoužívejte ho.</span><span class="sxs-lookup"><span data-stu-id="e8649-110">Do not use it.</span></span>|  
|[<span data-ttu-id="e8649-111">CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-111">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="e8649-112">Vytvoří objekt ICorDebugEval, který na tomto počítači pracuje `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-113">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-113">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="e8649-114">Vytvoří objekt ICorDebugStepper, který umožňuje krokování přes aktivní rámec v tomto `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-115">EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-115">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="e8649-116">Získá ukazatel rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-117">GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-117">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="e8649-118">Získá ukazatel rozhraní na aktivní ICorDebugChain `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-119">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-119">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="e8649-120">Získá ukazatel rozhraní na aktivní ICorDebugFrame `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-121">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-121">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="e8649-122">Získá ukazatel rozhraní na doménu aplikace, ve které `ICorDebugThread` je aktuálně prováděna.</span><span class="sxs-lookup"><span data-stu-id="e8649-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="e8649-123">GetCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-123">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="e8649-124">Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje výjimku aktuálně vyvolanou spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="e8649-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="e8649-125">GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-125">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="e8649-126">Získá hodnotu CorDebugThreadState –, která popisuje aktuální stav ladění tohoto `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-127">GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-127">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="e8649-128">Získá aktuální popisovač pro aktivní část tohoto `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-129">GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-129">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="e8649-130">Získá aktuální identifikátor operačního systému aktivní části tohoto `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-131">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-131">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="e8649-132">Načte ukazatel rozhraní do vlákna modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="e8649-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="e8649-133">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-133">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="e8649-134">Získá ukazatel rozhraní na proces, který `ICorDebugThread` tvoří součást.</span><span class="sxs-lookup"><span data-stu-id="e8649-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="e8649-135">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-135">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="e8649-136">Získá ukazatel rozhraní na sadu registrů přidruženou k tomuto `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-137">GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-137">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="e8649-138">Získá bitovou kombinaci hodnot CorDebugUserState –, které popisují aktuální stav `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8649-139">SetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="e8649-139">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="e8649-140">Nastaví bitovou kombinaci `CorDebugThreadState` hodnot, které popisují stav ladění this `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="e8649-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8649-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8649-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8649-142">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e8649-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8649-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8649-143">Requirements</span></span>  
 <span data-ttu-id="e8649-144">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8649-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8649-145">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e8649-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8649-146">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e8649-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8649-147">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8649-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8649-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8649-148">See also</span></span>

- [<span data-ttu-id="e8649-149">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8649-149">Debugging Interfaces</span></span>](debugging-interfaces.md)
