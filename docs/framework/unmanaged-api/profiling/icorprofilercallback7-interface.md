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
ms.openlocfilehash: 3c49a5f782ea105ce57b5fbc2c6bd9bd89f708d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629578"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="5f44e-102">ICorProfilerCallback7 Interface</span><span class="sxs-lookup"><span data-stu-id="5f44e-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="5f44e-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="5f44e-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="5f44e-104">Podtřída [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) , která poskytuje metodu zpětného volání, která používá modul common language runtime pro oznámení profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="5f44e-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f44e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5f44e-105">Methods</span></span>  
  
|<span data-ttu-id="5f44e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f44e-106">Method</span></span>|<span data-ttu-id="5f44e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5f44e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f44e-108">ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="5f44e-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="5f44e-109">Oznámí profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="5f44e-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f44e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f44e-110">Requirements</span></span>  
 <span data-ttu-id="5f44e-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f44e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f44e-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f44e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f44e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f44e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f44e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f44e-114">See also</span></span>
- [<span data-ttu-id="5f44e-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5f44e-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
