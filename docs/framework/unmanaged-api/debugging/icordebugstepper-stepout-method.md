---
title: ICorDebugStepper::StepOut – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 6c1d7db8aacaf81d47abd4a9cd972b44f56a3bb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137512"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="5f0cc-102">ICorDebugStepper::StepOut – metoda</span><span class="sxs-lookup"><span data-stu-id="5f0cc-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="5f0cc-103">Způsobí, že se toto ICorDebugStepper do jediného kroku prostřednictvím jeho obsahujícího vlákna a bude dokončeno, když aktuální rámec vrátí řízení volajícímu snímku.</span><span class="sxs-lookup"><span data-stu-id="5f0cc-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f0cc-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5f0cc-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f0cc-105">Remarks</span></span>  
 <span data-ttu-id="5f0cc-106">Operace `StepOut` se dokončí po běžném návratu z aktuálního rámce do volajícího rámce.</span><span class="sxs-lookup"><span data-stu-id="5f0cc-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="5f0cc-107">Pokud je zavolána `StepOut` v nespravovaném kódu, krok bude dokončen, když se aktuální rámec vrátí do spravovaného kódu, který jej volal.</span><span class="sxs-lookup"><span data-stu-id="5f0cc-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="5f0cc-108">V .NET Framework verze 2,0 nepoužívejte `StepOut` s nastaveným příznakem STOP_UNMANAGED, protože selže.</span><span class="sxs-lookup"><span data-stu-id="5f0cc-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="5f0cc-109">(K nastavení příznaků pro krokování použijte [ICorDebugStepper:: SetUnmappedStopMask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) .) Ladicí program spolupráce musí Krokovat s nativním samotným kódem.</span><span class="sxs-lookup"><span data-stu-id="5f0cc-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f0cc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f0cc-110">Requirements</span></span>  
 <span data-ttu-id="5f0cc-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f0cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f0cc-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5f0cc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f0cc-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5f0cc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f0cc-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f0cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
