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
ms.openlocfilehash: e044b1a2ad777868e33cd64bc8d09a9b76d547aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130670"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="5759e-102">ICorDebugManagedCallback::StepComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="5759e-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="5759e-103">Oznamuje ladicímu programu, že byl krok dokončen.</span><span class="sxs-lookup"><span data-stu-id="5759e-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5759e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5759e-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5759e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5759e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5759e-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, ve kterém byl krok dokončen.</span><span class="sxs-lookup"><span data-stu-id="5759e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5759e-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém byl krok dokončen.</span><span class="sxs-lookup"><span data-stu-id="5759e-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="5759e-108">pro Ukazatel na objekt ICorDebugStepper, který představuje krok ve spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="5759e-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="5759e-109">pro Hodnota výčtu CorDebugStepReason –, která označuje výsledek jednotlivého kroku.</span><span class="sxs-lookup"><span data-stu-id="5759e-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5759e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5759e-110">Remarks</span></span>  
 <span data-ttu-id="5759e-111">Stepper může být použita k pokračování v procházení, pokud je to žádoucí, pokud ladění není ukončeno.</span><span class="sxs-lookup"><span data-stu-id="5759e-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5759e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5759e-112">Requirements</span></span>  
 <span data-ttu-id="5759e-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5759e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5759e-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5759e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5759e-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5759e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5759e-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5759e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5759e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5759e-117">See also</span></span>

- [<span data-ttu-id="5759e-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5759e-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
