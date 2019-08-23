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
ms.openlocfilehash: c57b13b05522614ff066b93cb9f6a437cb340576
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962690"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="61a00-102">ICorDebugStepper – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61a00-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="61a00-103">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="61a00-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61a00-104">Metody</span><span class="sxs-lookup"><span data-stu-id="61a00-104">Methods</span></span>  
  
|<span data-ttu-id="61a00-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-105">Method</span></span>|<span data-ttu-id="61a00-106">Popis</span><span class="sxs-lookup"><span data-stu-id="61a00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61a00-107">Deactivate – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="61a00-108">Způsobí zrušení příkazu posledního kroku, kterýpřijal.`ICorDebugStepper`</span><span class="sxs-lookup"><span data-stu-id="61a00-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="61a00-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="61a00-110">Načte hodnotu, která označuje, zda `ICorDebugStepper` se aktuálně provádí krok.</span><span class="sxs-lookup"><span data-stu-id="61a00-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="61a00-111">SetInterceptMask – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="61a00-112">Nastaví hodnotu CorDebugIntercept –, která určuje typy kódu, na které se používá.</span><span class="sxs-lookup"><span data-stu-id="61a00-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="61a00-113">SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="61a00-114">Nastaví hodnotu, která označuje, zda volání [ICorDebugStepper:: StepRange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předávají hodnoty argumentu relativně k nativnímu kódu nebo kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="61a00-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="61a00-115">SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="61a00-116">Nastaví hodnotu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.</span><span class="sxs-lookup"><span data-stu-id="61a00-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="61a00-117">Step – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="61a00-118">Způsobí, `ICorDebugStepper` že se jedná o krok do jednoho kroku prostřednictvím jeho nadřazeného vlákna a volitelně pro pokračování v jednoduchém provádění prostřednictvím funkcí, které jsou volány v rámci vlákna.</span><span class="sxs-lookup"><span data-stu-id="61a00-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="61a00-119">StepOut – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="61a00-120">Způsobí, `ICorDebugStepper` že se jedná o krok do jednoho kroku prostřednictvím obsahujícího vlákna a k dokončení, když aktuální rámec vrátí řízení volajícímu snímku.</span><span class="sxs-lookup"><span data-stu-id="61a00-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="61a00-121">StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="61a00-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="61a00-122">Způsobí, `ICorDebugStepper` že se jedná o krok do jednoho kroku prostřednictvím obsahujícího vlákna a vrátí se, když dosáhne kódu nad poslední z určených rozsahů.</span><span class="sxs-lookup"><span data-stu-id="61a00-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61a00-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61a00-123">Remarks</span></span>  
 <span data-ttu-id="61a00-124">`ICorDebugStepper` Rozhraní slouží k následujícím účelům:</span><span class="sxs-lookup"><span data-stu-id="61a00-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="61a00-125">Funguje jako identifikátor mezi příkazem kroku, který je vydán a dokončením tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="61a00-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="61a00-126">Poskytuje centrální rozhraní pro zapouzdření veškerého krokování, které je možné provést.</span><span class="sxs-lookup"><span data-stu-id="61a00-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="61a00-127">Poskytuje způsob, jak předčasně zrušit operaci krokování.</span><span class="sxs-lookup"><span data-stu-id="61a00-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="61a00-128">Na vlákno může být více než jeden stepper.</span><span class="sxs-lookup"><span data-stu-id="61a00-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="61a00-129">Například zarážka může být dosaženo při krokování nad funkcí a uživatel může chtít spustit novou operaci krokování uvnitř této funkce.</span><span class="sxs-lookup"><span data-stu-id="61a00-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="61a00-130">Aby bylo možné určit, jak se má tato situace zvládnout, je k ladicí program.</span><span class="sxs-lookup"><span data-stu-id="61a00-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="61a00-131">Ladicí program může chtít zrušit původní operaci krokování nebo vnořit tyto dvě operace.</span><span class="sxs-lookup"><span data-stu-id="61a00-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="61a00-132">`ICorDebugStepper` Rozhraní podporuje obě volby.</span><span class="sxs-lookup"><span data-stu-id="61a00-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="61a00-133">Stepper se může migrovat mezi vlákny, pokud modul CLR (Common Language Runtime) provede více vláken, zařaditelné volání.</span><span class="sxs-lookup"><span data-stu-id="61a00-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61a00-134">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="61a00-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a00-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61a00-135">Requirements</span></span>  
 <span data-ttu-id="61a00-136">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a00-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a00-137">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="61a00-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61a00-138">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61a00-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61a00-139">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a00-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a00-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61a00-140">See also</span></span>

- [<span data-ttu-id="61a00-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="61a00-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
