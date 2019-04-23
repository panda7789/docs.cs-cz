---
title: ICorProfilerCallback9::DynamicMethodUnloaded Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96cdfb79c1573648173305d6ee789aa8db030ff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211007"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="c8054-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span><span class="sxs-lookup"><span data-stu-id="c8054-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="c8054-103">[Podporované v rozhraní .NET Framework 4.7.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="c8054-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="c8054-104">Profiler upozorní pokaždé, když je dynamická metoda uvolňování paměti shromažďují a následně byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="c8054-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8054-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8054-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8054-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8054-106">Parameters</span></span>  
<span data-ttu-id="c8054-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="c8054-107">[in] `functionId`</span></span>  
<span data-ttu-id="c8054-108">Identifikátor funkce v paměti, která se shromažďují a uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c8054-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="c8054-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8054-109">Requirements</span></span>  
 <span data-ttu-id="c8054-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8054-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8054-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c8054-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8054-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8054-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8054-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c8054-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8054-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8054-114">See also</span></span>

- [<span data-ttu-id="c8054-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c8054-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="c8054-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c8054-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="c8054-117">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8054-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="c8054-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="c8054-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
