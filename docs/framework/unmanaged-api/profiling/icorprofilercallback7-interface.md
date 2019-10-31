---
title: ICorProfilerCallback7 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: f8c2fb544cf9fd6642bd0581211e0e4e49633221
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139770"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="2b958-102">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b958-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="2b958-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="2b958-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="2b958-104">Podtřída [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) , která poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že je aktualizovaný datový proud symbolů přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="2b958-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b958-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2b958-105">Methods</span></span>  
  
|<span data-ttu-id="2b958-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2b958-106">Method</span></span>|<span data-ttu-id="2b958-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2b958-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b958-108">ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="2b958-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="2b958-109">Upozorní profileru, že je aktualizován datový proud symbolů přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="2b958-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b958-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b958-110">Requirements</span></span>  
 <span data-ttu-id="2b958-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b958-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b958-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2b958-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b958-113">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b958-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b958-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b958-114">See also</span></span>

- [<span data-ttu-id="2b958-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2b958-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
