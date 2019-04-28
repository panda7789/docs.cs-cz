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
ms.openlocfilehash: 280dc3f0271d7326fe4c22b813abebfd4d45c89e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749147"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="dfb9e-102">ICorDebugController::SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="dfb9e-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="dfb9e-103">Nastaví stav ladění všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfb9e-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfb9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfb9e-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="dfb9e-106">[in] Hodnota výčtu "cordebugthreadstate –", která určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="dfb9e-107">[in] Ukazatel na objekt "ICorDebugThread", který představuje vlákno má vyloučit z nastavení stavu ladění.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="dfb9e-108">Pokud je tato hodnota null, je vyloučené žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfb9e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfb9e-109">Remarks</span></span>  
 <span data-ttu-id="dfb9e-110">`SetAllThreadsDebugState` Metoda může mít vliv na vlákna, které nejsou viditelné prostřednictvím [enumeratethreads – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), tak vlákna, které pozastavené s `SetAllThreadsDebugState` metoda muset obnovit s `SetAllThreadsDebugState` metoda.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfb9e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfb9e-111">Requirements</span></span>  
 <span data-ttu-id="dfb9e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfb9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfb9e-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfb9e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfb9e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfb9e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfb9e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfb9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb9e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfb9e-116">See also</span></span>
