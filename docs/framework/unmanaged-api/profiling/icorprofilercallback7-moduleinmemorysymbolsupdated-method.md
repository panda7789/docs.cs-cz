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
ms.openlocfilehash: 6fbb86fc63a26599ae83c81817dbcb9abfb88cc8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864685"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="3245d-102">ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated – metoda</span><span class="sxs-lookup"><span data-stu-id="3245d-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="3245d-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="3245d-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3245d-104">Upozorní profiler vždy, když je aktualizován datový proud symbolu přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="3245d-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3245d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3245d-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3245d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3245d-106">Parameters</span></span>  
 <span data-ttu-id="3245d-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="3245d-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="3245d-108">Identifikátor modulu v paměti, jehož datový proud symbolů je aktualizovaný.</span><span class="sxs-lookup"><span data-stu-id="3245d-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3245d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3245d-109">Remarks</span></span>  
 <span data-ttu-id="3245d-110">Toto zpětné volání je řízeno nastavením příznaku masky události [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) při volání metody [Icorprofilercallback5 –:: SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3245d-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3245d-111">Tato událost není aktuálně vyvolána pro symboly implicitně vytvořené nebo upravené prostřednictvím rozhraní API <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="3245d-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="3245d-112">I když se symboly zadávají před voláním jednoho z přetížení spravovaných <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metod, které obsahují `rawSymbolStore` argument pro určení symbolů pro sestavení, modul runtime nemusí ve skutečnosti přidružit symbolické údaje k modulu, dokud nedošlo ke zpětnému volání [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3245d-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="3245d-113">Tato událost poskytuje později možnost shromažďovat symboly pro tyto moduly.</span><span class="sxs-lookup"><span data-stu-id="3245d-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3245d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3245d-114">Requirements</span></span>  
 <span data-ttu-id="3245d-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3245d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3245d-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3245d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3245d-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3245d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3245d-118">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3245d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3245d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3245d-119">See also</span></span>

- [<span data-ttu-id="3245d-120">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="3245d-120">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="3245d-121">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="3245d-121">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="3245d-122">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3245d-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
