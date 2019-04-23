---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method
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
ms.openlocfilehash: 12414064bf0651eab443951bde2a50dcff7b2291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226956"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="3402d-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span><span class="sxs-lookup"><span data-stu-id="3402d-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="3402d-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="3402d-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3402d-104">Profiler upozorní, jakmile dojde k aktualizaci symbolu proud přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="3402d-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3402d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3402d-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3402d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3402d-106">Parameters</span></span>  
 <span data-ttu-id="3402d-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="3402d-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="3402d-108">Identifikátor modulu v paměti aktualizaci jehož symbol streamu.</span><span class="sxs-lookup"><span data-stu-id="3402d-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3402d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3402d-109">Remarks</span></span>  
 <span data-ttu-id="3402d-110">Toto zpětné volání je řízena nastavením [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) příznak masky události při volání [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3402d-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3402d-111">Tato událost není aktuálně aktivována pro symboly implicitně vytvoření nebo úpravě prostřednictvím <xref:System.Reflection.Emit> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3402d-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="3402d-112">I když symboly jsou k dispozici před jeho zahájením ve volání do jednoho z přetížení spravovanou <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metody, které zahrnuje `rawSymbolStore` argumentu, abyste zadávali symboly pro sestavení, modul runtime nemůže ve skutečnosti přidružení symbolické dat s modulem až po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="3402d-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="3402d-113">Tato událost poskytuje vyšší moci shromažďovat symboly pro tyto moduly.</span><span class="sxs-lookup"><span data-stu-id="3402d-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3402d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3402d-114">Requirements</span></span>  
 <span data-ttu-id="3402d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3402d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3402d-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3402d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3402d-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3402d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3402d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3402d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3402d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3402d-119">See also</span></span>

- [<span data-ttu-id="3402d-120">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="3402d-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="3402d-121">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="3402d-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="3402d-122">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3402d-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
