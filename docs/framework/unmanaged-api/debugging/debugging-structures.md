---
title: Struktury pro ladění
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: a18094fb2621478dbdb4bbf672df436234112ed0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793754"
---
# <a name="debugging-structures"></a><span data-ttu-id="9c68e-102">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="9c68e-102">Debugging Structures</span></span>

<span data-ttu-id="9c68e-103">Tato část popisuje nespravované struktury, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="9c68e-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9c68e-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9c68e-104">In This Section</span></span>
 <span data-ttu-id="9c68e-105">[Struktura CLRDATA_ADDRESS_RANGE](clrdata-address-range-structure.md) Definuje rozsah adres.</span><span class="sxs-lookup"><span data-stu-id="9c68e-105">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="9c68e-106">[Struktura CLRDATA_IL_ADDRESS_MAP](clrdata-il-address-map-structure.md) Definuje mapování IL na adresu.</span><span class="sxs-lookup"><span data-stu-id="9c68e-106">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="9c68e-107">[Struktura CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) Definuje verzi produktu modulu CLR (Common Language Runtime) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="9c68e-107">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="9c68e-108">[Struktura codechunkinfo –](codechunkinfo-structure.md) Představuje jeden blok kódu v paměti.</span><span class="sxs-lookup"><span data-stu-id="9c68e-108">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="9c68e-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Obsahuje informace o funkcích, které jsou aktuálně aktivní v rámečcích vlákna.</span><span class="sxs-lookup"><span data-stu-id="9c68e-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="9c68e-110">[Struktura COR_ARRAY_LAYOUT](cor-array-layout-structure.md) Poskytuje informace o rozložení objektu pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="9c68e-110">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="9c68e-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Obsahuje posuny, které se používají k mapování kódu jazyka MSIL (Microsoft Intermediate Language) do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="9c68e-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="9c68e-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Obsahuje informace o posunu pro rozsah kódu.</span><span class="sxs-lookup"><span data-stu-id="9c68e-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="9c68e-113">[Struktura COR_FIELD](cor-field-structure.md) Poskytuje informace o poli v objektu.</span><span class="sxs-lookup"><span data-stu-id="9c68e-113">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="9c68e-114">[Struktura COR_GC_REFERENCE](cor-gc-reference-structure.md) Obsahuje informace o objektu, který má být shromážděn z paměti.</span><span class="sxs-lookup"><span data-stu-id="9c68e-114">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="9c68e-115">[Struktura COR_HEAPINFO](cor-heapinfo-structure.md) Poskytuje obecné informace o haldě uvolňování paměti, včetně toho, zda je vyčíslitelné.</span><span class="sxs-lookup"><span data-stu-id="9c68e-115">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="9c68e-116">[Struktura COR_HEAPOBJECT](cor-heapobject-structure.md) Poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="9c68e-116">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="9c68e-117">[COR_IL_MAP](cor-il-map-structure.md) Určuje změny relativního posunu funkce.</span><span class="sxs-lookup"><span data-stu-id="9c68e-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="9c68e-118">[Struktura COR_SEGMENT](cor-segment-structure.md) Obsahuje informace o oblasti paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="9c68e-118">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="9c68e-119">[Struktura COR_TYPEID](cor-typeid-structure.md) Obsahuje identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="9c68e-119">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="9c68e-120">[Struktura COR_TYPE_LAYOUT](cor-type-layout-structure.md) Poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="9c68e-120">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="9c68e-121">[COR_VERSION](cor-version-structure.md) Ukládá standardní číslo verze se čtyřmi částmi modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="9c68e-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="9c68e-122">[Struktura CorDebugBlockingObject –](cordebugblockingobject-structure.md) Definuje objekt, který blokuje vlákno, a důvod, proč je vlákno blokované.</span><span class="sxs-lookup"><span data-stu-id="9c68e-122">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="9c68e-123">[Struktura CorDebugEHClause](cordebugehclause-structure.md) Představuje klauzuli zpracování výjimek (EH) pro danou část mezilehlého jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="9c68e-123">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="9c68e-124">[Struktura CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) Představuje informace o snímku zásobníku z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="9c68e-124">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="9c68e-125">[Struktura CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) Mapuje identifikátor GUID prostředí Windows Runtime na odpovídající objekt [ICorDebugType](icordebugtype-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9c68e-125">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="9c68e-126">[Struktura DacpGetModuleAddress](dacpgetmoduleaddress-structure.md) Definuje kontejner pro požadavek na adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="9c68e-126">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="9c68e-127">[Struktura DacpMethodDescData](dacpmethoddescdata-structure.md) Definuje přenosovou vyrovnávací paměť pro běhové informace metody.</span><span class="sxs-lookup"><span data-stu-id="9c68e-127">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="9c68e-128">[Struktura DacpModuleData](dacpmoduledata-structure.md) Definuje přenosovou vyrovnávací paměť pro běhové informace modulu.</span><span class="sxs-lookup"><span data-stu-id="9c68e-128">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="9c68e-129">[Struktura DacpReJitData](dacprejitdata-structure.md) Definuje základní informace o dané metodě instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="9c68e-129">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="9c68e-130">[Struktura StackTrace_SimpleContext](stacktrace-simplecontext-structure.md) Poskytuje jednoduchý kontext, který lze použít místo úplné `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="9c68e-130">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9c68e-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9c68e-131">Related Sections</span></span>

 [<span data-ttu-id="9c68e-132">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="9c68e-132">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="9c68e-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9c68e-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="9c68e-134">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="9c68e-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="9c68e-135">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="9c68e-135">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="9c68e-136">Ladění</span><span class="sxs-lookup"><span data-stu-id="9c68e-136">Debugging</span></span>](index.md)
