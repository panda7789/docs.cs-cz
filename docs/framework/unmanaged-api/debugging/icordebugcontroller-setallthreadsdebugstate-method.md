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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138473"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="7a134-102">ICorDebugController::SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="7a134-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="7a134-103">Nastaví stav ladění všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="7a134-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a134-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a134-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a134-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a134-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="7a134-106">[in] Hodnota výčtu "cordebugthreadstate –", která určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="7a134-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="7a134-107">[in] Ukazatel na objekt "ICorDebugThread", který představuje vlákno má vyloučit z nastavení stavu ladění.</span><span class="sxs-lookup"><span data-stu-id="7a134-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="7a134-108">Pokud je tato hodnota null, je vyloučené žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="7a134-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a134-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a134-109">Remarks</span></span>  
 <span data-ttu-id="7a134-110">`SetAllThreadsDebugState` Metoda může mít vliv na vlákna, které nejsou viditelné prostřednictvím [enumeratethreads – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), tak vlákna, které pozastavené s `SetAllThreadsDebugState` metoda muset obnovit s `SetAllThreadsDebugState` metoda.</span><span class="sxs-lookup"><span data-stu-id="7a134-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a134-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a134-111">Requirements</span></span>  
 <span data-ttu-id="7a134-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a134-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a134-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a134-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a134-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a134-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7a134-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7a134-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a134-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a134-116">See also</span></span>
