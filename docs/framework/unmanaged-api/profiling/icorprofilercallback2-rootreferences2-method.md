---
title: ICorProfilerCallback2::RootReferences2 – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09616243aef272be041573864effd25017cc65c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082149"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="ca5b2-102">ICorProfilerCallback2::RootReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ca5b2-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="ca5b2-103">Oznámí profileru odkazy na kořenové po uvolňování paměti došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="ca5b2-104">Tato metoda je rozšířením [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca5b2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca5b2-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca5b2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca5b2-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="ca5b2-107">[in] Počet prvků v `rootRefIds`, `rootKinds`, `rootFlags`, a `rootIds` pole.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="ca5b2-108">[in] Pole objektu ID, každý z nich odkazuje na statický objekt nebo objekt v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="ca5b2-109">Prvky `rootKinds` pole obsahují informace, které klasifikovat odpovídající elementy ve `rootRefIds` pole.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="ca5b2-110">[in] Pole [cor_prf_gc_root_kind –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) hodnoty, které označují typ kořenové kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="ca5b2-111">[in] Pole [cor_prf_gc_root_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) hodnot, které popisují vlastnosti kořenové kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="ca5b2-112">[in] Pole UINT_PTR hodnoty, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce uvolnění paměti, v závislosti na hodnotu `rootKinds` parametru.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="ca5b2-113">Pokud je typ kořenového zásobníku, ID kořenového je pro funkci, která obsahuje proměnnou.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="ca5b2-114">Pokud toto ID kořenového je 0, funkce je nepojmenovaný funkce, který je interní modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="ca5b2-115">Pokud je typ kořenového popisovač, ID kořenového je pro popisovač kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="ca5b2-116">U jiných typů kořenové ID je neprůhledná hodnota a je třeba ignorovat.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca5b2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca5b2-117">Remarks</span></span>  
 <span data-ttu-id="ca5b2-118">`rootRefIds`, `rootKinds`, `rootFlags`, A `rootIds` pole jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="ca5b2-119">To znamená `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, a `rootIds[i]` všechny týkají stejným kořenem.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="ca5b2-120">Obě `RootReferences` a `RootReferences2` jsou volány pro oznámení profileru.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="ca5b2-121">Profilery obvykle implementuje jednu metodu nebo druhé, ale ne obojí, protože předaným informace `RootReferences2` je nadstavbou jazyka, které předáno `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="ca5b2-122">Je možné pro položky v `rootRefIds` rovno nule, což znamená, že odpovídající kořenový odkaz má hodnotu null a neodkazuje na objekt na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="ca5b2-123">ID objektů vrácených `RootReferences2` nejsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesun objektů ze staré adresy k nové adresy.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="ca5b2-124">Proto by se neměly pokoušet profilery pro kontrolu objektů během `RootReferences2` volání.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="ca5b2-125">Když [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, všechny objekty se přesunuly na jejich nových umístění a můžete ho bezpečně zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="ca5b2-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca5b2-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca5b2-126">Requirements</span></span>  
 <span data-ttu-id="ca5b2-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca5b2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca5b2-128">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ca5b2-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca5b2-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca5b2-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ca5b2-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ca5b2-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ca5b2-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca5b2-131">See also</span></span>

- [<span data-ttu-id="ca5b2-132">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca5b2-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ca5b2-133">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca5b2-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
