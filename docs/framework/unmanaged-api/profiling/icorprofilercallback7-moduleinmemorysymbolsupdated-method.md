---
title: 'ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated – metoda'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916202"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="c115f-102">ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="c115f-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="c115f-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="c115f-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="c115f-104">Upozorní profiler vždy, když je aktualizován datový proud symbolu přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="c115f-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c115f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c115f-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c115f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c115f-106">Parameters</span></span>  
 <span data-ttu-id="c115f-107">pro`moduleId`</span><span class="sxs-lookup"><span data-stu-id="c115f-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="c115f-108">Identifikátor modulu v paměti, jehož datový proud symbolů je aktualizovaný.</span><span class="sxs-lookup"><span data-stu-id="c115f-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c115f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c115f-109">Remarks</span></span>  
 <span data-ttu-id="c115f-110">Toto zpětné volání je řízeno nastavením příznaku masky události [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) při volání metody [Icorprofilercallback5 –:: SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c115f-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c115f-111">Tato událost není aktuálně vyvolána pro symboly implicitně vytvořené nebo upravené prostřednictvím <xref:System.Reflection.Emit> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c115f-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="c115f-112">I když se symboly zadávají před voláním jednoho z přetížení spravovaných <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metod, které `rawSymbolStore` obsahují argument pro určení symbolů pro sestavení, modul runtime nemusí ve skutečnosti přidružit symbolické údaje k modulu. až do chvíle, kdy došlo k [ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětnému volání.</span><span class="sxs-lookup"><span data-stu-id="c115f-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="c115f-113">Tato událost poskytuje později možnost shromažďovat symboly pro tyto moduly.</span><span class="sxs-lookup"><span data-stu-id="c115f-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c115f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c115f-114">Requirements</span></span>  
 <span data-ttu-id="c115f-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c115f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c115f-116">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c115f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c115f-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c115f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c115f-118">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c115f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c115f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c115f-119">See also</span></span>

- [<span data-ttu-id="c115f-120">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c115f-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="c115f-121">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c115f-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="c115f-122">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c115f-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
