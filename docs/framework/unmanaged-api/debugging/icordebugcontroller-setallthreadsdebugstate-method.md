---
title: ICorDebugController::SetAllThreadsDebugState – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dffe95df75fafe293c225c513db7ff7896765fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501770"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="745c1-102">ICorDebugController::SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="745c1-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="745c1-103">Nastaví stav ladění všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="745c1-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="745c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="745c1-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="745c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="745c1-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="745c1-106">[in] Hodnota výčtu "cordebugthreadstate –", která určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="745c1-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="745c1-107">[in] Ukazatel na objekt "ICorDebugThread", který představuje vlákno má vyloučit z nastavení stavu ladění.</span><span class="sxs-lookup"><span data-stu-id="745c1-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="745c1-108">Pokud je tato hodnota null, je vyloučené žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="745c1-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="745c1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="745c1-109">Remarks</span></span>  
 <span data-ttu-id="745c1-110">`SetAllThreadsDebugState` Metoda může mít vliv na vlákna, které nejsou viditelné prostřednictvím [enumeratethreads – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), tak vlákna, které pozastavené s `SetAllThreadsDebugState` metoda muset obnovit s `SetAllThreadsDebugState` metoda.</span><span class="sxs-lookup"><span data-stu-id="745c1-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="745c1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="745c1-111">Requirements</span></span>  
 <span data-ttu-id="745c1-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="745c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="745c1-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="745c1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="745c1-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="745c1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="745c1-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="745c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="745c1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="745c1-116">See also</span></span>

