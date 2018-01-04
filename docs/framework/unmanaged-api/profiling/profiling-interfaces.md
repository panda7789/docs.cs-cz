---
title: "Rozhraní pro profilaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f8c2a5ce5e1231c55f598e48d14bec896a4b5f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-interfaces"></a><span data-ttu-id="2e106-102">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2e106-102">Profiling Interfaces</span></span>
<span data-ttu-id="2e106-103">Tato část popisuje nespravovaná rozhraní, které vám umožní profilu program, který je vykonáván common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2e106-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e106-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2e106-104">In This Section</span></span>  
 [<span data-ttu-id="2e106-105">ICLRProfiling – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="2e106-106">Poskytuje [attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda, která umožňuje profileru pro připojení k spuštěných procesů.</span><span class="sxs-lookup"><span data-stu-id="2e106-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="2e106-107">ICorProfilerAssemblyReferenceProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="2e106-108">Umožňuje profileru k informování CLR odkazů na sestavení, které profileru přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2e106-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="2e106-109">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="2e106-110">Poskytuje metody, které jsou používány modulu CLR profileru kód upozornit, když dojde k události, ke kterým se připojila profileru.</span><span class="sxs-lookup"><span data-stu-id="2e106-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="2e106-111">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="2e106-112">Rozšiřuje `ICorProfilerCallback` rozhraní s zpětná volání, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="2e106-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="2e106-113">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="2e106-114">Poskytuje metody zpětného volání, které modul CLR používá ke komunikaci připojení a odpojení informace o stavu do profileru.</span><span class="sxs-lookup"><span data-stu-id="2e106-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="2e106-115">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="2e106-116">Poskytuje metody zpětného volání, které modul CLR používá ke sdělování informací profileru.</span><span class="sxs-lookup"><span data-stu-id="2e106-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="2e106-117">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="2e106-118">Poskytne metodu, která identifikuje přechodné uzavření objekty odkazuje kořeny kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="2e106-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="2e106-119">ICorProfilerCallback6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="2e106-120">Poskytuje metody zpětného volání, která používá modulu CLR oznámit profileru, který načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e106-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="2e106-121">ICorProfilerCallback7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="2e106-122">Poskytuje metody zpětného volání, která používá modul common language runtime profileru oznámit, že se aktualizuje symbol datový proud přidružený modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="2e106-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
 [<span data-ttu-id="2e106-123">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-123">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="2e106-124">Poskytuje metody, které umožňují kódu profileru ke komunikaci s CLR řídit, jak by měla JIT kompilátoru generování kódu při nutnosti rekompilace konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="2e106-124">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="2e106-125">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-125">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="2e106-126">Poskytuje metody pro postupně iteraci přes kolekci funkcí v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2e106-126">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="2e106-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="2e106-128">Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení sledování událostí a vyžádání informací.</span><span class="sxs-lookup"><span data-stu-id="2e106-128">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="2e106-129">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-129">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="2e106-130">Rozšiřuje `ICorProfilerInfo` rozhraní s metod podporovaných v rozhraní .NET Framework 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="2e106-130">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="2e106-131">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-131">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="2e106-132">Rozšiřuje `ICorProfilerInfo2` rozhraní s metod podporovaných v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="2e106-132">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="2e106-133">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-133">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="2e106-134">Poskytuje metody, které profilery kódu se používají ke komunikaci s CLR řízení události monitorování a k požadavku na informace.</span><span class="sxs-lookup"><span data-stu-id="2e106-134">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="2e106-135">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-135">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="2e106-136">Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení události monitorování.</span><span class="sxs-lookup"><span data-stu-id="2e106-136">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="2e106-137">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="2e106-138">Poskytuje enumerátor pro všechny metody, který patří k dané NGen modulu a které jsou vložená v těle dané metody.</span><span class="sxs-lookup"><span data-stu-id="2e106-138">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="2e106-139">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-139">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="2e106-140">Poskytuje metodu použít nově definovaná metadata modulu, který poskytuje přístup k datovému proudu symbol v paměti.</span><span class="sxs-lookup"><span data-stu-id="2e106-140">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="2e106-141">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-141">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="2e106-142">Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly zavedené aplikace nebo profileru.</span><span class="sxs-lookup"><span data-stu-id="2e106-142">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="2e106-143">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-143">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="2e106-144">Poskytuje metody pro postupně iteraci přes kolekci ukotvené objektů, které jsou generovány nástrojem [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="2e106-144">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="2e106-145">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-145">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="2e106-146">Poskytuje metody pro postupně iteraci prostřednictvím kolekce vláken v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2e106-146">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="2e106-147">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e106-147">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="2e106-148">Poskytuje [alokační](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2e106-148">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2e106-149">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2e106-149">Related Sections</span></span>  
 [<span data-ttu-id="2e106-150">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="2e106-150">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="2e106-151">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2e106-151">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="2e106-152">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2e106-152">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="2e106-153">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2e106-153">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
