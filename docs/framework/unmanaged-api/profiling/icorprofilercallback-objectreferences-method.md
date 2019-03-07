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
ms.openlocfilehash: e9659f37f0ae9297837dbc4b1602cb00b8eff2fd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471445"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="3f257-102">ICorProfilerCallback::ObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="3f257-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="3f257-103">Upozornění profileru o objektech v paměti, které se odkazuje zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="3f257-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f257-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f257-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f257-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f257-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="3f257-106">[in] ID objektu, který odkazuje na objekty.</span><span class="sxs-lookup"><span data-stu-id="3f257-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="3f257-107">[in] ID třídy, která je instance zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="3f257-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="3f257-108">[in] Počet objektů, které odkazuje zadaný objekt (to znamená, počet prvků v `objectRefIds` pole).</span><span class="sxs-lookup"><span data-stu-id="3f257-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="3f257-109">[in] Pole ID objektů, které se neodkazuje `objectId`.</span><span class="sxs-lookup"><span data-stu-id="3f257-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f257-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f257-110">Remarks</span></span>  
 <span data-ttu-id="3f257-111">`ObjectReferences` Metoda je volána pro každý objekt zbývajících v haldě, po dokončení procesu uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3f257-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="3f257-112">Pokud profiler vrátí chybu z této zpětné volání, bude profilování služby přestat vyvolání této zpětné volání až do dalšího uvolnění.</span><span class="sxs-lookup"><span data-stu-id="3f257-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="3f257-113">`ObjectReferences` Zpětného volání lze použít ve spojení s [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) zpětné volání pro vytvoření grafu odkaz na kompletní objekt pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="3f257-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="3f257-114">Modul CLR (CLR) zajišťuje, že každý odkaz na objekt je ohlášena jenom jednou `ObjectReferences` metody.</span><span class="sxs-lookup"><span data-stu-id="3f257-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="3f257-115">ID objektů vrácených `ObjectReferences` nejsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesouvání objektů.</span><span class="sxs-lookup"><span data-stu-id="3f257-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="3f257-116">Proto se nesmíte pokoušet profilery pro kontrolu objektů během `ObjectReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="3f257-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="3f257-117">Když [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, uvolňování paměti kolekce je kompletní a kontroly lze bezpečně provést.</span><span class="sxs-lookup"><span data-stu-id="3f257-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="3f257-118">S hodnotou null `ClassId` znamená, že `objectId` má typ, který je uvolnění.</span><span class="sxs-lookup"><span data-stu-id="3f257-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f257-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f257-119">Requirements</span></span>  
 <span data-ttu-id="3f257-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f257-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f257-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f257-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f257-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f257-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f257-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f257-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f257-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f257-124">See also</span></span>
- [<span data-ttu-id="3f257-125">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f257-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
