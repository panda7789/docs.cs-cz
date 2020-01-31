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
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866088"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="c7540-102">ICorProfilerCallback::ObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="c7540-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="c7540-103">Upozorní profiler na objekty v paměti, na které je odkazováno pomocí zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="c7540-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7540-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7540-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7540-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7540-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="c7540-106">pro ID objektu, který odkazuje na objekty.</span><span class="sxs-lookup"><span data-stu-id="c7540-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="c7540-107">pro ID třídy, jejíž zadaný objekt je instancí.</span><span class="sxs-lookup"><span data-stu-id="c7540-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="c7540-108">pro Počet objektů odkazovaný specifikovaným objektem (tj. počet prvků v poli `objectRefIds`).</span><span class="sxs-lookup"><span data-stu-id="c7540-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="c7540-109">pro Pole ID objektů, na které odkazují `objectId`.</span><span class="sxs-lookup"><span data-stu-id="c7540-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7540-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7540-110">Remarks</span></span>  
 <span data-ttu-id="c7540-111">Metoda `ObjectReferences` je volána pro každý objekt zbývající v haldě po dokončení uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c7540-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="c7540-112">Pokud Profiler vrátí chybu z tohoto zpětného volání, služba profilování přestane pokračovat ve volání tohoto zpětného volání do dalšího uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c7540-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="c7540-113">Zpětné volání `ObjectReferences` lze použít ve spojení s zpětným voláním [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) pro vytvoření kompletního grafu odkazů na objekty pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c7540-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="c7540-114">Modul CLR (Common Language Runtime) zajišťuje, že každý odkaz na objekt je uveden pouze jednou metodou `ObjectReferences`.</span><span class="sxs-lookup"><span data-stu-id="c7540-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="c7540-115">ID objektů vrácená `ObjectReferences` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů.</span><span class="sxs-lookup"><span data-stu-id="c7540-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="c7540-116">Proto se profilery nesmí pokoušet prozkoumat objekty během volání `ObjectReferences`.</span><span class="sxs-lookup"><span data-stu-id="c7540-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="c7540-117">Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) , uvolňování paměti je dokončeno a kontrola může být provedena bezpečně.</span><span class="sxs-lookup"><span data-stu-id="c7540-117">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="c7540-118">`ClassId` null značí, že `objectId` má typ, který se uvolňuje.</span><span class="sxs-lookup"><span data-stu-id="c7540-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7540-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7540-119">Requirements</span></span>  
 <span data-ttu-id="c7540-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7540-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7540-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c7540-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7540-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c7540-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7540-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7540-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7540-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7540-124">See also</span></span>

- [<span data-ttu-id="c7540-125">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7540-125">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
