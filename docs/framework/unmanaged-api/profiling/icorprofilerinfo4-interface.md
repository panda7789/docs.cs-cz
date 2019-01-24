---
title: ICorProfilerInfo4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78f9645ad31e7421e239089c5610f6523918228b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536620"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="2f708-102">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f708-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="2f708-103">Poskytuje metody, které profilery kódu se používají ke komunikaci s common language runtime (CLR), která řídí sledování událostí a informace o žádostech.</span><span class="sxs-lookup"><span data-stu-id="2f708-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="2f708-104">.</span><span class="sxs-lookup"><span data-stu-id="2f708-104">.</span></span> <span data-ttu-id="2f708-105">`ICorProfilerInfo4` Rozhraní je rozšířením druhým `ICorProfilerInfo` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2f708-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="2f708-106">Poskytuje nové metody pro podporu rekompilace just-in-time (JIT), přidá [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f708-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f708-107">Metody</span><span class="sxs-lookup"><span data-stu-id="2f708-107">Methods</span></span>  
  
|<span data-ttu-id="2f708-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-108">Method</span></span>|<span data-ttu-id="2f708-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2f708-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f708-110">EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="2f708-111">Vrátí enumerátor pro všechny funkce, které byly dříve zkompilován JIT Kompilátorem a překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="2f708-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="2f708-112">EnumThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="2f708-113">Získá enumerátor, který poskytuje metody, které postupně iterovat přes kolekci všechna spravovaná vlákna v profilovaný proces.</span><span class="sxs-lookup"><span data-stu-id="2f708-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="2f708-114">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="2f708-115">Získá rozsah nativního kódu přidružené verze překompilován JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="2f708-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="2f708-116">GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="2f708-117">Mapuje ukazatel na instrukci spravovaného kódu na verzi překompilován JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="2f708-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="2f708-118">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="2f708-119">Získá mapování z Microsoft intermediate language (MSIL) kompenzuje do nativních posunů pro kód obsažený ve verzi překompilován JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="2f708-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="2f708-120">GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="2f708-121">Vrátí velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="2f708-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="2f708-122">GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="2f708-123">Vrátí pole ID, které identifikují všechny překompilován JIT verze zadané funkce, které jsou pořád ještě přidělená.</span><span class="sxs-lookup"><span data-stu-id="2f708-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="2f708-124">InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="2f708-125">Inicializuje aktuální vlákno s předstihem následné profiler volání rozhraní API ve stejném vlákně, takže se lze vyvarovat této zablokování.</span><span class="sxs-lookup"><span data-stu-id="2f708-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="2f708-126">RequestReJIT – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="2f708-127">Požadavků opětovnou kompilaci JIT všechny výskyty zadaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="2f708-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="2f708-128">RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="2f708-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="2f708-129">Vrátí všechny výskyty zadaných funkcí na jejich původní verze.</span><span class="sxs-lookup"><span data-stu-id="2f708-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f708-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f708-130">Remarks</span></span>  
 <span data-ttu-id="2f708-131">Implementuje metody CLR `ICorProfilerInfo4` rozhraní s použitím modelu volných vláken.</span><span class="sxs-lookup"><span data-stu-id="2f708-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="2f708-132">Každá metoda vrátí HRESULT indikuje úspěch nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="2f708-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="2f708-133">Seznam možných návratové kódy naleznete v souboru CorError.h.</span><span class="sxs-lookup"><span data-stu-id="2f708-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f708-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f708-134">Requirements</span></span>  
 <span data-ttu-id="2f708-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f708-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f708-136">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f708-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f708-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f708-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f708-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f708-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f708-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f708-139">See also</span></span>
- [<span data-ttu-id="2f708-140">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2f708-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2f708-141">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f708-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
