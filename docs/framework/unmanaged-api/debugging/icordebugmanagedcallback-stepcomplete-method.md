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
ms.openlocfilehash: 89b010706222ad44bccabd94191c42a888584944
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212656"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="a9bb8-102">ICorDebugManagedCallback::StepComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="a9bb8-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="a9bb8-103">Oznamuje ladicímu programu, že byl krok dokončen.</span><span class="sxs-lookup"><span data-stu-id="a9bb8-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9bb8-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9bb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9bb8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a9bb8-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, ve kterém byl krok dokončen.</span><span class="sxs-lookup"><span data-stu-id="a9bb8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a9bb8-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém byl krok dokončen.</span><span class="sxs-lookup"><span data-stu-id="a9bb8-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="a9bb8-108">pro Ukazatel na objekt ICorDebugStepper, který představuje krok ve spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="a9bb8-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="a9bb8-109">pro Hodnota výčtu CorDebugStepReason –, která označuje výsledek jednotlivého kroku.</span><span class="sxs-lookup"><span data-stu-id="a9bb8-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9bb8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9bb8-110">Remarks</span></span>  
 <span data-ttu-id="a9bb8-111">Stepper může být použita k pokračování v procházení, pokud je to žádoucí, pokud ladění není ukončeno.</span><span class="sxs-lookup"><span data-stu-id="a9bb8-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9bb8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9bb8-112">Requirements</span></span>  
 <span data-ttu-id="a9bb8-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9bb8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9bb8-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9bb8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9bb8-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a9bb8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9bb8-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9bb8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bb8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9bb8-117">See also</span></span>

- [<span data-ttu-id="a9bb8-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9bb8-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
