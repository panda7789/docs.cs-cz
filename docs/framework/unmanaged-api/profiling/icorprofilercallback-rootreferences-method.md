---
title: ICorProfilerCallback::RootReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865958"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="56e09-102">ICorProfilerCallback::RootReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="56e09-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="56e09-103">Oznamuje profileru informace o kořenových odkazech po uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="56e09-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56e09-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="56e09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56e09-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="56e09-106">pro Počet odkazů v poli `rootRefIds`.</span><span class="sxs-lookup"><span data-stu-id="56e09-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="56e09-107">pro Pole ID objektů, které odkazuje buď na statický objekt, nebo na objekt v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="56e09-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56e09-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56e09-108">Remarks</span></span>  
 <span data-ttu-id="56e09-109">Pro upozorňování profileru jsou volány `RootReferences` a [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="56e09-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="56e09-110">Profilery obvykle implementují jeden nebo druhý, ale ne obojí, protože informace předané `RootReferences2` jsou nadmnožinou předaných `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="56e09-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="56e09-111">Je možné, že pole `rootRefIds` obsahuje objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="56e09-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="56e09-112">Například všechny odkazy na objekty deklarované v zásobníku jsou považovány za kořeny systémem uvolňování paměti a budou vždy hlášeny.</span><span class="sxs-lookup"><span data-stu-id="56e09-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="56e09-113">ID objektů vrácená `RootReferences` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých adres na nové adresy.</span><span class="sxs-lookup"><span data-stu-id="56e09-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="56e09-114">Proto se profilery nesmí pokoušet prozkoumat objekty během volání `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="56e09-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="56e09-115">Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) , všechny objekty byly přesunuty do jejich nových umístění a lze je bezpečně zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="56e09-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56e09-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56e09-116">Requirements</span></span>  
 <span data-ttu-id="56e09-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56e09-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56e09-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="56e09-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56e09-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="56e09-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56e09-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56e09-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e09-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56e09-121">See also</span></span>

- [<span data-ttu-id="56e09-122">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56e09-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
