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
ms.openlocfilehash: a6c480af921fb0259ef85beec8d8f65bdd430522
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689305"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="d4121-102">ICorProfilerCallback9 Interface</span><span class="sxs-lookup"><span data-stu-id="d4121-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="d4121-103">[Podporované v rozhraní .NET Framework 4.7.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="d4121-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="d4121-104">Podtřída [icorprofilercallback8 –](icorprofilercallback8-interface.md) , která poskytuje metodu zpětného volání používané modul common language runtime pro oznámení profileru, že dynamickou metodu byla uvolňování paměti shromažďují a následně byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="d4121-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4121-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d4121-105">Methods</span></span>  
  
|<span data-ttu-id="d4121-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d4121-106">Method</span></span>|<span data-ttu-id="d4121-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d4121-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4121-108">DynamicMethodUnloaded – metoda</span><span class="sxs-lookup"><span data-stu-id="d4121-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="d4121-109">Oznámí profileru, že dynamickou metodu byla uvolňování paměti shromažďují a následně byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="d4121-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4121-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4121-110">Requirements</span></span>  
 <span data-ttu-id="d4121-111">**Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4121-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4121-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4121-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="d4121-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d4121-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d4121-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4121-114">See also</span></span>
- [<span data-ttu-id="d4121-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d4121-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d4121-116">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4121-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="d4121-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="d4121-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="d4121-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="d4121-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
