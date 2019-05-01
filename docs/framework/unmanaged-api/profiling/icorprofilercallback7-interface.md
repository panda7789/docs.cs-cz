---
title: ICorProfilerCallback7 Interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81477010b22edee71098edfc1b8557db08b6038f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049697"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="66611-102">ICorProfilerCallback7 Interface</span><span class="sxs-lookup"><span data-stu-id="66611-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="66611-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="66611-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="66611-104">Podtřída [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) , která poskytuje metodu zpětného volání, která používá modul common language runtime pro oznámení profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="66611-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66611-105">Metody</span><span class="sxs-lookup"><span data-stu-id="66611-105">Methods</span></span>  
  
|<span data-ttu-id="66611-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="66611-106">Method</span></span>|<span data-ttu-id="66611-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66611-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66611-108">ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="66611-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="66611-109">Oznámí profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="66611-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66611-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66611-110">Requirements</span></span>  
 <span data-ttu-id="66611-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66611-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66611-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66611-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66611-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66611-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66611-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66611-114">See also</span></span>

- [<span data-ttu-id="66611-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="66611-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
