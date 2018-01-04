---
title: "ICorDebugStepper::StepOut – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d6462f166e9c734dacc7ebee13cb82e3b12158b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="9d192-102">ICorDebugStepper::StepOut – metoda</span><span class="sxs-lookup"><span data-stu-id="9d192-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="9d192-103">Způsobí, že tento ICorDebugStepper jedním krokem přes jeho obsahující vláken a provést při aktuální rámec vrátí prvek na snímek, volání.</span><span class="sxs-lookup"><span data-stu-id="9d192-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d192-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d192-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9d192-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d192-105">Remarks</span></span>  
 <span data-ttu-id="9d192-106">A `StepOut` operace dokončí po návratu normálně aktuální rámec volání rámečku.</span><span class="sxs-lookup"><span data-stu-id="9d192-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="9d192-107">Pokud `StepOut` je volána, když v nespravovaném kódu krok dokončí, když se vrátí aktuální rámec do spravovaného kódu, která je volána.</span><span class="sxs-lookup"><span data-stu-id="9d192-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="9d192-108">V rozhraní .NET Framework verze 2.0, nepoužívejte `StepOut` s STOP_UNMANAGED nastaven příznak vzhledem k tomu, že se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="9d192-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="9d192-109">(Použití [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) nastavit pro krokování s příznaky.) Spolupráce ladicí programy musí krok do nativního kódu sami.</span><span class="sxs-lookup"><span data-stu-id="9d192-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d192-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d192-110">Requirements</span></span>  
 <span data-ttu-id="9d192-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d192-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d192-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d192-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d192-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d192-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d192-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d192-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
