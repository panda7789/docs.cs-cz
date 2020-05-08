---
title: ICorDebugController::HasQueuedCallbacks – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: bd656445c2451d0583ddbc45e71c9e090bb80305
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892782"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="b6fc2-102">ICorDebugController::HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="b6fc2-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="b6fc2-103">Získá hodnotu, která označuje, zda jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="b6fc2-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6fc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6fc2-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6fc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6fc2-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="b6fc2-106">pro Ukazatel na objekt "ICorDebugThread", který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="b6fc2-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="b6fc2-107">mimo Ukazatel na hodnotu, která je `true` v případě, že jakékoli spravované zpětné volání jsou aktuálně zařazeny do fronty pro zadané vlákno; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="b6fc2-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="b6fc2-108">Pokud je pro `pThread` parametr zadána hodnota null, `HasQueuedCallbacks` vrátí `true` se, pokud jsou aktuálně spravovaná zpětná volání zařazena do fronty pro jakékoli vlákno.</span><span class="sxs-lookup"><span data-stu-id="b6fc2-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6fc2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6fc2-109">Remarks</span></span>  
 <span data-ttu-id="b6fc2-110">Zpětná volání budou odeslána po jednom, pokaždé, když se zavolá [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6fc2-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="b6fc2-111">Ladicí program může tento příznak kontrolovat, pokud chce ohlásit více událostí ladění, ke kterým dochází současně.</span><span class="sxs-lookup"><span data-stu-id="b6fc2-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="b6fc2-112">Když jsou události ladění zařazeny do fronty, již byly k dispozici, takže ladicí program musí celou frontu vyprázdnit, aby bylo zajištěno, že je stav laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="b6fc2-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="b6fc2-113">(Volání `ICorDebugController::Continue` vyprázdní frontu.) Pokud například fronta obsahuje dvě události ladění ve vlákně *x*a ladicí program pozastaví vlákno *x* po první události ladění a potom volá `ICorDebugController::Continue`, bude druhá událost ladění pro vlákno *x* odeslána, i když bylo vlákno pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="b6fc2-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6fc2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6fc2-114">Requirements</span></span>  
 <span data-ttu-id="b6fc2-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6fc2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6fc2-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6fc2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6fc2-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6fc2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6fc2-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6fc2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6fc2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6fc2-119">See also</span></span>
