---
title: ICorDebugStepper – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f83b9796bb692ce234a03c596387960bd879ebf3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212515"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="d38fc-102">ICorDebugStepper – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d38fc-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="d38fc-103">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="d38fc-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d38fc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d38fc-104">Methods</span></span>  
  
|<span data-ttu-id="d38fc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-105">Method</span></span>|<span data-ttu-id="d38fc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d38fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d38fc-107">Deactivate – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="d38fc-108">To způsobí, že `ICorDebugStepper` zrušení poslední krok příkazu získala.</span><span class="sxs-lookup"><span data-stu-id="d38fc-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="d38fc-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="d38fc-110">Získá hodnotu, která určuje, jestli to `ICorDebugStepper` právě probíhá krok.</span><span class="sxs-lookup"><span data-stu-id="d38fc-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="d38fc-111">SetInterceptMask – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="d38fc-112">Cordebugintercept – hodnota, která určuje typy kódu, které jsou vkročili nastaví.</span><span class="sxs-lookup"><span data-stu-id="d38fc-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="d38fc-113">SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="d38fc-114">Nastaví hodnotu určující, zda volání [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předání hodnoty argumentu vzhledem k nativní kód nebo kód Microsoft intermediate language (MSIL) metody, která je právě prošli.</span><span class="sxs-lookup"><span data-stu-id="d38fc-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="d38fc-115">SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="d38fc-116">Nastaví hodnotu cordebugunmappedstop –, který určuje typ nenamapované kódu, ve kterém se zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="d38fc-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="d38fc-117">Step – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="d38fc-118">To způsobí, že `ICorDebugStepper` jedním krokem prostřednictvím jeho nadřazeného vlákna a volitelně do pokračujte v jedné krokování funkcí, které jsou volány vlákna.</span><span class="sxs-lookup"><span data-stu-id="d38fc-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="d38fc-119">StepOut – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="d38fc-120">To způsobí, že `ICorDebugStepper` krokování jeho nadřazeného vlákna a v případě kompletní aktuální rámec vrátí řízení volající rámec.</span><span class="sxs-lookup"><span data-stu-id="d38fc-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="d38fc-121">StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="d38fc-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="d38fc-122">To způsobí, že `ICorDebugStepper` jedním krokem prostřednictvím jeho nadřazeného vlákna a vrátit se při dosažení kód za poslední zadaný rozsah.</span><span class="sxs-lookup"><span data-stu-id="d38fc-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d38fc-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d38fc-123">Remarks</span></span>  
 <span data-ttu-id="d38fc-124">`ICorDebugStepper` Rozhraní slouží k těmto účelům:</span><span class="sxs-lookup"><span data-stu-id="d38fc-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="d38fc-125">Funguje jako identifikátor mezi kroku příkaz, který je vydaný a dokončení tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="d38fc-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="d38fc-126">Poskytuje centrální rozhraní k zapouzdření všech krokování, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="d38fc-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="d38fc-127">Poskytuje způsob, jak předčasně krokování operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="d38fc-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="d38fc-128">Může existovat více než jeden krokovač na vlákno.</span><span class="sxs-lookup"><span data-stu-id="d38fc-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="d38fc-129">Například zarážky narazit při krokování přes funkci a uživatel chtít spustit nový krokování operaci uvnitř této funkce.</span><span class="sxs-lookup"><span data-stu-id="d38fc-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="d38fc-130">Záleží ladicí program určit, jak tuto situaci.</span><span class="sxs-lookup"><span data-stu-id="d38fc-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="d38fc-131">Ladicí program může chtít zrušit původní krokování nebo vnořené dvě operace.</span><span class="sxs-lookup"><span data-stu-id="d38fc-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="d38fc-132">`ICorDebugStepper` Rozhraní podporuje obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="d38fc-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="d38fc-133">Pokud modul CLR (CLR) provede volání více vláken, zařazené krokovač migrovat mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="d38fc-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d38fc-134">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="d38fc-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d38fc-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d38fc-135">Requirements</span></span>  
 <span data-ttu-id="d38fc-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d38fc-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d38fc-137">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d38fc-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d38fc-138">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d38fc-138">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d38fc-139">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d38fc-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d38fc-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d38fc-140">See also</span></span>

- [<span data-ttu-id="d38fc-141">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d38fc-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
