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
ms.openlocfilehash: 05a788179ff40a6889ed613b5f8659dd3f8e066f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196320"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="698a5-102">ICorProfilerCallback9::D ynamicMethodUnloaded – metoda</span><span class="sxs-lookup"><span data-stu-id="698a5-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="698a5-103">[Podporováno v .NET Framework 4.7.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="698a5-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="698a5-104">Upozorní profiler vždy, když je dynamická metoda uvolněna z paměti a následně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="698a5-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="698a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="698a5-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="698a5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="698a5-106">Parameters</span></span>  
<span data-ttu-id="698a5-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="698a5-107">[in] `functionId`</span></span>  
<span data-ttu-id="698a5-108">Identifikátor funkce v paměti, která byla uvolněna z paměti a uvolněna.</span><span class="sxs-lookup"><span data-stu-id="698a5-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="698a5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="698a5-109">Requirements</span></span>  
 <span data-ttu-id="698a5-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="698a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="698a5-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="698a5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="698a5-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="698a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="698a5-113">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="698a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698a5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="698a5-114">See also</span></span>

- [<span data-ttu-id="698a5-115">ICorProfilerCallback8. DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="698a5-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="698a5-116">ICorProfilerCallback8. DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="698a5-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="698a5-117">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="698a5-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="698a5-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="698a5-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
