---
title: ICorDebugManagedCallback::EvalException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4414bab535b63f55a580e93cc6de9cb0dedc073c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415513"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="b6ebd-102">ICorDebugManagedCallback::EvalException – metoda</span><span class="sxs-lookup"><span data-stu-id="b6ebd-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="b6ebd-103">Upozorní ladicí program, že zkušební verzi ukončilo došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ebd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6ebd-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6ebd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6ebd-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b6ebd-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, ve kterém byla ukončena vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b6ebd-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, ve kterém byla ukončena vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="b6ebd-108">[v] Ukazatel na ICorDebugEval objekt, který představuje kód, který provádí vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ebd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6ebd-109">Requirements</span></span>  
 <span data-ttu-id="b6ebd-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ebd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ebd-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6ebd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6ebd-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6ebd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ebd-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ebd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ebd-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6ebd-114">See Also</span></span>  
 [<span data-ttu-id="b6ebd-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6ebd-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
