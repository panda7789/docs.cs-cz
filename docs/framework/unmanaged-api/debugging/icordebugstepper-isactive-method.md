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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4166b63e0bb0ae276c48abb961e381809cc9792
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471417"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="ac6be-102">ICorDebugStepper::IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="ac6be-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="ac6be-103">Získá hodnotu určující, zda tento icordebugstepper – právě probíhá krok.</span><span class="sxs-lookup"><span data-stu-id="ac6be-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac6be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac6be-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac6be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac6be-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="ac6be-106">[out] Vrátí `true` Pokud krokovače právě probíhá krok; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="ac6be-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac6be-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac6be-107">Remarks</span></span>  
 <span data-ttu-id="ac6be-108">Všechny akce kroku zůstane aktivní, dokud ladicí program přijímá [icordebugmanagedcallback::stepcomplete –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) volání, které se automaticky deaktivuje krokovače.</span><span class="sxs-lookup"><span data-stu-id="ac6be-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="ac6be-109">Krokovač může také deaktivuje předčasně ukončen voláním [icordebugstepper::Deactivate –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) před zpětného volání je dosaženo stavu.</span><span class="sxs-lookup"><span data-stu-id="ac6be-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac6be-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac6be-110">Requirements</span></span>  
 <span data-ttu-id="ac6be-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac6be-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac6be-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac6be-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac6be-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac6be-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac6be-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac6be-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
