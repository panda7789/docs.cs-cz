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
ms.openlocfilehash: dbf12612bb432f8935d08bdeac0bbcb471c38c54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759636"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="4d4d9-102">ICorDebugManagedCallback::EvalException – metoda</span><span class="sxs-lookup"><span data-stu-id="4d4d9-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="4d4d9-103">Upozorní ladicího programu, že byl ukončen zkušební verzi s neošetřenou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d4d9-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d4d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d4d9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4d4d9-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve kterém byl ukončen hodnocení.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="4d4d9-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, ve kterém byl ukončen hodnocení.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="4d4d9-108">[in] Ukazatel na objekt icordebugeval –, který představuje kód, který provádí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d4d9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d4d9-109">Requirements</span></span>  
 <span data-ttu-id="4d4d9-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d4d9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d4d9-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d4d9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d4d9-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d4d9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d4d9-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d4d9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4d9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d4d9-114">See also</span></span>

- [<span data-ttu-id="4d4d9-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d4d9-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
