---
title: ICorProfilerCallback7 rozhraní
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
ms.openlocfilehash: f681001b610f42fef28181ffe3b47d702aabdf6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452688"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="8781a-102">ICorProfilerCallback7 rozhraní</span><span class="sxs-lookup"><span data-stu-id="8781a-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="8781a-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="8781a-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="8781a-104">Podtřídou třídy [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) , který poskytuje metody zpětného volání, která používá modul common language runtime profileru oznámit, že se aktualizuje symbol datový proud přidružený modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="8781a-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8781a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8781a-105">Methods</span></span>  
  
|<span data-ttu-id="8781a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8781a-106">Method</span></span>|<span data-ttu-id="8781a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8781a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8781a-108">ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="8781a-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="8781a-109">Upozorní profileru, že se aktualizuje symbol datový proud přidružený modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="8781a-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8781a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8781a-110">Requirements</span></span>  
 <span data-ttu-id="8781a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8781a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8781a-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8781a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8781a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8781a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8781a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8781a-114">See Also</span></span>  
 [<span data-ttu-id="8781a-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8781a-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
