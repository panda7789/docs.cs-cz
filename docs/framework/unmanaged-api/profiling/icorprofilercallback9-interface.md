---
title: ICorProfilerCallback9 – rozhraní
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136566"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="7fa6f-102">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fa6f-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="7fa6f-103">[Podporováno v .NET Framework 4.7.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="7fa6f-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="7fa6f-104">Podtřída [ICorProfilerCallback8](icorprofilercallback8-interface.md) , která poskytuje metodu zpětného volání, kterou používá modul CLR (Common Language Runtime) k upozornění profileru, že dynamická metoda byla uvolněna z paměti a následně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="7fa6f-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fa6f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7fa6f-105">Methods</span></span>  
  
|<span data-ttu-id="7fa6f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7fa6f-106">Method</span></span>|<span data-ttu-id="7fa6f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7fa6f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fa6f-108">DynamicMethodUnloaded – metoda</span><span class="sxs-lookup"><span data-stu-id="7fa6f-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="7fa6f-109">Upozorní profileru, že dynamická metoda byla uvolněna z paměti a následně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="7fa6f-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fa6f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fa6f-110">Requirements</span></span>  
 <span data-ttu-id="7fa6f-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fa6f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fa6f-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7fa6f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="7fa6f-113">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7fa6f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7fa6f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fa6f-114">See also</span></span>

- [<span data-ttu-id="7fa6f-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7fa6f-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7fa6f-116">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fa6f-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="7fa6f-117">ICorProfilerCallback8. DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="7fa6f-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="7fa6f-118">ICorProfilerCallback8. DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="7fa6f-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
