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
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791710"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="98d97-102">ICorDebugStepper::StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="98d97-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="98d97-103">Způsobí, že se toto ICorDebugStepper do jednoho kroku prostřednictvím jeho obsahujícího vlákna a vrátí se, když dosáhne kódu za poslední z určených rozsahů.</span><span class="sxs-lookup"><span data-stu-id="98d97-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d97-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98d97-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98d97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98d97-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="98d97-106">pro Nastavte na `true` pro krokování do funkce, která je volána v rámci vlákna.</span><span class="sxs-lookup"><span data-stu-id="98d97-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="98d97-107">Nastavte na `false` pro krok nad funkcí.</span><span class="sxs-lookup"><span data-stu-id="98d97-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="98d97-108">pro Pole struktur COR_DEBUG_STEP_RANGE, z nichž každý určuje rozsah.</span><span class="sxs-lookup"><span data-stu-id="98d97-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="98d97-109">pro Velikost pole `ranges`.</span><span class="sxs-lookup"><span data-stu-id="98d97-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98d97-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98d97-110">Remarks</span></span>  
 <span data-ttu-id="98d97-111">Metoda `StepRange` funguje podobně jako metoda [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , s tím rozdílem, že není dokončena, dokud není dosaženo kódu mimo daný rozsah.</span><span class="sxs-lookup"><span data-stu-id="98d97-111">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="98d97-112">To může být efektivnější než v jednom okamžiku krokování jednotlivých instrukcí.</span><span class="sxs-lookup"><span data-stu-id="98d97-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="98d97-113">Rozsahy jsou zadány jako seznam párů posunů od začátku rámce stepper.</span><span class="sxs-lookup"><span data-stu-id="98d97-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="98d97-114">Rozsahy jsou relativní vzhledem k kódu jazyka MSIL (Microsoft Intermediate Language) metody.</span><span class="sxs-lookup"><span data-stu-id="98d97-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="98d97-115">Zavolejte [ICorDebugStepper:: SetRangeIL –](icordebugstepper-setrangeil-method.md) s `false`, aby byly rozsahy relativní vzhledem k nativnímu kódu metody.</span><span class="sxs-lookup"><span data-stu-id="98d97-115">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98d97-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98d97-116">Requirements</span></span>  
 <span data-ttu-id="98d97-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98d97-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d97-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98d97-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98d97-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="98d97-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98d97-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98d97-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
