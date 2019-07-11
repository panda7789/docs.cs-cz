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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d17f51867b64780fca9b21c5f48c88db36343af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748781"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="b5c51-102">ICorDebugController::HasQueuedCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="b5c51-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="b5c51-103">Získá hodnotu určující, zda všechny spravované zpětná volání jsou právě ve frontě pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="b5c51-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5c51-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5c51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5c51-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="b5c51-106">[in] Ukazatel na objekt "ICorDebugThread", který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="b5c51-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="b5c51-107">[out] Ukazatel na hodnotu, která je `true` Pokud žádné spravované zpětná volání nejsou aktuálně ve frontě pro zadaný podproces; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="b5c51-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="b5c51-108">Pokud je zadána hodnota null pro `pThread` parametr `HasQueuedCallbacks` vrátí `true` Pokud aktuálně spravované zpětná volání zařazených do fronty pro jakékoli vlákno.</span><span class="sxs-lookup"><span data-stu-id="b5c51-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5c51-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5c51-109">Remarks</span></span>  
 <span data-ttu-id="b5c51-110">Zpětná volání bude odbavované jeden po druhém, pokaždé, když [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="b5c51-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="b5c51-111">Ladicí program můžete zkontrolovat tento příznak, pokud chce sestavy více ladění události, které probíhají souběžně.</span><span class="sxs-lookup"><span data-stu-id="b5c51-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="b5c51-112">Při ladění událostí se zařadí do fronty, jsou již došlo, aby ladicí program musí vyprázdnit celá fronta opravdu o stavu laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="b5c51-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="b5c51-113">(Volání `ICorDebugController::Continue` k vyprázdnění fronty.) Například, pokud tato fronta obsahuje dvě ladění události na vlákně *X*, a ladicí program pozastaví vlákno *X* po první ladění události a poté zavolá `ICorDebugController::Continue`, druhá událost ladění pro vlákno *X* bude odeslána, i když je pozastavená vlákna.</span><span class="sxs-lookup"><span data-stu-id="b5c51-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5c51-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5c51-114">Requirements</span></span>  
 <span data-ttu-id="b5c51-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5c51-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c51-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5c51-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5c51-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5c51-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5c51-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5c51-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c51-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5c51-119">See also</span></span>
