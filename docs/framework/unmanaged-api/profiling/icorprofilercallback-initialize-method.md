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
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500101"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="6fb6e-102">ICorProfilerCallback::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="6fb6e-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="6fb6e-103">Volá se, aby se inicializoval Profiler kódu, když se spustí nová aplikace Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6fb6e-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fb6e-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fb6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fb6e-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="6fb6e-106">\[v] ukazatel na rozhraní [IUnknown](/cpp/atl/iunknown) , které musí Profiler zadat dotaz na ukazatel rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6fb6e-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="6fb6e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fb6e-107">Remarks</span></span>  
 <span data-ttu-id="6fb6e-108">`Initialize`Volání je jediná možnost Povolit (nebo zakázat) zpětná volání, která jsou neměnná.</span><span class="sxs-lookup"><span data-stu-id="6fb6e-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="6fb6e-109">Jakmile je zpětné volání povoleno `Initialize` voláním, nelze jej zakázat později pomocí [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="6fb6e-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="6fb6e-110">Hodnota COR_PRF_MONITOR_IMMUTABLE výčtu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) označuje, které události jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="6fb6e-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb6e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fb6e-111">Requirements</span></span>  
 <span data-ttu-id="6fb6e-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb6e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb6e-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6fb6e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6fb6e-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6fb6e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fb6e-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb6e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb6e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fb6e-116">See also</span></span>

- [<span data-ttu-id="6fb6e-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fb6e-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6fb6e-118">Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="6fb6e-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
