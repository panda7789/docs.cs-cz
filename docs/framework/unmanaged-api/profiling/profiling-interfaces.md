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
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457459"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="28581-102">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="28581-102">Profiling Interfaces</span></span>
<span data-ttu-id="28581-103">Tato část popisuje nespravovaná rozhraní, které vám umožní profilování program, který se provádí modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="28581-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28581-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="28581-104">In This Section</span></span>  
 [<span data-ttu-id="28581-105">ICLRProfiling – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="28581-106">Poskytuje [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metodu, která umožňuje profileru připojit ke spuštěnému procesu.</span><span class="sxs-lookup"><span data-stu-id="28581-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="28581-107">ICorProfilerAssemblyReferenceProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="28581-108">Umožňuje profileru informovat CLR odkazy na sestavení, které profiler přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="28581-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="28581-109">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="28581-110">Poskytuje metody, které se používají modulem CLR upozornění profileru kód, pokud dojde k událostem, ke kterým se připojila profiler.</span><span class="sxs-lookup"><span data-stu-id="28581-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="28581-111">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="28581-112">Rozšiřuje `ICorProfilerCallback` rozhraní s zpětná volání, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="28581-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="28581-113">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="28581-114">Poskytuje metody zpětného volání, které používá modul CLR pro komunikaci připojení a odpojení profileru informace o stavu.</span><span class="sxs-lookup"><span data-stu-id="28581-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="28581-115">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="28581-116">Poskytuje metody zpětného volání, které používá modul CLR ke sdělování informací profileru.</span><span class="sxs-lookup"><span data-stu-id="28581-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="28581-117">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="28581-118">Poskytuje metodu, která identifikuje přechodné uzavření objekty odkazuje kořeny kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="28581-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="28581-119">ICorProfilerCallback6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="28581-120">Poskytuje metodu zpětného volání, která používá modul CLR oznámit profiler, který se načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="28581-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="28581-121">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="28581-122">Poskytuje metodu zpětného volání, která používá modul common language runtime pro oznámení profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="28581-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="28581-123">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-123">ICorProfilerCallback8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
<span data-ttu-id="28581-124">Poskytuje metody zpětného volání, které používá modul common language runtime pro oznámení profileru, který je spuštěn a dokončení kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="28581-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="28581-125">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-125">ICorProfilerCallback9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
<span data-ttu-id="28581-126">Poskytuje metodu zpětného volání, která používá modul common language runtime pro oznámení profileru, který je dynamická metoda uvolňování paměti shromažďují a následně byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="28581-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="28581-127">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-127">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="28581-128">Poskytuje metody, které umožňují profileru kód ke komunikaci s modulem CLR řídit, jak by měl kompilátor JIT generování kódu při opětovné kompilaci konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="28581-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="28581-129">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-129">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="28581-130">Poskytuje metody pro postupně iteraci prostřednictvím kolekce funkcí v CLR.</span><span class="sxs-lookup"><span data-stu-id="28581-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="28581-131">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-131">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="28581-132">Poskytuje metody pro použití u profilery kódu ke komunikaci s modulem CLR řídit sledování událostí a žádost o informace.</span><span class="sxs-lookup"><span data-stu-id="28581-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="28581-133">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-133">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="28581-134">Rozšiřuje `ICorProfilerInfo` rozhraní s metodami, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="28581-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="28581-135">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-135">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="28581-136">Rozšiřuje `ICorProfilerInfo2` rozhraní s metodami, které jsou podporovány v rozhraní .NET Framework 4 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="28581-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="28581-137">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-137">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="28581-138">Poskytuje metody, které profilery kódu se používají ke komunikaci s modulem CLR k řízení sledování událostí a požádat o informace.</span><span class="sxs-lookup"><span data-stu-id="28581-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="28581-139">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-139">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="28581-140">Poskytuje metody pro použití u profilery kódu ke komunikaci s modulem CLR řízení události monitorování.</span><span class="sxs-lookup"><span data-stu-id="28581-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="28581-141">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-141">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="28581-142">Poskytuje enumerátor pro všechny metody, která patří do daného modulu NGen a, které jsou vloženy do těla dané metody.</span><span class="sxs-lookup"><span data-stu-id="28581-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="28581-143">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-143">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="28581-144">Poskytuje způsob, jak použít nově definované v modulu metadat, který poskytuje přístup k datovému proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="28581-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="28581-145">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-145">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="28581-146">Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly načtené aplikace nebo profileru.</span><span class="sxs-lookup"><span data-stu-id="28581-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="28581-147">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-147">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="28581-148">Poskytuje metody, které postupně iterovat přes kolekci zmrazené objekty, které se vygenerovaly [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="28581-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="28581-149">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-149">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="28581-150">Poskytuje metody pro postupně iterovat přes kolekci vláken v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="28581-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="28581-151">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28581-151">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="28581-152">Poskytuje [alokační](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda přidělení paměti pro nové tělo funkce Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="28581-152">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="28581-153">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="28581-153">Related Sections</span></span>  
 [<span data-ttu-id="28581-154">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="28581-154">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="28581-155">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="28581-155">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="28581-156">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="28581-156">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="28581-157">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="28581-157">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
