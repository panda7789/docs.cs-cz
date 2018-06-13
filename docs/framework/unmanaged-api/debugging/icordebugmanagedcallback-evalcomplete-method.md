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
ms.openlocfilehash: 688c5a4b5a18cea444ebf1d63f3ea012a5d815c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415207"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="581d2-102">ICorDebugManagedCallback::EvalComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="581d2-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="581d2-103">Upozorní ladicí program dokončí zkušební verzi.</span><span class="sxs-lookup"><span data-stu-id="581d2-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="581d2-104">Syntax</span></span>  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="581d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="581d2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="581d2-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, ve kterém byla provedena vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="581d2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="581d2-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, ve kterém byla provedena vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="581d2-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="581d2-108">[v] Ukazatel na ICorDebugEval objekt, který představuje kód, který provádí vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="581d2-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="581d2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="581d2-109">Requirements</span></span>  
 <span data-ttu-id="581d2-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="581d2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="581d2-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="581d2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="581d2-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="581d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="581d2-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="581d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581d2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="581d2-114">See Also</span></span>  
 [<span data-ttu-id="581d2-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="581d2-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
