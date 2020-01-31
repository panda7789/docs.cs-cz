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
ms.openlocfilehash: 028207486f43e35086ed2e515eb3ae6bca304491
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866070"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="eed66-102">ICorProfilerCallback::ObjectsAllocatedByClass – metoda</span><span class="sxs-lookup"><span data-stu-id="eed66-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="eed66-103">Upozorňuje Profiler o počtu instancí každé zadané třídy, které byly vytvořeny od posledního uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="eed66-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eed66-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="eed66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eed66-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="eed66-106">pro Velikost polí `classIds` a `cObjects`</span><span class="sxs-lookup"><span data-stu-id="eed66-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="eed66-107">pro Pole identifikátorů třídy, kde každé ID určuje třídu s jednou nebo více instancemi.</span><span class="sxs-lookup"><span data-stu-id="eed66-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="eed66-108">pro Pole celých čísel, kde každé celé číslo určuje počet instancí odpovídající třídy v poli `classIds`.</span><span class="sxs-lookup"><span data-stu-id="eed66-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eed66-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eed66-109">Remarks</span></span>  
 <span data-ttu-id="eed66-110">Pole `classIds` a `cObjects` jsou paralelní pole.</span><span class="sxs-lookup"><span data-stu-id="eed66-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="eed66-111">Například `classIds[i]` a `cObjects[i]` odkazují na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="eed66-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="eed66-112">Pokud nebyla od předchozího uvolňování paměti vytvořena žádná instance třídy, je třída vynechána.</span><span class="sxs-lookup"><span data-stu-id="eed66-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="eed66-113">`ObjectsAllocatedByClass` zpětné volání nebude hlásit objekty přidělené v haldě velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="eed66-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="eed66-114">Čísla uvedená `ObjectsAllocatedByClass` jsou pouze odhady.</span><span class="sxs-lookup"><span data-stu-id="eed66-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="eed66-115">Pro přesné počty použijte [ICorProfilerCallback:: ObjectAllocated –](icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="eed66-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="eed66-116">Pole `classIds` může obsahovat jednu nebo více položek s hodnotou null, pokud odpovídající pole `cObjects` obsahuje typy, které jsou uvolňovány.</span><span class="sxs-lookup"><span data-stu-id="eed66-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eed66-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eed66-117">Requirements</span></span>  
 <span data-ttu-id="eed66-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eed66-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eed66-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eed66-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eed66-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eed66-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eed66-121">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eed66-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed66-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eed66-122">See also</span></span>

- [<span data-ttu-id="eed66-123">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eed66-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
