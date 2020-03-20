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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175093"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="01efa-102">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01efa-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="01efa-103">[Podporováno v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="01efa-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="01efa-104">Podtřída [ICorProfilerCallback7,](icorprofilercallback7-interface.md) která poskytuje metody zpětného volání používané běžným jazykem runtime upozornit profiler, že kompilace JIT dynamické metody byla spuštěna a dokončena.</span><span class="sxs-lookup"><span data-stu-id="01efa-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="01efa-105">Metody</span><span class="sxs-lookup"><span data-stu-id="01efa-105">Methods</span></span>  
  
|<span data-ttu-id="01efa-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="01efa-106">Method</span></span>|<span data-ttu-id="01efa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="01efa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01efa-108">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="01efa-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="01efa-109">Upozorní profiler, že byla spuštěna kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="01efa-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="01efa-110">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="01efa-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="01efa-111">Upozorní profiler, že byla dokončena kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="01efa-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01efa-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01efa-112">Requirements</span></span>  
 <span data-ttu-id="01efa-113">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01efa-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01efa-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01efa-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="01efa-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="01efa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="01efa-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="01efa-116">See also</span></span>

- [<span data-ttu-id="01efa-117">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="01efa-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="01efa-118">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01efa-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
