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
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137534"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="fc52a-102">ICorDebugStepper::Step – metoda</span><span class="sxs-lookup"><span data-stu-id="fc52a-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="fc52a-103">Způsobí, že se toto ICorDebugStepper do jednoho kroku prostřednictvím jeho obsahujícího vlákna a volitelně také pro pokračování v jednoduchém prostředí prostřednictvím funkcí, které jsou volány ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="fc52a-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc52a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc52a-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc52a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc52a-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="fc52a-106">pro Nastavte na `true` pro krokování do funkce, která je volána v rámci vlákna.</span><span class="sxs-lookup"><span data-stu-id="fc52a-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="fc52a-107">Nastavte na `false` pro krok nad funkcí.</span><span class="sxs-lookup"><span data-stu-id="fc52a-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc52a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc52a-108">Remarks</span></span>  
 <span data-ttu-id="fc52a-109">Krok se dokončí, když modul CLR (Common Language Runtime) provede další spravovanou instrukci v tomto stepper snímku.</span><span class="sxs-lookup"><span data-stu-id="fc52a-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="fc52a-110">Pokud je `Step` volána na stepper, který není ve spravovaném kódu, krok bude dokončen, když vlákno provede další instrukci spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fc52a-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc52a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc52a-111">Requirements</span></span>  
 <span data-ttu-id="fc52a-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc52a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc52a-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc52a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc52a-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fc52a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc52a-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc52a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
