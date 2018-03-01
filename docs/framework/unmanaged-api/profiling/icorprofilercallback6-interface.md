---
title: "Rozhraní ICorProfilerCallback6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 733ca2f03e73852f2fef1e42fb9ec961ade2975d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="ba0af-102">Rozhraní ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="ba0af-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="ba0af-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ba0af-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ba0af-104">Podtřídou třídy [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) , který poskytuje metody zpětného volání, která používá modul common language runtime oznámit profileru, který načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba0af-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba0af-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ba0af-105">Methods</span></span>  
  
|<span data-ttu-id="ba0af-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ba0af-106">Method</span></span>|<span data-ttu-id="ba0af-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ba0af-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba0af-108">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="ba0af-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="ba0af-109">Upozorní profileru, že sestavení v velmi brzy načítá fáze, když modul common language runtime provede procházení uzavření odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba0af-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba0af-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba0af-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba0af-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba0af-111">Requirements</span></span>  
 <span data-ttu-id="ba0af-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba0af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba0af-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba0af-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba0af-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba0af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba0af-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba0af-115">See Also</span></span>  
 [<span data-ttu-id="ba0af-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ba0af-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
