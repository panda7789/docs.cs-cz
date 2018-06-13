---
title: Rozhraní ICorProfilerCallback6
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05e571149a794cbffa9e602255455d779a83e2a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452953"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="37ea6-102">Rozhraní ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="37ea6-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="37ea6-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="37ea6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="37ea6-104">Podtřídou třídy [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) , který poskytuje metody zpětného volání, která používá modul common language runtime oznámit profileru, který načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="37ea6-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37ea6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="37ea6-105">Methods</span></span>  
  
|<span data-ttu-id="37ea6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="37ea6-106">Method</span></span>|<span data-ttu-id="37ea6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="37ea6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37ea6-108">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="37ea6-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="37ea6-109">Upozorní profileru, že sestavení v velmi brzy načítá fáze, když modul common language runtime provede procházení uzavření odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="37ea6-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ea6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37ea6-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ea6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37ea6-111">Requirements</span></span>  
 <span data-ttu-id="37ea6-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ea6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ea6-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="37ea6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="37ea6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37ea6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ea6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="37ea6-115">See Also</span></span>  
 [<span data-ttu-id="37ea6-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="37ea6-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
