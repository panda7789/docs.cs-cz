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
ms.openlocfilehash: 602bcd12d1fd4c5806de6db81252731baa447b7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988218"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="89628-102">ICorDebugManagedCallback::EvalException – metoda</span><span class="sxs-lookup"><span data-stu-id="89628-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="89628-103">Upozorní ladicího programu, že byl ukončen zkušební verzi s neošetřenou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="89628-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89628-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89628-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89628-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89628-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="89628-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve kterém byl ukončen hodnocení.</span><span class="sxs-lookup"><span data-stu-id="89628-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="89628-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, ve kterém byl ukončen hodnocení.</span><span class="sxs-lookup"><span data-stu-id="89628-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="89628-108">[in] Ukazatel na objekt icordebugeval –, který představuje kód, který provádí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="89628-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89628-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89628-109">Requirements</span></span>  
 <span data-ttu-id="89628-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89628-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89628-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89628-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89628-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89628-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89628-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89628-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89628-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89628-114">See also</span></span>

- [<span data-ttu-id="89628-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89628-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
