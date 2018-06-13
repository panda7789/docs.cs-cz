---
title: ICorProfilerCallback::ObjectReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e64eeff8ef80aa264c9c49bd12a0cc45e0da18a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461884"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="a0ec8-102">ICorProfilerCallback::ObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="a0ec8-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="a0ec8-103">Upozorní profileru o objektech v paměti, které se odkazuje zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ec8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0ec8-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0ec8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0ec8-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a0ec8-106">[v] ID objektu, která odkazují objekty.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="a0ec8-107">[v] ID třídy, která představuje instanci zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="a0ec8-108">[v] Počet objektů, které odkazuje zadaný objekt (který je počet elementů ve `objectRefIds` pole).</span><span class="sxs-lookup"><span data-stu-id="a0ec8-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="a0ec8-109">[v] Pole ID objektů, které se odkazuje `objectId`.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0ec8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0ec8-110">Remarks</span></span>  
 <span data-ttu-id="a0ec8-111">`ObjectReferences` Metoda je volána pro každý objekt v haldě zbývající po dokončení uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="a0ec8-112">Pokud profileru vrátí chybu z této zpětné volání, bude zastaveno profilování služby vyvolání tento zpětného volání až do další uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="a0ec8-113">`ObjectReferences` Zpětného volání lze použít ve spojení s [icorprofilercallback::rootreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) zpětné volání pro vytvoření grafu odkaz dokončení objektu pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="a0ec8-114">Modul CLR (CLR) zajišťuje, že každý odkaz na objekt je hlášen jenom jednou `ObjectReferences` metoda.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="a0ec8-115">Vrácený objekt ID `ObjectReferences` nejsou platné během zpětného volání sebe, protože kolekce paměti může být uprostřed přesun objektů.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="a0ec8-116">Proto se profilery nesmíte pokoušet zkontrolovat objekty během `ObjectReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="a0ec8-117">Když [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána paměti kolekce je úplný a kontroly lze bezpečně provést.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="a0ec8-118">Null `ClassId` znamená, že `objectId` má typ, který je uvolnění.</span><span class="sxs-lookup"><span data-stu-id="a0ec8-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0ec8-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0ec8-119">Requirements</span></span>  
 <span data-ttu-id="a0ec8-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0ec8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0ec8-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0ec8-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0ec8-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0ec8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0ec8-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0ec8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ec8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0ec8-124">See Also</span></span>  
 [<span data-ttu-id="a0ec8-125">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0ec8-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
