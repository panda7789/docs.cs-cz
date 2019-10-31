---
title: ICorProfilerCallback8 – rozhraní
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136454"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="aa8c6-102">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa8c6-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="aa8c6-103">[Podporováno v .NET Framework 4,7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="aa8c6-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="aa8c6-104">Podtřída [ICorProfilerCallback7](icorprofilercallback7-interface.md) , která poskytuje metody zpětného volání používané modulem CLR (Common Language Runtime) k informování profileru o zahájení a dokončení kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="aa8c6-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="aa8c6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aa8c6-105">Methods</span></span>  
  
|<span data-ttu-id="aa8c6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="aa8c6-106">Method</span></span>|<span data-ttu-id="aa8c6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aa8c6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa8c6-108">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="aa8c6-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="aa8c6-109">Upozorní profileru, že byla spuštěna kompilace JIT pro dynamickou metodu.</span><span class="sxs-lookup"><span data-stu-id="aa8c6-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="aa8c6-110">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="aa8c6-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="aa8c6-111">Upozorní profileru, že byla dokončena kompilace dynamické metody JIT.</span><span class="sxs-lookup"><span data-stu-id="aa8c6-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa8c6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa8c6-112">Requirements</span></span>  
 <span data-ttu-id="aa8c6-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa8c6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa8c6-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="aa8c6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="aa8c6-115">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aa8c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="aa8c6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa8c6-116">See also</span></span>

- [<span data-ttu-id="aa8c6-117">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="aa8c6-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="aa8c6-118">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa8c6-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
