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
ms.openlocfilehash: 8fda98c20b42355b9f52595929bbf5b980b5b857
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077235"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="3f5cd-102">Rozhraní ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="3f5cd-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="3f5cd-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="3f5cd-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3f5cd-104">Podtřída [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) , která poskytuje metodu zpětného volání, která používá modul common language runtime oznámit profiler, který se načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f5cd-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f5cd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3f5cd-105">Methods</span></span>  
  
|<span data-ttu-id="3f5cd-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f5cd-106">Method</span></span>|<span data-ttu-id="3f5cd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f5cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f5cd-108">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="3f5cd-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="3f5cd-109">Oznámí profileru, že sestavení ve velmi brzy načítá fáze, když modul CLR provede procházení uzavření odkaz sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f5cd-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f5cd-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f5cd-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f5cd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f5cd-111">Requirements</span></span>  
 <span data-ttu-id="3f5cd-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f5cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f5cd-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f5cd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f5cd-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f5cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5cd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f5cd-115">See also</span></span>

- [<span data-ttu-id="3f5cd-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3f5cd-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
