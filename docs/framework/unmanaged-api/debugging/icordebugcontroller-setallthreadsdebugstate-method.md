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
ms.openlocfilehash: c2e8aaa2774e3e2699a73c40804391ca245047b1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976587"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="c8a05-102">ICorDebugController::SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="c8a05-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="c8a05-103">Nastaví stav ladění pro všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="c8a05-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8a05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8a05-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8a05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8a05-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="c8a05-106">pro Hodnota výčtu "CorDebugThreadState –", která určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="c8a05-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="c8a05-107">pro Ukazatel na objekt "ICorDebugThread", který představuje vlákno, které má být vyloučeno z nastavení stavu ladění.</span><span class="sxs-lookup"><span data-stu-id="c8a05-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="c8a05-108">Pokud je tato hodnota null, nezbavuje se žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="c8a05-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8a05-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8a05-109">Remarks</span></span>  
 <span data-ttu-id="c8a05-110">Metoda může ovlivnit vlákna, která nejsou viditelná prostřednictvím [metody EnumerateThreads –](icordebugcontroller-enumeratethreads-method.md), takže vlákna, která byla pozastavená `SetAllThreadsDebugState` pomocí metody, bude nutné obnovit `SetAllThreadsDebugState` metodou. `SetAllThreadsDebugState`</span><span class="sxs-lookup"><span data-stu-id="c8a05-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8a05-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8a05-111">Requirements</span></span>  
 <span data-ttu-id="c8a05-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8a05-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8a05-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c8a05-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8a05-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c8a05-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8a05-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8a05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a05-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8a05-116">See also</span></span>
