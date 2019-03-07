---
title: ICorProfilerCallback::ObjectsAllocatedByClass – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e26e7ac9b89e005d9520ad860cf3acee7d3cc6cc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479750"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="089cc-102">ICorProfilerCallback::ObjectsAllocatedByClass – metoda</span><span class="sxs-lookup"><span data-stu-id="089cc-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="089cc-103">Informuje o počtu instancí každé zadané třídy, které byly vytvořeny od posledního shromažďování dat paměti profilerem.</span><span class="sxs-lookup"><span data-stu-id="089cc-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="089cc-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="089cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="089cc-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="089cc-106">[in] Velikost `classIds` a `cObjects` pole.</span><span class="sxs-lookup"><span data-stu-id="089cc-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="089cc-107">[in] Pole ID, kde každé ID Určuje třídu s jednu nebo víc instancí tříd.</span><span class="sxs-lookup"><span data-stu-id="089cc-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="089cc-108">[in] Pole celých čísel, kde každé celé číslo určuje počet instancí pro odpovídající třídu v `classIds` pole.</span><span class="sxs-lookup"><span data-stu-id="089cc-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="089cc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="089cc-109">Remarks</span></span>  
 <span data-ttu-id="089cc-110">`classIds` a `cObjects` pole jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="089cc-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="089cc-111">Například `classIds[i]` a `cObjects[i]` odkazovat na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="089cc-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="089cc-112">Pokud od předchozí uvolňování paměti kolekce byla vytvořena žádná instance třídy, třída je vynechán.</span><span class="sxs-lookup"><span data-stu-id="089cc-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="089cc-113">`ObjectsAllocatedByClass` Zpětné volání, nebudou podávat objekty přidělené ve velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="089cc-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="089cc-114">Čísla hlášených `ObjectsAllocatedByClass` jsou pouze odhady.</span><span class="sxs-lookup"><span data-stu-id="089cc-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="089cc-115">Přesný počet, použijte [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="089cc-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="089cc-116">`classIds` Pole může obsahovat jeden nebo více položky s hodnotou null, pokud odpovídající `cObjects` pole obsahuje typy, které jsou uvolnění.</span><span class="sxs-lookup"><span data-stu-id="089cc-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="089cc-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="089cc-117">Requirements</span></span>  
 <span data-ttu-id="089cc-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="089cc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="089cc-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="089cc-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="089cc-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="089cc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="089cc-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="089cc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089cc-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="089cc-122">See also</span></span>
- [<span data-ttu-id="089cc-123">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="089cc-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
