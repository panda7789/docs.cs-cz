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
ms.openlocfilehash: 0431b54997c9889e2b3206392e86e4dcde45ffb3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212448"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="601b8-102">ICorDebugManagedCallback::EvalComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="601b8-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="601b8-103">Oznamuje ladicímu programu, že bylo dokončeno vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="601b8-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="601b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="601b8-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="601b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="601b8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="601b8-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve které bylo provedeno vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="601b8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="601b8-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém bylo provedeno vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="601b8-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="601b8-108">pro Ukazatel na objekt ICorDebugEval, který představuje kód, který provedl vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="601b8-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="601b8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="601b8-109">Requirements</span></span>  
 <span data-ttu-id="601b8-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="601b8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="601b8-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="601b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="601b8-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="601b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="601b8-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="601b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="601b8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="601b8-114">See also</span></span>

- [<span data-ttu-id="601b8-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="601b8-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
