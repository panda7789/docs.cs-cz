---
title: ICorProfilerCallback9 Interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227753"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="242bf-102">ICorProfilerCallback9 Interface</span><span class="sxs-lookup"><span data-stu-id="242bf-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="242bf-103">[Podporované v rozhraní .NET Framework 4.7.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="242bf-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="242bf-104">Podtřída [icorprofilercallback8 –](icorprofilercallback8-interface.md) , která poskytuje metodu zpětného volání používané modul common language runtime pro oznámení profileru, že dynamickou metodu byla uvolňování paměti shromažďují a následně byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="242bf-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="242bf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="242bf-105">Methods</span></span>  
  
|<span data-ttu-id="242bf-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="242bf-106">Method</span></span>|<span data-ttu-id="242bf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="242bf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="242bf-108">DynamicMethodUnloaded – metoda</span><span class="sxs-lookup"><span data-stu-id="242bf-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="242bf-109">Oznámí profileru, že dynamickou metodu byla uvolňování paměti shromažďují a následně byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="242bf-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="242bf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="242bf-110">Requirements</span></span>  
 <span data-ttu-id="242bf-111">**Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="242bf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="242bf-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="242bf-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="242bf-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="242bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="242bf-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="242bf-114">See also</span></span>

- [<span data-ttu-id="242bf-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="242bf-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="242bf-116">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="242bf-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="242bf-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="242bf-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="242bf-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="242bf-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
