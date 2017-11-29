---
title: "ICorDebugController::HasQueuedCallbacks – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.HasQueuedCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81830cbadcf9fb359b8e1a74cd47f9d18543c29c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="b310a-102">ICorDebugController::HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="b310a-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="b310a-103">Získá hodnotu, která určuje, zda všechny spravované zpětná volání jsou aktuálně ve frontě pro zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="b310a-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b310a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b310a-104">Syntax</span></span>  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b310a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b310a-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="b310a-106">[v] Ukazatel na objekt "ICorDebugThread", který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="b310a-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="b310a-107">[out] Ukazatel na hodnotu, která je `true` Pokud žádné spravované zpětná volání jsou aktuálně ve frontě pro zadaný vlákno, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="b310a-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="b310a-108">Pokud je zadána hodnota null pro `pThread` parametr `HasQueuedCallbacks` vrátí `true` Pokud aktuálně nejsou k dispozici spravované zpětná volání zařazených do fronty pro všechny přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="b310a-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b310a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b310a-109">Remarks</span></span>  
 <span data-ttu-id="b310a-110">Zpětná volání bude odeslat jeden po druhém, pokaždé, když [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="b310a-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="b310a-111">Ladicí program můžete zkontrolovat tento příznak, pokud chcete ohlásit více ladění událostí, které nastat současně.</span><span class="sxs-lookup"><span data-stu-id="b310a-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="b310a-112">Při ladění událostí jsou zařazeny do fronty, se již došlo, takže ladicí program musí vyprazdňování celý frontu jistotu stav ladění.</span><span class="sxs-lookup"><span data-stu-id="b310a-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="b310a-113">(Volání `ICorDebugController::Continue` na vyprazdňování fronty.) Například, pokud fronty obsahuje dvě ladění události ve vlákně *X*, a ladicí program pozastaví vlákno *X* po první ladění událostí a volání `ICorDebugController::Continue`, druhá událost ladění pro vlákno *X* bude odeslána, i když vlákno bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="b310a-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b310a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b310a-114">Requirements</span></span>  
 <span data-ttu-id="b310a-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b310a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b310a-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b310a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b310a-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b310a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b310a-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b310a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b310a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b310a-119">See Also</span></span>  
 
