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
ms.openlocfilehash: 3ae93081bd201f745fa47bc01a9c6fcbf6e9f63c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781859"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="21f9f-102">ICorDebugManagedCallback::EvalException – metoda</span><span class="sxs-lookup"><span data-stu-id="21f9f-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="21f9f-103">Oznamuje ladicímu programu, že vyhodnocení skončilo neošetřenou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="21f9f-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21f9f-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21f9f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="21f9f-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve které bylo vyhodnocení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="21f9f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="21f9f-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém bylo vyhodnocení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="21f9f-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="21f9f-108">pro Ukazatel na objekt ICorDebugEval, který představuje kód, který provedl vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="21f9f-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f9f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21f9f-109">Requirements</span></span>  
 <span data-ttu-id="21f9f-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f9f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f9f-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21f9f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21f9f-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="21f9f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21f9f-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f9f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f9f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21f9f-114">See also</span></span>

- [<span data-ttu-id="21f9f-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21f9f-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
