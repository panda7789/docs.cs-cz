---
title: ICorDebugManagedCallback::StepComplete – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5b243d8c618559bd4371bf3acde1136f532f55e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476136"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="5911f-102">ICorDebugManagedCallback::StepComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="5911f-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="5911f-103">Upozorní ladicího programu, že se dokončil krok.</span><span class="sxs-lookup"><span data-stu-id="5911f-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5911f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5911f-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5911f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5911f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5911f-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vláken, ve kterém byla dokončena v kroku.</span><span class="sxs-lookup"><span data-stu-id="5911f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5911f-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, ve kterém byla dokončena v kroku.</span><span class="sxs-lookup"><span data-stu-id="5911f-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="5911f-108">[in] Ukazatel na objekt icordebugstepper –, který představuje krok ve spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="5911f-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="5911f-109">[in] Hodnota cordebugstepreason – výčet, který určuje výsledek jednotlivé kroky.</span><span class="sxs-lookup"><span data-stu-id="5911f-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5911f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5911f-110">Remarks</span></span>  
 <span data-ttu-id="5911f-111">Krokovače můžou sloužit k dál, krokování v případě potřeby, pokud ladění je ukončen.</span><span class="sxs-lookup"><span data-stu-id="5911f-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5911f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5911f-112">Requirements</span></span>  
 <span data-ttu-id="5911f-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5911f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5911f-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5911f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5911f-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5911f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5911f-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5911f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5911f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5911f-117">See also</span></span>
- [<span data-ttu-id="5911f-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5911f-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
