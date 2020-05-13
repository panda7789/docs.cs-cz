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
ms.openlocfilehash: 20a841006d51671a491e11c4e40287baf739d191
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209822"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="3ba80-102">ICorDebugManagedCallback::EvalException – metoda</span><span class="sxs-lookup"><span data-stu-id="3ba80-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="3ba80-103">Oznamuje ladicímu programu, že vyhodnocení skončilo neošetřenou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="3ba80-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ba80-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ba80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ba80-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3ba80-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve které bylo vyhodnocení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="3ba80-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3ba80-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém bylo vyhodnocení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="3ba80-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="3ba80-108">pro Ukazatel na objekt ICorDebugEval, který představuje kód, který provedl vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="3ba80-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ba80-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ba80-109">Requirements</span></span>  
 <span data-ttu-id="3ba80-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ba80-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ba80-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ba80-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ba80-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ba80-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ba80-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ba80-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba80-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ba80-114">See also</span></span>

- [<span data-ttu-id="3ba80-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ba80-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
