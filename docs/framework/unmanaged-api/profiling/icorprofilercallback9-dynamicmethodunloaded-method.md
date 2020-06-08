---
title: ICorProfilerCallback9::D ynamicMethodUnloaded – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2391ad854b17ec117940a3d3568c40d6cf7f4725
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498970"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="a6a5f-102">ICorProfilerCallback9::D ynamicMethodUnloaded – metoda</span><span class="sxs-lookup"><span data-stu-id="a6a5f-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="a6a5f-103">[Podporováno v .NET Framework 4.7.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="a6a5f-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="a6a5f-104">Upozorní profiler vždy, když je dynamická metoda uvolněna z paměti a následně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="a6a5f-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a5f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6a5f-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6a5f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6a5f-106">Parameters</span></span>  
<span data-ttu-id="a6a5f-107">pro`functionId`</span><span class="sxs-lookup"><span data-stu-id="a6a5f-107">[in] `functionId`</span></span>  
<span data-ttu-id="a6a5f-108">Identifikátor funkce v paměti, která byla uvolněna z paměti a uvolněna.</span><span class="sxs-lookup"><span data-stu-id="a6a5f-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6a5f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6a5f-109">Requirements</span></span>  
 <span data-ttu-id="a6a5f-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6a5f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a5f-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a6a5f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6a5f-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a6a5f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6a5f-113">**Verze .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a5f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a5f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6a5f-114">See also</span></span>

- [<span data-ttu-id="a6a5f-115">ICorProfilerCallback8. DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="a6a5f-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="a6a5f-116">ICorProfilerCallback8. DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="a6a5f-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="a6a5f-117">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6a5f-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="a6a5f-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="a6a5f-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
