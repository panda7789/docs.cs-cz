---
title: Rozhraní pro profilaci
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: 8b6b9acff2945e2d8fd684bfa31e4af086ea5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868145"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="45f50-102">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="45f50-102">Profiling Interfaces</span></span>
<span data-ttu-id="45f50-103">Tato část popisuje nespravovaná rozhraní, která umožňují profilovat program, který je spuštěn modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="45f50-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45f50-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="45f50-104">In This Section</span></span>  
 [<span data-ttu-id="45f50-105">ICLRProfiling – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-105">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="45f50-106">Poskytuje metodu [AttachProfiler –](iclrprofiling-attachprofiler-method.md) , která umožňuje profileru připojit se k běžícímu procesu.</span><span class="sxs-lookup"><span data-stu-id="45f50-106">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="45f50-107">ICorProfilerAssemblyReferenceProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="45f50-108">Umožňuje profileru informovat modul CLR o odkazech na sestavení, které bude Profiler přidávat do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="45f50-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="45f50-109">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-109">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="45f50-110">Poskytuje metody, které používá modul CLR k oznamování profileru kódu, když dojde k událostem, ke kterým má Profiler odběr.</span><span class="sxs-lookup"><span data-stu-id="45f50-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="45f50-111">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-111">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="45f50-112">Rozšiřuje rozhraní `ICorProfilerCallback` pomocí zpětných volání podporovaných v .NET Framework 2,0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="45f50-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="45f50-113">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-113">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="45f50-114">Poskytuje metody zpětného volání, které modul CLR používá ke komunikaci informací o stavu připojení a odpojení profileru.</span><span class="sxs-lookup"><span data-stu-id="45f50-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="45f50-115">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-115">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="45f50-116">Poskytuje metody zpětného volání, které modul CLR používá ke sdělování informací do profileru.</span><span class="sxs-lookup"><span data-stu-id="45f50-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="45f50-117">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-117">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="45f50-118">Poskytuje metodu, která identifikuje přenosný uzávěr objektů, na které odkazují kořeny uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="45f50-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="45f50-119">ICorProfilerCallback6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-119">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="45f50-120">Poskytuje metodu zpětného volání, kterou modul CLR používá pro upozornění profileru, že se sestavení načítá.</span><span class="sxs-lookup"><span data-stu-id="45f50-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="45f50-121">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-121">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="45f50-122">Poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že je aktualizován datový proud symbolů přidružený k modulu v paměti.</span><span class="sxs-lookup"><span data-stu-id="45f50-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="45f50-123">ICorProfilerCallback8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="45f50-124">Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá pro upozornění profileru o spuštění a dokončení kompilace JIT dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="45f50-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="45f50-125">ICorProfilerCallback9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-125">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="45f50-126">Poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že dynamická metoda je uvolněna z paměti a následně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="45f50-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="45f50-127">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-127">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="45f50-128">Poskytuje metody, které umožňují profileru kódu komunikovat s modulem CLR pro řízení způsobu, jakým má kompilátor JIT vygenerovat kód při rekompilaci konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="45f50-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="45f50-129">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-129">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="45f50-130">Poskytuje metody pro sekvenční iteraci kolekcí funkcí v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="45f50-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="45f50-131">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="45f50-132">Poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR pro řízení událostí a informace o požadavcích.</span><span class="sxs-lookup"><span data-stu-id="45f50-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="45f50-133">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-133">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="45f50-134">Rozšiřuje rozhraní `ICorProfilerInfo` s metodami podporovanými v .NET Framework 2,0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="45f50-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="45f50-135">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-135">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="45f50-136">Rozšiřuje rozhraní `ICorProfilerInfo2` o metody podporované .NET Framework 4 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="45f50-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="45f50-137">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-137">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="45f50-138">Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR k řízení sledování událostí a k vyžádání informací.</span><span class="sxs-lookup"><span data-stu-id="45f50-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="45f50-139">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="45f50-140">Poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR k řízení sledování událostí.</span><span class="sxs-lookup"><span data-stu-id="45f50-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="45f50-141">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-141">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="45f50-142">Poskytuje enumerátor pro všechny metody, které patří do daného modulu NGen a které jsou v těle dané metody vložené.</span><span class="sxs-lookup"><span data-stu-id="45f50-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="45f50-143">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-143">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="45f50-144">Poskytuje způsob, jak použít nově definovaná metadata na modul a který poskytuje přístup k datovému proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="45f50-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="45f50-145">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-145">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="45f50-146">Poskytuje metody pro sekvenční iteraci kolekcí modulů načtených aplikací nebo profilerem.</span><span class="sxs-lookup"><span data-stu-id="45f50-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="45f50-147">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-147">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="45f50-148">Poskytuje metody pro sekvenční iteraci kolekcí zmrazených objektů, které jsou generovány pomocí nástroje [Ngen. exe (generátor nativních imagí)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="45f50-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="45f50-149">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-149">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="45f50-150">Poskytuje metody pro sekvenční iteraci v kolekci vláken v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="45f50-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="45f50-151">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45f50-151">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="45f50-152">Poskytuje metodu [přidělení](imethodmalloc-alloc-method.md) pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="45f50-152">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="45f50-153">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="45f50-153">Related Sections</span></span>  
 [<span data-ttu-id="45f50-154">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="45f50-154">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="45f50-155">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="45f50-155">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="45f50-156">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="45f50-156">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="45f50-157">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="45f50-157">Profiling Structures</span></span>](profiling-structures.md)
