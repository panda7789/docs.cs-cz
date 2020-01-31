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
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865880"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="da504-102">ICorProfilerCallback::RuntimeSuspendStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="da504-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="da504-103">Upozorní profileru, že modul runtime chystá pozastavit všechny běhové vlákna.</span><span class="sxs-lookup"><span data-stu-id="da504-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da504-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da504-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da504-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da504-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="da504-106">pro Hodnota výčtu [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) , která označuje důvod pro pozastavení.</span><span class="sxs-lookup"><span data-stu-id="da504-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da504-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da504-107">Remarks</span></span>  
 <span data-ttu-id="da504-108">Všechna vlákna modulu runtime, která jsou v nespravovaném kódu, mohou pokračovat v běhu, dokud se nepokusí znovu zadat modul runtime.</span><span class="sxs-lookup"><span data-stu-id="da504-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="da504-109">V tomto okamžiku se také pozastaví, dokud modul runtime nebude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="da504-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="da504-110">To platí také pro nová vlákna, která vstupují do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="da504-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="da504-111">Všechna vlákna v modulu runtime jsou buď okamžitě pozastavena, pokud jsou již v kódu přerušitelné, nebo jsou požádány o pozastavení, když dosáhnou přerušitelné kódu.</span><span class="sxs-lookup"><span data-stu-id="da504-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da504-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da504-112">Requirements</span></span>  
 <span data-ttu-id="da504-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da504-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da504-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="da504-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da504-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="da504-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da504-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da504-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da504-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da504-117">See also</span></span>

- [<span data-ttu-id="da504-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da504-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="da504-119">RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="da504-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="da504-120">RuntimeSuspendFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="da504-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
