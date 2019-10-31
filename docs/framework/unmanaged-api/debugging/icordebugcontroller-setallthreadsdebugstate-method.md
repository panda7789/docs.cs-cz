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
ms.openlocfilehash: 1190f83e2671216cf1627eeb710ba576e4b2ec93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125359"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="7d90b-102">ICorDebugController::SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="7d90b-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="7d90b-103">Nastaví stav ladění pro všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="7d90b-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d90b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d90b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d90b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d90b-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="7d90b-106">pro Hodnota výčtu "CorDebugThreadState –", která určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="7d90b-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="7d90b-107">pro Ukazatel na objekt "ICorDebugThread", který představuje vlákno, které má být vyloučeno z nastavení stavu ladění.</span><span class="sxs-lookup"><span data-stu-id="7d90b-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="7d90b-108">Pokud je tato hodnota null, nezbavuje se žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="7d90b-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d90b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d90b-109">Remarks</span></span>  
 <span data-ttu-id="7d90b-110">Metoda `SetAllThreadsDebugState` může ovlivnit vlákna, která nejsou viditelná prostřednictvím [metody EnumerateThreads –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), takže vlákna, která byla pozastavená metodou `SetAllThreadsDebugState`, bude nutné obnovit pomocí metody `SetAllThreadsDebugState`.</span><span class="sxs-lookup"><span data-stu-id="7d90b-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d90b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d90b-111">Requirements</span></span>  
 <span data-ttu-id="7d90b-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d90b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d90b-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d90b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d90b-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d90b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d90b-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d90b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d90b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d90b-116">See also</span></span>
