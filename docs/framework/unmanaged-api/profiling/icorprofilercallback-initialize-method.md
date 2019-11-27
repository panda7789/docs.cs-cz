---
title: ICorProfilerCallback::Initialize – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: 64df6a81eb23c20537238c702fd0c204d64d14bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434552"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="07e51-102">ICorProfilerCallback::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="07e51-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="07e51-103">Volá se, aby se inicializoval Profiler kódu, když se spustí nová aplikace Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="07e51-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07e51-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07e51-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="07e51-106">[v](/cpp/atl/iunknown) rozhraní, které musí Profiler zadat dotaz na ukazatel rozhraní [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="07e51-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e51-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07e51-107">Remarks</span></span>  
 <span data-ttu-id="07e51-108">`Initialize` volání je jediná možnost Povolit (nebo zakázat) zpětná volání, která jsou neměnná.</span><span class="sxs-lookup"><span data-stu-id="07e51-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="07e51-109">Jakmile je zpětné volání povoleno voláním `Initialize`, nelze jej později zakázat pomocí [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="07e51-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="07e51-110">Hodnota COR_PRF_MONITOR_IMMUTABLE výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) označuje, které události jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="07e51-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e51-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07e51-111">Requirements</span></span>  
 <span data-ttu-id="07e51-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07e51-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e51-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="07e51-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07e51-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="07e51-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07e51-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e51-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e51-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07e51-116">See also</span></span>

- [<span data-ttu-id="07e51-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07e51-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="07e51-118">Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="07e51-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
