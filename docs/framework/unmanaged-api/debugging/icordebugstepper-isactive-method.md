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
ms.openlocfilehash: dcb276e6fba6a1b46b6be630804dc6f07c211b86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420505"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="c94f9-102">ICorDebugStepper::IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="c94f9-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="c94f9-103">Získá hodnotu, která určuje, zda tento ICorDebugStepper právě probíhá krok.</span><span class="sxs-lookup"><span data-stu-id="c94f9-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c94f9-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c94f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c94f9-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="c94f9-106">[out] Vrátí `true` Pokud krokovače právě probíhá krok; jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="c94f9-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c94f9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c94f9-107">Remarks</span></span>  
 <span data-ttu-id="c94f9-108">Všechny akce krok zůstane aktivní, dokud obdrží ladicího programu [icordebugmanagedcallback::stepcomplete –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) volání, které automaticky deaktivuje krokovače.</span><span class="sxs-lookup"><span data-stu-id="c94f9-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="c94f9-109">Krokovač může být také předčasně deaktivováno voláním [icordebugstepper::Deactivate –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) před zpětné volání je dosaženo stavu.</span><span class="sxs-lookup"><span data-stu-id="c94f9-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94f9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c94f9-110">Requirements</span></span>  
 <span data-ttu-id="c94f9-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c94f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94f9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c94f9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c94f9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c94f9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c94f9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c94f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
