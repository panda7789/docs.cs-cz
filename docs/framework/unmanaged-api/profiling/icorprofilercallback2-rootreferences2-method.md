---
title: "ICorProfilerCallback2::RootReferences2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29a5a3051b75df18a08498369aa5707a53caf75f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="fdff3-102">ICorProfilerCallback2::RootReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fdff3-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="fdff3-103">Upozorní profileru o odkazů na kořenový po uvolnění paměti došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="fdff3-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="fdff3-104">Tato metoda je rozšířením [icorprofilercallback::rootreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="fdff3-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdff3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdff3-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fdff3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdff3-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="fdff3-107">[v] Počet elementů ve `rootRefIds`, `rootKinds`, `rootFlags`, a `rootIds` pole.</span><span class="sxs-lookup"><span data-stu-id="fdff3-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="fdff3-108">[v] Pole ID, objektů každý z nich odkazuje na objekt statické nebo objekt v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="fdff3-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="fdff3-109">Elementy v `rootKinds` pole obsahují informace, které klasifikovat odpovídající elementů v `rootRefIds` pole.</span><span class="sxs-lookup"><span data-stu-id="fdff3-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="fdff3-110">[v] Pole [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) hodnoty, které označují typ kořenové kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="fdff3-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="fdff3-111">[v] Pole [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) hodnoty, které popisuje vlastnosti kořenové kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="fdff3-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="fdff3-112">[v] Pole UINT_PTR hodnot, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce paměti, v závislosti na hodnotě `rootKinds` parametr.</span><span class="sxs-lookup"><span data-stu-id="fdff3-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="fdff3-113">Pokud je typ kořenové zásobníku, kořenové ID je pro tuto funkci, která obsahuje proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fdff3-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="fdff3-114">Pokud toto ID kořenové 0, funkce je nepojmenované funkce, která je interní modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="fdff3-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="fdff3-115">Je-li typ kořenové popisovač, je kořenový ID pro popisovač kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="fdff3-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="fdff3-116">Pro ostatní typy kořenové ID je neprůhledné hodnoty a třeba ji ignorovat.</span><span class="sxs-lookup"><span data-stu-id="fdff3-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdff3-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdff3-117">Remarks</span></span>  
 <span data-ttu-id="fdff3-118">`rootRefIds`, `rootKinds`, `rootFlags`, A `rootIds` pole jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="fdff3-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="fdff3-119">To znamená `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, a `rootIds[i]` všechny týkají stejnou kořenovou.</span><span class="sxs-lookup"><span data-stu-id="fdff3-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="fdff3-120">Obě `RootReferences` a `RootReferences2` se nazývají oznámit profileru.</span><span class="sxs-lookup"><span data-stu-id="fdff3-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="fdff3-121">Profilery bude obvykle implementovat jednu metodu nebo dalších, ale ne obojí, protože předaná informace `RootReferences2` je nadmnožinou, je předaná `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="fdff3-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="fdff3-122">Je možné pro položky v `rootRefIds` být nula, což znamená, že odkaz na odpovídající kořenové má hodnotu null a není odkaz na objekt v haldě spravované.</span><span class="sxs-lookup"><span data-stu-id="fdff3-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="fdff3-123">Vrácený objekt ID `RootReferences2` nejsou platné během zpětného volání sebe, protože kolekce paměti může být uprostřed přesun objektů z původní adresy na nové adresy.</span><span class="sxs-lookup"><span data-stu-id="fdff3-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="fdff3-124">Proto profilery neměli zkontrolovat objekty během `RootReferences2` volání.</span><span class="sxs-lookup"><span data-stu-id="fdff3-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="fdff3-125">Když [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, všechny objekty byly přesunuty do nového umístění a může být prověřovány bezpečně.</span><span class="sxs-lookup"><span data-stu-id="fdff3-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdff3-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdff3-126">Requirements</span></span>  
 <span data-ttu-id="fdff3-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdff3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdff3-128">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fdff3-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdff3-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdff3-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdff3-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdff3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdff3-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdff3-131">See Also</span></span>  
 [<span data-ttu-id="fdff3-132">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdff3-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fdff3-133">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdff3-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
