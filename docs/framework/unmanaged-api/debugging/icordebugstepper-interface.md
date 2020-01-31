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
ms.openlocfilehash: e9bb69567a247472af42efb08b609d3474c87ed2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791795"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="f1c5e-102">ICorDebugStepper – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1c5e-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="f1c5e-103">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1c5e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f1c5e-104">Methods</span></span>  
  
|<span data-ttu-id="f1c5e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-105">Method</span></span>|<span data-ttu-id="f1c5e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f1c5e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1c5e-107">Deactivate – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-107">Deactivate Method</span></span>](icordebugstepper-deactivate-method.md)|<span data-ttu-id="f1c5e-108">Způsobí, že toto `ICorDebugStepper` zruší přijatý příkaz posledního kroku.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="f1c5e-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-109">IsActive Method</span></span>](icordebugstepper-isactive-method.md)|<span data-ttu-id="f1c5e-110">Získá hodnotu, která označuje, zda tento `ICorDebugStepper` aktuálně provádí krok.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="f1c5e-111">SetInterceptMask – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-111">SetInterceptMask Method</span></span>](icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="f1c5e-112">Nastaví hodnotu CorDebugIntercept –, která určuje typy kódu, na které se používá.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="f1c5e-113">SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-113">SetRangeIL Method</span></span>](icordebugstepper-setrangeil-method.md)|<span data-ttu-id="f1c5e-114">Nastaví hodnotu, která označuje, zda volání [ICorDebugStepper:: StepRange –](icordebugstepper-steprange-method.md) předávají hodnoty argumentu relativně k nativnímu kódu nebo kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="f1c5e-115">SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-115">SetUnmappedStopMask Method</span></span>](icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="f1c5e-116">Nastaví hodnotu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="f1c5e-117">Step – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-117">Step Method</span></span>](icordebugstepper-step-method.md)|<span data-ttu-id="f1c5e-118">Způsobí, že se toto `ICorDebugStepper` k jednomu kroku prostřednictvím jeho obsahujícího vlákna, a volitelně, aby bylo možné pokračovat v jednoduchém krokování prostřednictvím funkcí, které jsou volány ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="f1c5e-119">StepOut – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-119">StepOut Method</span></span>](icordebugstepper-stepout-method.md)|<span data-ttu-id="f1c5e-120">Způsobí, že se tato `ICorDebugStepper` k jednomu kroku prostřednictvím jeho obsahujícího vlákna a k dokončení, když aktuální rámec vrátí řízení volajícímu snímku.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="f1c5e-121">StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="f1c5e-121">StepRange Method</span></span>](icordebugstepper-steprange-method.md)|<span data-ttu-id="f1c5e-122">Způsobí, že se tato `ICorDebugStepper` k jednomu kroku prostřednictvím jeho obsahujícího vlákna a vrátí se, pokud dosáhne kódu za poslední z určených rozsahů.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1c5e-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1c5e-123">Remarks</span></span>  
 <span data-ttu-id="f1c5e-124">Rozhraní `ICorDebugStepper` slouží k následujícím účelům:</span><span class="sxs-lookup"><span data-stu-id="f1c5e-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="f1c5e-125">Funguje jako identifikátor mezi příkazem kroku, který je vydán a dokončením tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="f1c5e-126">Poskytuje centrální rozhraní pro zapouzdření veškerého krokování, které je možné provést.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="f1c5e-127">Poskytuje způsob, jak předčasně zrušit operaci krokování.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="f1c5e-128">Na vlákno může být více než jeden stepper.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="f1c5e-129">Například zarážka může být dosaženo při krokování nad funkcí a uživatel může chtít spustit novou operaci krokování uvnitř této funkce.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="f1c5e-130">Aby bylo možné určit, jak se má tato situace zvládnout, je k ladicí program.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="f1c5e-131">Ladicí program může chtít zrušit původní operaci krokování nebo vnořit tyto dvě operace.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="f1c5e-132">Rozhraní `ICorDebugStepper` podporuje obě volby.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="f1c5e-133">Stepper se může migrovat mezi vlákny, pokud modul CLR (Common Language Runtime) provede více vláken, zařaditelné volání.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1c5e-134">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f1c5e-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1c5e-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1c5e-135">Requirements</span></span>  
 <span data-ttu-id="f1c5e-136">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1c5e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1c5e-137">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f1c5e-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1c5e-138">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f1c5e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1c5e-139">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1c5e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c5e-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1c5e-140">See also</span></span>

- [<span data-ttu-id="f1c5e-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f1c5e-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
