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
ms.openlocfilehash: 4f8cfd912a3d6f66f5f2586a8942c7ce9bd52a63
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445884"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="01e0e-102">ICorProfilerCallback::ObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="01e0e-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="01e0e-103">Upozorní profiler na objekty v paměti, na které je odkazováno pomocí zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="01e0e-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01e0e-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="01e0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01e0e-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="01e0e-106">pro ID objektu, který odkazuje na objekty.</span><span class="sxs-lookup"><span data-stu-id="01e0e-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="01e0e-107">pro ID třídy, jejíž zadaný objekt je instancí.</span><span class="sxs-lookup"><span data-stu-id="01e0e-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="01e0e-108">pro Počet objektů odkazovaný specifikovaným objektem (tj. počet prvků v poli `objectRefIds`).</span><span class="sxs-lookup"><span data-stu-id="01e0e-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="01e0e-109">pro Pole ID objektů, na které odkazují `objectId`.</span><span class="sxs-lookup"><span data-stu-id="01e0e-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01e0e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01e0e-110">Remarks</span></span>  
 <span data-ttu-id="01e0e-111">Metoda `ObjectReferences` je volána pro každý objekt zbývající v haldě po dokončení uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="01e0e-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="01e0e-112">Pokud Profiler vrátí chybu z tohoto zpětného volání, služba profilování přestane pokračovat ve volání tohoto zpětného volání do dalšího uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="01e0e-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="01e0e-113">Zpětné volání `ObjectReferences` lze použít ve spojení s zpětným voláním [ICorProfilerCallback:: RootReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) pro vytvoření kompletního grafu odkazů na objekty pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="01e0e-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="01e0e-114">Modul CLR (Common Language Runtime) zajišťuje, že každý odkaz na objekt je uveden pouze jednou metodou `ObjectReferences`.</span><span class="sxs-lookup"><span data-stu-id="01e0e-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="01e0e-115">ID objektů vrácená `ObjectReferences` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů.</span><span class="sxs-lookup"><span data-stu-id="01e0e-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="01e0e-116">Proto se profilery nesmí pokoušet prozkoumat objekty během volání `ObjectReferences`.</span><span class="sxs-lookup"><span data-stu-id="01e0e-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="01e0e-117">Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) , uvolňování paměti je dokončeno a kontrola může být provedena bezpečně.</span><span class="sxs-lookup"><span data-stu-id="01e0e-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="01e0e-118">`ClassId` null značí, že `objectId` má typ, který se uvolňuje.</span><span class="sxs-lookup"><span data-stu-id="01e0e-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e0e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01e0e-119">Requirements</span></span>  
 <span data-ttu-id="01e0e-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01e0e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e0e-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="01e0e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01e0e-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01e0e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01e0e-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e0e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e0e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01e0e-124">See also</span></span>

- [<span data-ttu-id="01e0e-125">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01e0e-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
