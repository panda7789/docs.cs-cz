---
title: ICorProfilerCallback::RuntimeSuspendStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: cc01254d9604ce39c964c7d78059ef4087483c77
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503221"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="8de74-102">ICorProfilerCallback::RuntimeSuspendStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="8de74-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="8de74-103">Upozorní profileru, že modul runtime chystá pozastavit všechny běhové vlákna.</span><span class="sxs-lookup"><span data-stu-id="8de74-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8de74-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8de74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8de74-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="8de74-106">pro Hodnota výčtu [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) , která označuje důvod pro pozastavení.</span><span class="sxs-lookup"><span data-stu-id="8de74-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8de74-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8de74-107">Remarks</span></span>  
 <span data-ttu-id="8de74-108">Všechna vlákna modulu runtime, která jsou v nespravovaném kódu, mohou pokračovat v běhu, dokud se nepokusí znovu zadat modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8de74-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="8de74-109">V tomto okamžiku se také pozastaví, dokud modul runtime nebude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="8de74-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="8de74-110">To platí také pro nová vlákna, která vstupují do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8de74-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="8de74-111">Všechna vlákna v modulu runtime jsou buď okamžitě pozastavena, pokud jsou již v kódu přerušitelné, nebo jsou požádány o pozastavení, když dosáhnou přerušitelné kódu.</span><span class="sxs-lookup"><span data-stu-id="8de74-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de74-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8de74-112">Requirements</span></span>  
 <span data-ttu-id="8de74-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8de74-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de74-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8de74-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8de74-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8de74-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8de74-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de74-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de74-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8de74-117">See also</span></span>

- [<span data-ttu-id="8de74-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8de74-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8de74-119">RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="8de74-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="8de74-120">RuntimeSuspendFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="8de74-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
