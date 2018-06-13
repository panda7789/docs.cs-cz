---
title: ICorProfilerCallback8 rozhraní
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
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455280"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="1272b-102">ICorProfilerCallback8 rozhraní</span><span class="sxs-lookup"><span data-stu-id="1272b-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="1272b-103">[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="1272b-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="1272b-104">Podtřídou třídy [ICorProfilerCallback7](icorprofilercallback7-interface.md) , který poskytuje metody zpětného volání používané modul common language runtime oznámit profileru, který má JIT – kompilace dynamické metody spuštění a dokončení.</span><span class="sxs-lookup"><span data-stu-id="1272b-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="1272b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1272b-105">Methods</span></span>  
  
|<span data-ttu-id="1272b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1272b-106">Method</span></span>|<span data-ttu-id="1272b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1272b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1272b-108">DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="1272b-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="1272b-109">Aby bylo zahájeno JIT – kompilace dynamické metody upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="1272b-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="1272b-110">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="1272b-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="1272b-111">Upozorní profileru, že byla dokončena JIT – kompilace dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="1272b-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1272b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1272b-112">Requirements</span></span>  
 <span data-ttu-id="1272b-113">**Platformy:** najdete v části [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1272b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1272b-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1272b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="1272b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1272b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1272b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1272b-116">See Also</span></span>  
<span data-ttu-id="1272b-117">[Rozhraní pro profilaci](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="1272b-117">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
[<span data-ttu-id="1272b-118">ICorProfilerCallback9 rozhraní</span><span class="sxs-lookup"><span data-stu-id="1272b-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
