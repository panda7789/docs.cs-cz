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
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448002"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="eac3a-102">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eac3a-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="eac3a-103">Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí a informace o požadavcích.</span><span class="sxs-lookup"><span data-stu-id="eac3a-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="eac3a-104">.</span><span class="sxs-lookup"><span data-stu-id="eac3a-104">.</span></span> <span data-ttu-id="eac3a-105">Rozhraní `ICorProfilerInfo4` je rozšířením ostatních rozhraní `ICorProfilerInfo`.</span><span class="sxs-lookup"><span data-stu-id="eac3a-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="eac3a-106">Poskytuje nové metody pro podporu opětovné kompilace JIT (just-in-time), přidané v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="eac3a-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eac3a-107">Metody</span><span class="sxs-lookup"><span data-stu-id="eac3a-107">Methods</span></span>  
  
|<span data-ttu-id="eac3a-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-108">Method</span></span>|<span data-ttu-id="eac3a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="eac3a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eac3a-110">EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="eac3a-111">Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT a rekompilovány JIT.</span><span class="sxs-lookup"><span data-stu-id="eac3a-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="eac3a-112">EnumThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="eac3a-113">Získá enumerátor, který poskytuje metody pro sekvenční iteraci v kolekci všech spravovaných vláken v profilované procesu.</span><span class="sxs-lookup"><span data-stu-id="eac3a-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="eac3a-114">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="eac3a-115">Získá rozsahy nativního kódu přidruženého k Rekompilované verzi JIT zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="eac3a-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="eac3a-116">GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="eac3a-117">Mapuje ukazatel na instrukci spravovaného kódu pro rekompilovaný verzi zadané funkce JIT.</span><span class="sxs-lookup"><span data-stu-id="eac3a-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="eac3a-118">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="eac3a-119">Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v překompilované verzi zadané funkce JIT.</span><span class="sxs-lookup"><span data-stu-id="eac3a-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="eac3a-120">GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="eac3a-121">Vrací velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="eac3a-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="eac3a-122">GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="eac3a-123">Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny.</span><span class="sxs-lookup"><span data-stu-id="eac3a-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="eac3a-124">InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="eac3a-125">Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.</span><span class="sxs-lookup"><span data-stu-id="eac3a-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="eac3a-126">RequestReJIT – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="eac3a-127">Vyžádá rekompilaci JIT všech instancí zadaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="eac3a-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="eac3a-128">RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="eac3a-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="eac3a-129">Vrátí všechny výskyty zadaných funkcí do jejich původních verzí.</span><span class="sxs-lookup"><span data-stu-id="eac3a-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eac3a-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eac3a-130">Remarks</span></span>  
 <span data-ttu-id="eac3a-131">Modul CLR implementuje metody rozhraní `ICorProfilerInfo4` pomocí modelu s volnými vlákny.</span><span class="sxs-lookup"><span data-stu-id="eac3a-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="eac3a-132">Každá metoda vrátí hodnotu HRESULT, aby označovala úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="eac3a-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="eac3a-133">Seznam možných návratových kódů naleznete v souboru CorError. h.</span><span class="sxs-lookup"><span data-stu-id="eac3a-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eac3a-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eac3a-134">Requirements</span></span>  
 <span data-ttu-id="eac3a-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eac3a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eac3a-136">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eac3a-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eac3a-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eac3a-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eac3a-138">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eac3a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac3a-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eac3a-139">See also</span></span>

- [<span data-ttu-id="eac3a-140">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="eac3a-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="eac3a-141">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eac3a-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
