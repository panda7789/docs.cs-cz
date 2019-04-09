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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125564"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="74efb-102">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74efb-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="74efb-103">[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="74efb-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="74efb-104">Podtřída [icorprofilercallback7 –](icorprofilercallback7-interface.md) , který poskytuje metody zpětného volání používané modulem common language runtime pro oznámení profileru, který je spuštěn a dokončení kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="74efb-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="74efb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="74efb-105">Methods</span></span>  
  
|<span data-ttu-id="74efb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="74efb-106">Method</span></span>|<span data-ttu-id="74efb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="74efb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74efb-108">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="74efb-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="74efb-109">Oznámí profileru, byla spuštěna kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="74efb-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="74efb-110">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="74efb-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="74efb-111">Upozornění profileru dokončení kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="74efb-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74efb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74efb-112">Requirements</span></span>  
 <span data-ttu-id="74efb-113">**Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74efb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74efb-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74efb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
**<span data-ttu-id="74efb-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="74efb-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="74efb-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74efb-116">See also</span></span>

- [<span data-ttu-id="74efb-117">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="74efb-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="74efb-118">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74efb-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
