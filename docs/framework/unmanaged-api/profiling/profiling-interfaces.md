---
title: Rozhraní pro profilaci
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059fadc5607e76b871083682136fda542ae9bacf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462049"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="d5491-102">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5491-102">Profiling Interfaces</span></span>
<span data-ttu-id="d5491-103">Tato část popisuje nespravovaná rozhraní, které vám umožní profilu program, který je vykonáván common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d5491-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5491-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d5491-104">In This Section</span></span>  
 [<span data-ttu-id="d5491-105">ICLRProfiling – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="d5491-106">Poskytuje [attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda, která umožňuje profileru pro připojení k spuštěných procesů.</span><span class="sxs-lookup"><span data-stu-id="d5491-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="d5491-107">ICorProfilerAssemblyReferenceProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="d5491-108">Umožňuje profileru k informování CLR odkazů na sestavení, které profileru přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d5491-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="d5491-109">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="d5491-110">Poskytuje metody, které jsou používány modulu CLR profileru kód upozornit, když dojde k události, ke kterým se připojila profileru.</span><span class="sxs-lookup"><span data-stu-id="d5491-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="d5491-111">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="d5491-112">Rozšiřuje `ICorProfilerCallback` rozhraní s zpětná volání, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="d5491-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="d5491-113">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="d5491-114">Poskytuje metody zpětného volání, které modul CLR používá ke komunikaci připojení a odpojení informace o stavu do profileru.</span><span class="sxs-lookup"><span data-stu-id="d5491-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="d5491-115">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="d5491-116">Poskytuje metody zpětného volání, které modul CLR používá ke sdělování informací profileru.</span><span class="sxs-lookup"><span data-stu-id="d5491-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="d5491-117">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="d5491-118">Poskytne metodu, která identifikuje přechodné uzavření objekty odkazuje kořeny kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="d5491-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="d5491-119">ICorProfilerCallback6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="d5491-120">Poskytuje metody zpětného volání, která používá modulu CLR oznámit profileru, který načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5491-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="d5491-121">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="d5491-122">Poskytuje metody zpětného volání, která používá modul common language runtime profileru oznámit, že se aktualizuje symbol datový proud přidružený modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="d5491-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="d5491-123">ICorProfilerCallback8 rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-123">ICorProfilerCallback8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
<span data-ttu-id="d5491-124">Poskytuje metody zpětného volání, které používá modul common language runtime oznámit profileru, který má JIT – kompilace dynamické metody spuštění a dokončení.</span><span class="sxs-lookup"><span data-stu-id="d5491-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="d5491-125">ICorProfilerCallback9 rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-125">ICorProfilerCallback9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
<span data-ttu-id="d5491-126">Poskytuje metody zpětného volání, která používá modul common language runtime oznámit profileru, který je dynamická metoda shromážděných a následně uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d5491-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="d5491-127">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-127">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="d5491-128">Poskytuje metody, které umožňují kódu profileru ke komunikaci s CLR řídit, jak by měla JIT kompilátoru generování kódu při nutnosti rekompilace konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="d5491-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="d5491-129">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-129">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="d5491-130">Poskytuje metody pro postupně iteraci přes kolekci funkcí v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d5491-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="d5491-131">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-131">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="d5491-132">Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení sledování událostí a vyžádání informací.</span><span class="sxs-lookup"><span data-stu-id="d5491-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="d5491-133">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-133">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="d5491-134">Rozšiřuje `ICorProfilerInfo` rozhraní s metod podporovaných v rozhraní .NET Framework 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="d5491-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="d5491-135">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-135">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="d5491-136">Rozšiřuje `ICorProfilerInfo2` rozhraní s metod podporovaných v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="d5491-136">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="d5491-137">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-137">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="d5491-138">Poskytuje metody, které profilery kódu se používají ke komunikaci s CLR řízení události monitorování a k požadavku na informace.</span><span class="sxs-lookup"><span data-stu-id="d5491-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="d5491-139">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-139">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="d5491-140">Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení události monitorování.</span><span class="sxs-lookup"><span data-stu-id="d5491-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="d5491-141">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-141">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="d5491-142">Poskytuje enumerátor pro všechny metody, který patří k dané NGen modulu a které jsou vložená v těle dané metody.</span><span class="sxs-lookup"><span data-stu-id="d5491-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="d5491-143">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-143">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="d5491-144">Poskytuje metodu použít nově definovaná metadata modulu, který poskytuje přístup k datovému proudu symbol v paměti.</span><span class="sxs-lookup"><span data-stu-id="d5491-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="d5491-145">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-145">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="d5491-146">Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly zavedené aplikace nebo profileru.</span><span class="sxs-lookup"><span data-stu-id="d5491-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="d5491-147">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-147">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="d5491-148">Poskytuje metody pro postupně iteraci přes kolekci ukotvené objektů, které jsou generovány nástrojem [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="d5491-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="d5491-149">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-149">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="d5491-150">Poskytuje metody pro postupně iteraci prostřednictvím kolekce vláken v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d5491-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="d5491-151">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5491-151">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="d5491-152">Poskytuje [alokační](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5491-152">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d5491-153">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d5491-153">Related Sections</span></span>  
 [<span data-ttu-id="d5491-154">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="d5491-154">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="d5491-155">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5491-155">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="d5491-156">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5491-156">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="d5491-157">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5491-157">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
