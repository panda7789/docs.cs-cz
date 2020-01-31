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
ms.openlocfilehash: 90071121411b706052e1cbb4cb647536dae2835a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864866"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="23f1f-102">Rozhraní ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="23f1f-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="23f1f-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="23f1f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="23f1f-104">Podtřída [ICorProfilerCallback5 –](icorprofilercallback5-interface.md) , která poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že se načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="23f1f-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23f1f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="23f1f-105">Methods</span></span>  
  
|<span data-ttu-id="23f1f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="23f1f-106">Method</span></span>|<span data-ttu-id="23f1f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="23f1f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23f1f-108">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="23f1f-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="23f1f-109">Upozorní profileru, že sestavení je ve fázi brzkého nasazování, pokud modul CLR provádí procházení zavřením odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="23f1f-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23f1f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23f1f-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f1f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23f1f-111">Requirements</span></span>  
 <span data-ttu-id="23f1f-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23f1f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f1f-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="23f1f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23f1f-114">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f1f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f1f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23f1f-115">See also</span></span>

- [<span data-ttu-id="23f1f-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="23f1f-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
