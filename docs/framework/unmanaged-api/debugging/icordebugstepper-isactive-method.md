---
title: ICorDebugStepper::IsActive – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: faddf30248b58c68037635480d8977f22ad077d0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379026"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="eee2b-102">ICorDebugStepper::IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="eee2b-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="eee2b-103">Načte hodnotu, která označuje, jestli tento ICorDebugStepper aktuálně provádí krok.</span><span class="sxs-lookup"><span data-stu-id="eee2b-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eee2b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eee2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eee2b-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="eee2b-106">mimo Vrátí, `true` zda stepper aktuálně provádí krok. v opačném případě vrátí hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="eee2b-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eee2b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eee2b-107">Remarks</span></span>  
 <span data-ttu-id="eee2b-108">Jakákoli akce kroku zůstane aktivní, dokud ladicí program nepřijme volání [ICorDebugManagedCallback:: StepComplete –](icordebugmanagedcallback-stepcomplete-method.md) , které automaticky deaktivuje stepper.</span><span class="sxs-lookup"><span data-stu-id="eee2b-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="eee2b-109">Stepper se může předčasně deaktivovat také voláním [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) před dosažením podmínky zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="eee2b-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eee2b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eee2b-110">Requirements</span></span>  
 <span data-ttu-id="eee2b-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eee2b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eee2b-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eee2b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eee2b-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eee2b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eee2b-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eee2b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
