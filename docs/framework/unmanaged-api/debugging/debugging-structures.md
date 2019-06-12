---
title: Struktury pro ladění
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45a4b5c2a65ae7e4c01ffc3977875e598d076557
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025927"
---
# <a name="debugging-structures"></a><span data-ttu-id="e4c77-102">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="e4c77-102">Debugging Structures</span></span>

<span data-ttu-id="e4c77-103">Tato část popisuje nespravované struktury, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e4c77-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e4c77-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e4c77-104">In This Section</span></span>
 <span data-ttu-id="e4c77-105">[Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definuje rozsah adres.</span><span class="sxs-lookup"><span data-stu-id="e4c77-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="e4c77-106">[Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definuje IL pro mapování adresy</span><span class="sxs-lookup"><span data-stu-id="e4c77-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="e4c77-107">[Clr_debugging_version – struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Určuje verzi modulu common language runtime (CLR) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="e4c77-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="e4c77-108">[Codechunkinfo – struktura](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) představuje jediný neodkazovaný blok kódu v paměti.</span><span class="sxs-lookup"><span data-stu-id="e4c77-108">[CodeChunkInfo Structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="e4c77-109">[Cor_active_function –](cor-active-function-structure.md) obsahuje informace o funkcích, které jsou aktuálně aktivní vlákna snímků.</span><span class="sxs-lookup"><span data-stu-id="e4c77-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="e4c77-110">[Cor_array_layout – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) poskytuje informace o rozložení objektu array v paměti.</span><span class="sxs-lookup"><span data-stu-id="e4c77-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="e4c77-111">[Cor_debug_il_to_native_map –](cor-debug-il-to-native-map-structure.md) obsahuje kód posuny, které se používají k mapování jazyk Microsoft intermediate language (MSIL) do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e4c77-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="e4c77-112">[Cor_debug_step_range –](cor-debug-step-range-structure.md) obsahuje informace o posunu pro celou řadu kódu.</span><span class="sxs-lookup"><span data-stu-id="e4c77-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="e4c77-113">[Cor_field – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) poskytuje informace o pole v objektu.</span><span class="sxs-lookup"><span data-stu-id="e4c77-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="e4c77-114">[Cor_gc_reference – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obsahuje informace o objektu, který má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="e4c77-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="e4c77-115">[Cor_heapinfo – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) poskytuje obecné informace o haldě uvolňování paměti kolekce, včetně toho, zda je vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="e4c77-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="e4c77-116">[Cor_heapobject – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="e4c77-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="e4c77-117">[Cor_il_map –](cor-il-map-structure.md) určuje změny v relativním posunem funkce.</span><span class="sxs-lookup"><span data-stu-id="e4c77-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="e4c77-118">[Cor_segment – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) obsahuje informace o oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="e4c77-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="e4c77-119">[Cor_typeid – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) obsahuje identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="e4c77-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="e4c77-120">[Cor_type_layout – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="e4c77-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="e4c77-121">[Cor_version –](cor-version-structure.md) ukládá číslo standardní sestávající ze čtyř částí verze modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e4c77-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="e4c77-122">[Cordebugblockingobject – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) definuje objekt, který blokuje vlákno a důvod, proč je vlákno blokované.</span><span class="sxs-lookup"><span data-stu-id="e4c77-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="e4c77-123">[Struktura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) představuje klauzuli výjimka zpracování (EH) pro danou část (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="e4c77-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="e4c77-124">[Cordebugexceptionobjectstackframe – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) představuje zásobník snímků informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="e4c77-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="e4c77-125">[Cordebugguidtotypemapping – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) identifikátor GUID Windows Runtime se mapuje na jeho odpovídající [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="e4c77-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="e4c77-126">[Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definuje kontejner pro žádost o adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="e4c77-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="e4c77-127">[Struktura DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) definuje přenos vyrovnávací paměť pro informace o modulu runtime metody.</span><span class="sxs-lookup"><span data-stu-id="e4c77-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="e4c77-128">[Struktura DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) definuje přenos vyrovnávací paměť pro informace o modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e4c77-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="e4c77-129">[Struktura DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) definuje základních informací o dané metody instrumentována profileru.</span><span class="sxs-lookup"><span data-stu-id="e4c77-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="e4c77-130">[Stacktrace_simplecontext – struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) poskytuje jednoduché kontext, který jde použít místo úplné `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="e4c77-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e4c77-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e4c77-131">Related Sections</span></span>

 [<span data-ttu-id="e4c77-132">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="e4c77-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="e4c77-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e4c77-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="e4c77-134">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="e4c77-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="e4c77-135">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="e4c77-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="e4c77-136">Ladění</span><span class="sxs-lookup"><span data-stu-id="e4c77-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
