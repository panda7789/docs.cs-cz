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
ms.openlocfilehash: 9a49d8e1ff31942c6564ab560d6726b9ede26466
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499139"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="f6fa0-102">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6fa0-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="f6fa0-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="f6fa0-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="f6fa0-104">Podtřída [ICorProfilerCallback6](icorprofilercallback6-interface.md) , která poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že je aktualizovaný datový proud symbolů přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="f6fa0-104">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6fa0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f6fa0-105">Methods</span></span>  
  
|<span data-ttu-id="f6fa0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f6fa0-106">Method</span></span>|<span data-ttu-id="f6fa0-107">Description</span><span class="sxs-lookup"><span data-stu-id="f6fa0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6fa0-108">ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="f6fa0-108">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="f6fa0-109">Upozorní profileru, že je aktualizován datový proud symbolů přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="f6fa0-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6fa0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6fa0-110">Requirements</span></span>  
 <span data-ttu-id="f6fa0-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6fa0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6fa0-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f6fa0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6fa0-113">**Verze .NET Framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6fa0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fa0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6fa0-114">See also</span></span>

- [<span data-ttu-id="f6fa0-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f6fa0-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
