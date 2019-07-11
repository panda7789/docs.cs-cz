---
title: ICorDebugManagedCallback::EvalComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a874646a6746a9b2fc8ce597e6c1ca47340c199a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759643"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="9bb34-102">ICorDebugManagedCallback::EvalComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="9bb34-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="9bb34-103">Upozorní ladicího programu, že zkušební verzi bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="9bb34-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bb34-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bb34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bb34-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9bb34-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve kterém se provedla hodnocení.</span><span class="sxs-lookup"><span data-stu-id="9bb34-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9bb34-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, ve kterém se provedla hodnocení.</span><span class="sxs-lookup"><span data-stu-id="9bb34-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="9bb34-108">[in] Ukazatel na objekt icordebugeval –, který představuje kód, který provádí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="9bb34-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bb34-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bb34-109">Requirements</span></span>  
 <span data-ttu-id="9bb34-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bb34-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bb34-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bb34-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bb34-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bb34-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bb34-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bb34-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb34-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bb34-114">See also</span></span>

- [<span data-ttu-id="9bb34-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bb34-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
