---
title: ICorDebugStepper::Step – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760565"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="0851c-102">ICorDebugStepper::Step – metoda</span><span class="sxs-lookup"><span data-stu-id="0851c-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="0851c-103">Způsobí, že tento icordebugstepper – jedním krokem prostřednictvím jeho nadřazeného vlákna a volitelně do pokračujte v jedné krokování funkcí, které jsou volány vlákna.</span><span class="sxs-lookup"><span data-stu-id="0851c-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0851c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0851c-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0851c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0851c-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="0851c-106">[in] Nastavte na `true` krok do funkce, která je volána v rámci vlákna.</span><span class="sxs-lookup"><span data-stu-id="0851c-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="0851c-107">Nastavte na `false` krok přes funkci.</span><span class="sxs-lookup"><span data-stu-id="0851c-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0851c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0851c-108">Remarks</span></span>  
 <span data-ttu-id="0851c-109">Krok dokončí, když modul common language runtime provádí další instrukci spravované v rámci této krokovač.</span><span class="sxs-lookup"><span data-stu-id="0851c-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="0851c-110">Pokud `Step` se volalo krokovač, která není v spravovaného kódu, krok dokončí další instrukci spravovaný kód je spuštěn metodou vlákna.</span><span class="sxs-lookup"><span data-stu-id="0851c-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0851c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0851c-111">Requirements</span></span>  
 <span data-ttu-id="0851c-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0851c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0851c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0851c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0851c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0851c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0851c-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0851c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
