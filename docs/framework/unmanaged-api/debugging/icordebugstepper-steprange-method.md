---
title: ICorDebugStepper::StepRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b18474aeaa79224de5371df3ff0cac5ed9bf4ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994277"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="e06ed-102">ICorDebugStepper::StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="e06ed-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="e06ed-103">Způsobí, že tento icordebugstepper – jedním krokem prostřednictvím jeho nadřazeného vlákna a vrátit se dosáhne kódu za poslední zadaný rozsah.</span><span class="sxs-lookup"><span data-stu-id="e06ed-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e06ed-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e06ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e06ed-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="e06ed-106">[in] Nastavte na `true` krok do funkce, která je volána v rámci vlákna.</span><span class="sxs-lookup"><span data-stu-id="e06ed-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="e06ed-107">Nastavte na `false` krok přes funkci.</span><span class="sxs-lookup"><span data-stu-id="e06ed-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="e06ed-108">[in] Pole struktur cor_debug_step_range –, z nichž každý určuje rozsah.</span><span class="sxs-lookup"><span data-stu-id="e06ed-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="e06ed-109">[in] Velikost `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="e06ed-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06ed-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e06ed-110">Remarks</span></span>  
 <span data-ttu-id="e06ed-111">`StepRange` Metoda se dá použít jako [icordebugstepper::Step –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metody, s tím rozdílem, že nedokončí až do kódu mimo zadaný rozsah je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="e06ed-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="e06ed-112">To může být efektivnější než krokování jedné instrukce v čase.</span><span class="sxs-lookup"><span data-stu-id="e06ed-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="e06ed-113">Rozsahy jsou zadané jako seznam dvojic posunu od začátku krokovač rámce.</span><span class="sxs-lookup"><span data-stu-id="e06ed-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="e06ed-114">Rozsahy jsou relativní vzhledem k kód Microsoft intermediate language (MSIL) metody.</span><span class="sxs-lookup"><span data-stu-id="e06ed-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="e06ed-115">Volání [icordebugstepper::setrangeil –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) s `false` aby rozsahy vzhledem k nativního kódu metody.</span><span class="sxs-lookup"><span data-stu-id="e06ed-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e06ed-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e06ed-116">Requirements</span></span>  
 <span data-ttu-id="e06ed-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e06ed-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e06ed-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e06ed-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e06ed-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e06ed-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e06ed-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e06ed-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
