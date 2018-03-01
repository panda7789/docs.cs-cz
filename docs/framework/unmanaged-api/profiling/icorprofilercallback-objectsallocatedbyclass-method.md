---
title: "ICorProfilerCallback::ObjectsAllocatedByClass – metoda"
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
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4adeda7ac884b37bcfc2b0c9599dd8e36c469747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="9e069-102">ICorProfilerCallback::ObjectsAllocatedByClass – metoda</span><span class="sxs-lookup"><span data-stu-id="9e069-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="9e069-103">Informuje o počtu instancí každé zadané třídy, které byly vytvořeny od poslední uvolňování profileru.</span><span class="sxs-lookup"><span data-stu-id="9e069-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e069-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e069-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e069-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e069-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="9e069-106">[v] Velikost `classIds` a `cObjects` pole.</span><span class="sxs-lookup"><span data-stu-id="9e069-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="9e069-107">[v] Pole ID, kde každý ID Určuje třídu s jednu nebo více instancí tříd.</span><span class="sxs-lookup"><span data-stu-id="9e069-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="9e069-108">[v] Pole celých čísel, kde každý celé číslo určuje počet instancí pro odpovídající třídu v `classIds` pole.</span><span class="sxs-lookup"><span data-stu-id="9e069-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e069-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e069-109">Remarks</span></span>  
 <span data-ttu-id="9e069-110">`classIds` a `cObjects` pole jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="9e069-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="9e069-111">Například `classIds[i]` a `cObjects[i]` odkazovat na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="9e069-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="9e069-112">Pokud od předchozí uvolňování byla vytvořena žádná instance třídy, třída je vynechán.</span><span class="sxs-lookup"><span data-stu-id="9e069-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="9e069-113">`ObjectsAllocatedByClass` Zpětného volání, nebudou podávat objekty přidělené v haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="9e069-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="9e069-114">Čísla hlášené `ObjectsAllocatedByClass` jsou jenom odhadované.</span><span class="sxs-lookup"><span data-stu-id="9e069-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="9e069-115">Pro přesné počty použít [icorprofilercallback::objectallocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="9e069-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="9e069-116">`classIds` Pole může obsahovat jeden nebo více položky s hodnotou null, pokud odpovídající `cObjects` pole obsahuje typy, které jsou uvolnění.</span><span class="sxs-lookup"><span data-stu-id="9e069-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e069-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e069-117">Requirements</span></span>  
 <span data-ttu-id="9e069-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e069-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e069-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e069-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e069-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e069-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e069-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e069-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e069-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e069-122">See Also</span></span>  
 [<span data-ttu-id="9e069-123">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e069-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
