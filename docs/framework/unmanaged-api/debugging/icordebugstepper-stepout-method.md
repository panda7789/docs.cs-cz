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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987425"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="3f143-102">ICorDebugStepper::StepOut – metoda</span><span class="sxs-lookup"><span data-stu-id="3f143-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="3f143-103">Způsobí, že tento icordebugstepper – jedním krokem prostřednictvím jeho nadřazeného vlákna a dokončit, jakmile aktuální rámec vrátí řízení volající rámec.</span><span class="sxs-lookup"><span data-stu-id="3f143-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f143-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f143-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f143-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f143-105">Remarks</span></span>  
 <span data-ttu-id="3f143-106">A `StepOut` operace se dokončí po návratu obvykle aktuální rámec volání rámce.</span><span class="sxs-lookup"><span data-stu-id="3f143-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="3f143-107">Pokud `StepOut` je volána, když v nespravovaném kódu, krok dokončí aktuální rámec návratu do spravovaného kódu, která ji zavolala.</span><span class="sxs-lookup"><span data-stu-id="3f143-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="3f143-108">V rozhraní .NET Framework verze 2.0, nepoužívejte `StepOut` s STOP_UNMANAGED příznak nastaven, protože se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="3f143-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="3f143-109">(Použití [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) nastavení příznaků pro krokování.) Spolupráce ladicí programy musí Krok ven do nativního kódu sami.</span><span class="sxs-lookup"><span data-stu-id="3f143-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f143-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f143-110">Requirements</span></span>  
 <span data-ttu-id="3f143-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f143-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f143-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f143-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f143-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f143-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f143-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f143-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
