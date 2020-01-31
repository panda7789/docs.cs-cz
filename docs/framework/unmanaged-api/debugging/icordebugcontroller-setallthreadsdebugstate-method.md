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
ms.openlocfilehash: be7fce700756d7120e0853446b7b307ec77c2080
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783764"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="2cdd3-102">ICorDebugController::SetAllThreadsDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="2cdd3-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="2cdd3-103">Nastaví stav ladění pro všechna spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="2cdd3-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cdd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cdd3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cdd3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cdd3-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="2cdd3-106">pro Hodnota výčtu "CorDebugThreadState –", která určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="2cdd3-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="2cdd3-107">pro Ukazatel na objekt "ICorDebugThread", který představuje vlákno, které má být vyloučeno z nastavení stavu ladění.</span><span class="sxs-lookup"><span data-stu-id="2cdd3-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="2cdd3-108">Pokud je tato hodnota null, nezbavuje se žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="2cdd3-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cdd3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cdd3-109">Remarks</span></span>  
 <span data-ttu-id="2cdd3-110">Metoda `SetAllThreadsDebugState` může ovlivnit vlákna, která nejsou viditelná prostřednictvím [metody EnumerateThreads –](icordebugcontroller-enumeratethreads-method.md), takže vlákna, která byla pozastavená metodou `SetAllThreadsDebugState`, bude nutné obnovit pomocí metody `SetAllThreadsDebugState`.</span><span class="sxs-lookup"><span data-stu-id="2cdd3-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cdd3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cdd3-111">Requirements</span></span>  
 <span data-ttu-id="2cdd3-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cdd3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cdd3-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2cdd3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cdd3-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2cdd3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cdd3-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cdd3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cdd3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cdd3-116">See also</span></span>
