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
ms.openlocfilehash: 2ce58113f40c8eb67a89b6ab6c9bb8f755975bd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499750"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="a5946-102">ICorProfilerCallback2::RootReferences2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a5946-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="a5946-103">Oznamuje Profiler o kořenových odkazech poté, co došlo k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a5946-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="a5946-104">Tato metoda je rozšířením metody [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a5946-104">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5946-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5946-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5946-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5946-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="a5946-107">pro Počet prvků v `rootRefIds` polích,, a `rootKinds` `rootFlags` `rootIds` .</span><span class="sxs-lookup"><span data-stu-id="a5946-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="a5946-108">pro Pole identifikátorů objektů, z nichž každý odkazuje buď na statický objekt, nebo na objekt v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a5946-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="a5946-109">Prvky v `rootKinds` poli poskytují informace pro klasifikaci odpovídajících prvků v `rootRefIds` poli.</span><span class="sxs-lookup"><span data-stu-id="a5946-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="a5946-110">pro Pole hodnot [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) , které určují typ kořenu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a5946-110">[in] An array of [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="a5946-111">pro Pole hodnot [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) , které popisují vlastnosti kořenu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a5946-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="a5946-112">pro Pole hodnot UINT_PTR, které odkazují na celé číslo, které obsahuje další informace o kořenu uvolňování paměti v závislosti na hodnotě `rootKinds` parametru.</span><span class="sxs-lookup"><span data-stu-id="a5946-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="a5946-113">Pokud je typ kořenového adresáře zásobník, je ID kořenového adresáře pro funkci, která obsahuje proměnnou.</span><span class="sxs-lookup"><span data-stu-id="a5946-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="a5946-114">Pokud je toto kořenové ID 0, funkce je nepojmenovaná funkce, která je interní pro CLR.</span><span class="sxs-lookup"><span data-stu-id="a5946-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="a5946-115">Pokud je typ kořene popisovač, ID kořenového adresáře je pro popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a5946-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="a5946-116">U ostatních kořenových typů je ID neprůhledná hodnota a měla by být ignorována.</span><span class="sxs-lookup"><span data-stu-id="a5946-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5946-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5946-117">Remarks</span></span>  
 <span data-ttu-id="a5946-118">Pole `rootRefIds` , `rootKinds` , `rootFlags` a `rootIds` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="a5946-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="a5946-119">To znamená,,, `rootRefIds[i]` `rootKinds[i]` `rootFlags[i]` , a `rootIds[i]` všechny se týkají stejného kořene.</span><span class="sxs-lookup"><span data-stu-id="a5946-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="a5946-120">`RootReferences`A `RootReferences2` jsou volány pro upozorňování profileru.</span><span class="sxs-lookup"><span data-stu-id="a5946-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="a5946-121">Profilery obvykle implementují jednu metodu nebo druhou, ale ne obojí, protože předané informace `RootReferences2` jsou nadmnožinou, kterou předává `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="a5946-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="a5946-122">Je možné `rootRefIds` , že položky mají hodnotu nula, což znamená, že odpovídající kořenový odkaz má hodnotu null a neodkazuje na objekt na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="a5946-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="a5946-123">ID objektů vrácená nástrojem `RootReferences2` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých adres na nové adresy.</span><span class="sxs-lookup"><span data-stu-id="a5946-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="a5946-124">Proto by profilery neměly zkoušet při volání kontrolu objektů `RootReferences2` .</span><span class="sxs-lookup"><span data-stu-id="a5946-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="a5946-125">Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) , všechny objekty byly přesunuty do jejich nových umístění a lze je bezpečně zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="a5946-125">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5946-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5946-126">Requirements</span></span>  
 <span data-ttu-id="a5946-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5946-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5946-128">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a5946-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5946-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a5946-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5946-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5946-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5946-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5946-131">See also</span></span>

- [<span data-ttu-id="a5946-132">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5946-132">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a5946-133">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5946-133">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
