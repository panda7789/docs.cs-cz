---
title: "ICorDebugStepper::Step – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f921725d6794f08530a537462208264ced1dc089
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="c28fc-102">ICorDebugStepper::Step – metoda</span><span class="sxs-lookup"><span data-stu-id="c28fc-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="c28fc-103">Způsobí, že tento ICorDebugStepper jedním krokem přes jeho obsahující vláken a volitelně můžete do pokračovat jedním procházení funkce, které se nazývají vlákna.</span><span class="sxs-lookup"><span data-stu-id="c28fc-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c28fc-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c28fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c28fc-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="c28fc-106">[v] Nastavte na `true` k krokování s vnořením funkci, která je volána v rámci vlákno.</span><span class="sxs-lookup"><span data-stu-id="c28fc-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="c28fc-107">Nastavte na `false` krok přes funkci.</span><span class="sxs-lookup"><span data-stu-id="c28fc-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c28fc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c28fc-108">Remarks</span></span>  
 <span data-ttu-id="c28fc-109">V kroku dokončení, když modul common language runtime provede další instrukce spravované v rámci této krokovač.</span><span class="sxs-lookup"><span data-stu-id="c28fc-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="c28fc-110">Pokud `Step` je volána na krokovač, který se nenachází ve spravovaném kódu, krok dokončí při další instrukce spravovaného kódu vlákno.</span><span class="sxs-lookup"><span data-stu-id="c28fc-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28fc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c28fc-111">Requirements</span></span>  
 <span data-ttu-id="c28fc-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28fc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28fc-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c28fc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c28fc-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c28fc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c28fc-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c28fc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
