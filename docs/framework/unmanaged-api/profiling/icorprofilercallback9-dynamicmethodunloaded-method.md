---
title: ICorProfilerCallback9::DynamicMethodUnloaded Metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177030"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="7b749-102">ICorProfilerCallback9::DynamicMethodUnloaded Metoda</span><span class="sxs-lookup"><span data-stu-id="7b749-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="7b749-103">[Podporováno v rozhraní .NET Framework 4.7.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="7b749-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="7b749-104">Upozorní profiler vždy, když dynamická metoda je uvolněna a následně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="7b749-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b749-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b749-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b749-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b749-106">Parameters</span></span>  
<span data-ttu-id="7b749-107">[v]`functionId`</span><span class="sxs-lookup"><span data-stu-id="7b749-107">[in] `functionId`</span></span>  
<span data-ttu-id="7b749-108">Identifikátor funkce v paměti, která byla uvolněna a uvolněna.</span><span class="sxs-lookup"><span data-stu-id="7b749-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b749-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b749-109">Requirements</span></span>  
 <span data-ttu-id="7b749-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b749-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b749-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b749-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b749-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b749-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b749-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7b749-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b749-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b749-114">See also</span></span>

- [<span data-ttu-id="7b749-115">Metoda ICorProfilerCallback8.DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="7b749-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="7b749-116">Metoda ICorProfilerCallback8.DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="7b749-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="7b749-117">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b749-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="7b749-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="7b749-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
