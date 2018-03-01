---
title: "ICorDebugManagedCallback::StepComplete – metoda"
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
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e7a09216284593c79c0cda6f5283ea8250678af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="138e1-102">ICorDebugManagedCallback::StepComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="138e1-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="138e1-103">Aby byla dokončena krok upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="138e1-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="138e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="138e1-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="138e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="138e1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="138e1-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující vláken, ve kterém byla dokončena v kroku.</span><span class="sxs-lookup"><span data-stu-id="138e1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="138e1-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, ve kterém byla dokončena v kroku.</span><span class="sxs-lookup"><span data-stu-id="138e1-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="138e1-108">[v] Ukazatel na ICorDebugStepper objekt, který reprezentuje krokem při provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="138e1-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="138e1-109">[v] Hodnota CorDebugStepReason – výčet, který určuje výsledek jednotlivé kroky.</span><span class="sxs-lookup"><span data-stu-id="138e1-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="138e1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="138e1-110">Remarks</span></span>  
 <span data-ttu-id="138e1-111">Krokovače může sloužit k krokování pokračovat v případě potřeby, pokud je ladění je ukončen.</span><span class="sxs-lookup"><span data-stu-id="138e1-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="138e1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="138e1-112">Requirements</span></span>  
 <span data-ttu-id="138e1-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="138e1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="138e1-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="138e1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="138e1-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="138e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="138e1-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="138e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138e1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="138e1-117">See Also</span></span>  
 [<span data-ttu-id="138e1-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="138e1-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
