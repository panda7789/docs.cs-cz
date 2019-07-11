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
ms.openlocfilehash: 9348652129a3357784654006dc16d822298f28f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749959"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="b5621-102">ICorDebugController::SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="b5621-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="b5621-103">Nastaví stav ladění všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="b5621-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5621-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5621-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5621-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5621-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="b5621-106">[in] Hodnota výčtu "cordebugthreadstate –", která určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b5621-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="b5621-107">[in] Ukazatel na objekt "ICorDebugThread", který představuje vlákno má vyloučit z nastavení stavu ladění.</span><span class="sxs-lookup"><span data-stu-id="b5621-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="b5621-108">Pokud je tato hodnota null, je vyloučené žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="b5621-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5621-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5621-109">Remarks</span></span>  
 <span data-ttu-id="b5621-110">`SetAllThreadsDebugState` Metoda může mít vliv na vlákna, které nejsou viditelné prostřednictvím [enumeratethreads – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), tak vlákna, které pozastavené s `SetAllThreadsDebugState` metoda muset obnovit s `SetAllThreadsDebugState` metoda.</span><span class="sxs-lookup"><span data-stu-id="b5621-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5621-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5621-111">Requirements</span></span>  
 <span data-ttu-id="b5621-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5621-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5621-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5621-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5621-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5621-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5621-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5621-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5621-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5621-116">See also</span></span>
