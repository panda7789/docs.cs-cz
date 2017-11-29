---
title: ICorDebugStepper Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper
helpviewer_keywords: ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83d394669270eb26b33e084b20a621e18b5b14aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper-interface1"></a><span data-ttu-id="7498a-102">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="7498a-102">ICorDebugStepper Interface1</span></span>
<span data-ttu-id="7498a-103">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="7498a-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7498a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7498a-104">Methods</span></span>  
  
|<span data-ttu-id="7498a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-105">Method</span></span>|<span data-ttu-id="7498a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7498a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7498a-107">Deactivate – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="7498a-108">To způsobí, že `ICorDebugStepper` zrušení poslední krok příkazu přijala.</span><span class="sxs-lookup"><span data-stu-id="7498a-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="7498a-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="7498a-110">Získá hodnotu, která určuje, jestli to `ICorDebugStepper` právě probíhá krok.</span><span class="sxs-lookup"><span data-stu-id="7498a-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="7498a-111">Setinterceptmask – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="7498a-112">Nastaví CorDebugIntercept hodnotu, která určuje typy kód, který se stupeň do.</span><span class="sxs-lookup"><span data-stu-id="7498a-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="7498a-113">Setrangeil – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="7498a-114">Nastaví hodnotu určující, zda volá, aby se [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předat hodnoty argumentu relativně k nativní kód nebo kód (MSIL intermediate language) Microsoft metody, která je se provedl.</span><span class="sxs-lookup"><span data-stu-id="7498a-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="7498a-115">Setunmappedstopmask – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="7498a-116">Nastaví CorDebugUnmappedStop hodnotu, která určuje typ nenamapovaný kódu, ve kterém se zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="7498a-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="7498a-117">Step – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="7498a-118">To způsobí, že `ICorDebugStepper` jedním krokem přes jeho obsahující vláken a volitelně můžete do pokračovat jedním procházení funkce, které se nazývají vlákna.</span><span class="sxs-lookup"><span data-stu-id="7498a-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="7498a-119">StepOut – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="7498a-120">To způsobí, že `ICorDebugStepper` krokování prostřednictvím jeho obsahující vláken a dokončení v případě aktuální rámec vrátí prvek na snímek, volání.</span><span class="sxs-lookup"><span data-stu-id="7498a-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="7498a-121">Steprange – metoda</span><span class="sxs-lookup"><span data-stu-id="7498a-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="7498a-122">To způsobí, že `ICorDebugStepper` jedním krokem přes jeho obsahující vláken a vrátit, když dorazí do kódu nad rámec poslední zadaný rozsah.</span><span class="sxs-lookup"><span data-stu-id="7498a-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7498a-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7498a-123">Remarks</span></span>  
 <span data-ttu-id="7498a-124">`ICorDebugStepper` Rozhraní slouží k těmto účelům:</span><span class="sxs-lookup"><span data-stu-id="7498a-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="7498a-125">Jedná jako identifikátor mezi krok příkaz, který je vydán a tento příkaz dokončit.</span><span class="sxs-lookup"><span data-stu-id="7498a-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="7498a-126">Poskytuje centrální rozhraní pro zapouzdření všechny krokování, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="7498a-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="7498a-127">Poskytuje způsob, jak předčasně zrušit taktování operaci.</span><span class="sxs-lookup"><span data-stu-id="7498a-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="7498a-128">Může existovat více než jeden krokovač na vlákno.</span><span class="sxs-lookup"><span data-stu-id="7498a-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="7498a-129">Například zarážky narazit při krokování přes funkci a uživatel může chtít spustit operaci nového taktování uvnitř této funkce.</span><span class="sxs-lookup"><span data-stu-id="7498a-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="7498a-130">Je ladicího programu určit, jak tuto situaci můžete vyřešit.</span><span class="sxs-lookup"><span data-stu-id="7498a-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="7498a-131">Ladicí program chtít zrušte původní taktování operaci nebo vnořit těchto dvou operací.</span><span class="sxs-lookup"><span data-stu-id="7498a-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="7498a-132">`ICorDebugStepper` Rozhraní podporuje obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="7498a-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="7498a-133">Je-li krokovač může migrovat mezi vlákny, pokud modul CLR (CLR) zavolá cross-threaded, zařazené.</span><span class="sxs-lookup"><span data-stu-id="7498a-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7498a-134">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7498a-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7498a-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7498a-135">Requirements</span></span>  
 <span data-ttu-id="7498a-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7498a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7498a-137">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7498a-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7498a-138">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7498a-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7498a-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7498a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7498a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="7498a-140">See Also</span></span>  
 [<span data-ttu-id="7498a-141">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="7498a-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
