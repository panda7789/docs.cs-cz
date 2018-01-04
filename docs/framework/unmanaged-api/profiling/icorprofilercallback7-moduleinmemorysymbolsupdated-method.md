---
title: "ICorProfilerCallback7::ModuleInMemorySymbolsUpdated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfiler7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 898adf043e425c00d6e311e2f67c53ed65cacb33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="74b5a-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="74b5a-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="74b5a-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="74b5a-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="74b5a-104">Upozorní profileru při každé aktualizaci symbol datový proud přidružený modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="74b5a-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b5a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74b5a-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74b5a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="74b5a-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="74b5a-107">Identifikátor v paměti modulu, jehož symbol datového proudu se aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="74b5a-107">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74b5a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74b5a-108">Remarks</span></span>  
 <span data-ttu-id="74b5a-109">Tato zpětné volání je řízena nastavením [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) příznak maska událostí při volání metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="74b5a-109">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74b5a-110">Tato událost není aktuálně aktivována pro symboly implicitně vytvoření nebo úpravě prostřednictvím <xref:System.Reflection.Emit> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="74b5a-110">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="74b5a-111">I když symboly jsou součástí předem volání do jednoho z přetížení spravovaný <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metody, které zahrnuje `rawSymbolStore` argument, abyste zadávali symboly pro sestavení, modul runtime nemusí ve skutečnosti přidružení symbolický dat s modulem dokud po [moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="74b5a-111">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="74b5a-112">Tato událost poskytuje novější příležitostí ke shromažďování symboly pro tyto moduly.</span><span class="sxs-lookup"><span data-stu-id="74b5a-112">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74b5a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74b5a-113">Requirements</span></span>  
 <span data-ttu-id="74b5a-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74b5a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b5a-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74b5a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74b5a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74b5a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74b5a-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b5a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b5a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="74b5a-118">See Also</span></span>  
 [<span data-ttu-id="74b5a-119">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="74b5a-119">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="74b5a-120">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="74b5a-120">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="74b5a-121">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74b5a-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
