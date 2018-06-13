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
ms.openlocfilehash: f452a3324365fb23e1affc11dbdb2ede15346010
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462439"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="840c1-102">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="840c1-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="840c1-103">Poskytuje metody, které profilery kódu se používají ke komunikaci s modul common language runtime (CLR) k řízení sledování událostí a informace o požadavku.</span><span class="sxs-lookup"><span data-stu-id="840c1-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="840c1-104">.</span><span class="sxs-lookup"><span data-stu-id="840c1-104">.</span></span> <span data-ttu-id="840c1-105">`ICorProfilerInfo4` Rozhraní je rozšířením dalších `ICorProfilerInfo` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="840c1-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="840c1-106">Poskytuje nové metody pro podporu rekompilace v běhu (JIT), přidán do [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="840c1-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="840c1-107">Metody</span><span class="sxs-lookup"><span data-stu-id="840c1-107">Methods</span></span>  
  
|<span data-ttu-id="840c1-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-108">Method</span></span>|<span data-ttu-id="840c1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="840c1-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="840c1-110">EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="840c1-111">Vrátí enumerátor pro všechny funkce, které byly dříve kompilována a překompilovat JIT.</span><span class="sxs-lookup"><span data-stu-id="840c1-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="840c1-112">EnumThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="840c1-113">Získá enumerátor, který poskytuje metody pro postupně iteraci prostřednictvím kolekce všech spravovaných vláken v procesu PROFILOVANÉHO.</span><span class="sxs-lookup"><span data-stu-id="840c1-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="840c1-114">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="840c1-115">Získá rozsah nativního kódu přidružené verze překompilovat JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="840c1-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="840c1-116">GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="840c1-117">Ukazatel instrukce spravovaného kódu se mapuje na verzi překompilovat JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="840c1-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="840c1-118">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="840c1-119">Získá mapu od společnosti Microsoft (MSIL intermediate language) posune do nativní posunutí pro kód obsažené ve verzi překompilovat JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="840c1-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="840c1-120">GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="840c1-121">Vrátí velikost zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="840c1-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="840c1-122">GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="840c1-123">Vrátí pole ID, které identifikují všechny překompilovat JIT verze zadaná funkce, které jsou pořád ještě přidělená.</span><span class="sxs-lookup"><span data-stu-id="840c1-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="840c1-124">InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="840c1-125">Inicializuje aktuální vlákno předem následné profileru, které volání rozhraní API ve stejném vlákně, takže se vyhnout této vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="840c1-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="840c1-126">RequestReJIT – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="840c1-127">Požadavky JIT rekompilace všech instancí určených funkcí.</span><span class="sxs-lookup"><span data-stu-id="840c1-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="840c1-128">RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="840c1-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="840c1-129">Vrátí všechny výskyty určených funkcí jejich původní verze.</span><span class="sxs-lookup"><span data-stu-id="840c1-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="840c1-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="840c1-130">Remarks</span></span>  
 <span data-ttu-id="840c1-131">Modul CLR implementuje metody `ICorProfilerInfo4` rozhraní pomocí modelu podprocesy.</span><span class="sxs-lookup"><span data-stu-id="840c1-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="840c1-132">Každá metoda vrátí HRESULT indikující úspěch nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="840c1-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="840c1-133">Seznam možných návratové kódy naleznete v souboru CorError.h.</span><span class="sxs-lookup"><span data-stu-id="840c1-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="840c1-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="840c1-134">Requirements</span></span>  
 <span data-ttu-id="840c1-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="840c1-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="840c1-136">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="840c1-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="840c1-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="840c1-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="840c1-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="840c1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="840c1-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="840c1-139">See Also</span></span>  
 [<span data-ttu-id="840c1-140">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="840c1-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="840c1-141">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="840c1-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
