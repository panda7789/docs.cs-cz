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
ms.openlocfilehash: 58d11e9084f53c69f2656b4f0ee6bc7d2cc4ae21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495863"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="81d67-102">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81d67-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="81d67-103">Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí a informace o požadavcích.</span><span class="sxs-lookup"><span data-stu-id="81d67-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="81d67-104">.</span><span class="sxs-lookup"><span data-stu-id="81d67-104">.</span></span> <span data-ttu-id="81d67-105">`ICorProfilerInfo4`Rozhraní je rozšířením ostatních `ICorProfilerInfo` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81d67-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="81d67-106">Poskytuje nové metody pro podporu opětovné kompilace JIT (just-in-time), přidané v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="81d67-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81d67-107">Metody</span><span class="sxs-lookup"><span data-stu-id="81d67-107">Methods</span></span>  
  
|<span data-ttu-id="81d67-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-108">Method</span></span>|<span data-ttu-id="81d67-109">Description</span><span class="sxs-lookup"><span data-stu-id="81d67-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81d67-110">EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="81d67-111">Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT a rekompilovány JIT.</span><span class="sxs-lookup"><span data-stu-id="81d67-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="81d67-112">EnumThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="81d67-113">Získá enumerátor, který poskytuje metody pro sekvenční iteraci v kolekci všech spravovaných vláken v profilované procesu.</span><span class="sxs-lookup"><span data-stu-id="81d67-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="81d67-114">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="81d67-115">Získá rozsahy nativního kódu přidruženého k Rekompilované verzi JIT zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="81d67-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="81d67-116">GetFunctionFromIP2 – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="81d67-117">Mapuje ukazatel na instrukci spravovaného kódu pro rekompilovaný verzi zadané funkce JIT.</span><span class="sxs-lookup"><span data-stu-id="81d67-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="81d67-118">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="81d67-119">Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v překompilované verzi zadané funkce JIT.</span><span class="sxs-lookup"><span data-stu-id="81d67-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="81d67-120">GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="81d67-121">Vrací velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="81d67-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="81d67-122">GetReJITIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="81d67-123">Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny.</span><span class="sxs-lookup"><span data-stu-id="81d67-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="81d67-124">InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="81d67-125">Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.</span><span class="sxs-lookup"><span data-stu-id="81d67-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="81d67-126">RequestReJIT – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="81d67-127">Vyžádá rekompilaci JIT všech instancí zadaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="81d67-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="81d67-128">RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="81d67-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="81d67-129">Vrátí všechny výskyty zadaných funkcí do jejich původních verzí.</span><span class="sxs-lookup"><span data-stu-id="81d67-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d67-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81d67-130">Remarks</span></span>  
 <span data-ttu-id="81d67-131">CLR implementuje metody `ICorProfilerInfo4` rozhraní pomocí modelu s volnými vlákny.</span><span class="sxs-lookup"><span data-stu-id="81d67-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="81d67-132">Každá metoda vrátí hodnotu HRESULT, aby označovala úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="81d67-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="81d67-133">Seznam možných návratových kódů naleznete v souboru CorError. h.</span><span class="sxs-lookup"><span data-stu-id="81d67-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d67-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81d67-134">Requirements</span></span>  
 <span data-ttu-id="81d67-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d67-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d67-136">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="81d67-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="81d67-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="81d67-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81d67-138">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d67-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d67-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81d67-139">See also</span></span>

- [<span data-ttu-id="81d67-140">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="81d67-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="81d67-141">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81d67-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
