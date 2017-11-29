---
title: "ICorDebugManagedCallback::EvalException – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EvalException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed64c7b28d60e966e836ac75e6dd7c0848304a38
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="84cb8-102">ICorDebugManagedCallback::EvalException – metoda</span><span class="sxs-lookup"><span data-stu-id="84cb8-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="84cb8-103">Upozorní ladicí program, že zkušební verzi ukončilo došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="84cb8-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84cb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84cb8-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84cb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84cb8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="84cb8-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, ve kterém byla ukončena vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="84cb8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="84cb8-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, ve kterém byla ukončena vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="84cb8-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="84cb8-108">[v] Ukazatel na ICorDebugEval objekt, který představuje kód, který provádí vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="84cb8-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84cb8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84cb8-109">Requirements</span></span>  
 <span data-ttu-id="84cb8-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84cb8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84cb8-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84cb8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84cb8-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84cb8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84cb8-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84cb8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cb8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="84cb8-114">See Also</span></span>  
 [<span data-ttu-id="84cb8-115">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="84cb8-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
