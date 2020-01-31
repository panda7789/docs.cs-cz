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
ms.openlocfilehash: e4a003b30c495852a3a68d44d92bef35c3ed7812
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866292"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="b4d49-102">ICorProfilerCallback::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="b4d49-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="b4d49-103">Volá se, aby se inicializoval Profiler kódu, když se spustí nová aplikace Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b4d49-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4d49-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4d49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4d49-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="b4d49-106">\[in] ukazatel na rozhraní [IUnknown](/cpp/atl/iunknown) , které musí Profiler dotazovat na ukazatel rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b4d49-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="b4d49-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4d49-107">Remarks</span></span>  
 <span data-ttu-id="b4d49-108">`Initialize` volání je jediná možnost Povolit (nebo zakázat) zpětná volání, která jsou neměnná.</span><span class="sxs-lookup"><span data-stu-id="b4d49-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="b4d49-109">Jakmile je zpětné volání povoleno voláním `Initialize`, nelze jej později zakázat pomocí [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="b4d49-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="b4d49-110">Hodnota COR_PRF_MONITOR_IMMUTABLE výčtu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) označuje, které události jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="b4d49-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d49-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4d49-111">Requirements</span></span>  
 <span data-ttu-id="b4d49-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d49-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d49-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b4d49-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4d49-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4d49-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d49-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d49-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d49-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4d49-116">See also</span></span>

- [<span data-ttu-id="b4d49-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4d49-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b4d49-118">Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="b4d49-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
