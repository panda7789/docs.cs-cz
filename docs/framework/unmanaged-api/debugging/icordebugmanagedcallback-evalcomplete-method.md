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
ms.openlocfilehash: c1261942865419762fa454eb8d4bc5e5d99e86d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193171"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="9d4ae-102">ICorDebugManagedCallback::EvalComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="9d4ae-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="9d4ae-103">Upozorní ladicího programu, že zkušební verzi bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="9d4ae-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d4ae-104">Syntax</span></span>  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d4ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d4ae-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9d4ae-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve kterém se provedla hodnocení.</span><span class="sxs-lookup"><span data-stu-id="9d4ae-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9d4ae-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, ve kterém se provedla hodnocení.</span><span class="sxs-lookup"><span data-stu-id="9d4ae-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="9d4ae-108">[in] Ukazatel na objekt icordebugeval –, který představuje kód, který provádí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="9d4ae-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4ae-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d4ae-109">Requirements</span></span>  
 <span data-ttu-id="9d4ae-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4ae-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d4ae-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d4ae-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d4ae-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9d4ae-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9d4ae-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d4ae-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d4ae-114">See also</span></span>

- [<span data-ttu-id="9d4ae-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d4ae-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
