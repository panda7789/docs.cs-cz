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
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791778"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="96fdd-102">ICorDebugStepper::IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="96fdd-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="96fdd-103">Načte hodnotu, která označuje, jestli tento ICorDebugStepper aktuálně provádí krok.</span><span class="sxs-lookup"><span data-stu-id="96fdd-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96fdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96fdd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96fdd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96fdd-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="96fdd-106">mimo Vrátí `true`, pokud stepper aktuálně provádí krok; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="96fdd-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96fdd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96fdd-107">Remarks</span></span>  
 <span data-ttu-id="96fdd-108">Jakákoli akce kroku zůstane aktivní, dokud ladicí program nepřijme volání [ICorDebugManagedCallback:: StepComplete –](icordebugmanagedcallback-stepcomplete-method.md) , které automaticky deaktivuje stepper.</span><span class="sxs-lookup"><span data-stu-id="96fdd-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="96fdd-109">Stepper se může předčasně deaktivovat také voláním [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) před dosažením podmínky zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="96fdd-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96fdd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96fdd-110">Requirements</span></span>  
 <span data-ttu-id="96fdd-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96fdd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96fdd-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96fdd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96fdd-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="96fdd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96fdd-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96fdd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
