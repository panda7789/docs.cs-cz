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
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415322"
---
# <a name="debugging-structures"></a><span data-ttu-id="016cf-102">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="016cf-102">Debugging Structures</span></span>
<span data-ttu-id="016cf-103">Tato část popisuje nespravované struktury, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="016cf-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="016cf-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="016cf-104">In This Section</span></span>  
 [<span data-ttu-id="016cf-105">CLR_DEBUGGING_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="016cf-106">Určuje verzi modulu common language runtime (CLR) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="016cf-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="016cf-107">CodeChunkInfo – struktura 1</span><span class="sxs-lookup"><span data-stu-id="016cf-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="016cf-108">Představuje jediný neodkazovaný blok kódu v paměti.</span><span class="sxs-lookup"><span data-stu-id="016cf-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="016cf-109">CorDebugBlockingObject – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="016cf-110">Definuje objekt, který blokuje vlákno a důvod, proč je vlákno blokované.</span><span class="sxs-lookup"><span data-stu-id="016cf-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="016cf-111">CorDebugEHClause – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="016cf-112">Představuje výjimku zpracování – klauzule (EH) pro danou část (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="016cf-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="016cf-113">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="016cf-114">Představuje zásobník snímků informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="016cf-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="016cf-115">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="016cf-116">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID odpovídající [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="016cf-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="016cf-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="016cf-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="016cf-118">Obsahuje informace o funkcích, které jsou aktuálně aktivní vlákna snímků.</span><span class="sxs-lookup"><span data-stu-id="016cf-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="016cf-119">COR_ARRAY_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="016cf-120">Poskytuje informace o rozložení objektu array v paměti.</span><span class="sxs-lookup"><span data-stu-id="016cf-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="016cf-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="016cf-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="016cf-122">Obsahuje posuny, které se používají k mapování kód Microsoft intermediate language (MSIL) do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="016cf-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="016cf-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="016cf-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="016cf-124">Obsahuje informace o posunu pro celou řadu kódu.</span><span class="sxs-lookup"><span data-stu-id="016cf-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="016cf-125">COR_FIELD – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="016cf-126">Poskytuje informace o pole v objektu.</span><span class="sxs-lookup"><span data-stu-id="016cf-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="016cf-127">COR_GC_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="016cf-128">Obsahuje informace o objektu, který má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="016cf-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="016cf-129">COR_HEAPINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="016cf-130">Obsahuje obecné informace o haldě uvolňování paměti kolekce, včetně toho, zda je vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="016cf-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="016cf-131">COR_HEAPOBJECT – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="016cf-132">Poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="016cf-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="016cf-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="016cf-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="016cf-134">Určuje změny v relativním posunem funkce.</span><span class="sxs-lookup"><span data-stu-id="016cf-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="016cf-135">COR_SEGMENT – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="016cf-136">Obsahuje informace o oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="016cf-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="016cf-137">COR_TYPEID – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="016cf-138">Obsahuje identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="016cf-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="016cf-139">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="016cf-140">Poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="016cf-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="016cf-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="016cf-141">COR_VERSION</span></span>  
 <span data-ttu-id="016cf-142">Ukládá číslo standardní sestávající ze čtyř částí verze modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="016cf-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="016cf-143">StackTrace_SimpleContext – struktura</span><span class="sxs-lookup"><span data-stu-id="016cf-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="016cf-144">Poskytuje jednoduchý kontext, který jde použít místo úplné `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="016cf-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

 <span data-ttu-id="016cf-145">[Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definuje rozsah adres.</span><span class="sxs-lookup"><span data-stu-id="016cf-145">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>
 
 <span data-ttu-id="016cf-146">[Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definuje IL pro mapování adresy</span><span class="sxs-lookup"><span data-stu-id="016cf-146">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>
 
 <span data-ttu-id="016cf-147">[Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definuje kontejner pro žádost o adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="016cf-147">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

  
## <a name="related-sections"></a><span data-ttu-id="016cf-148">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="016cf-148">Related Sections</span></span>  
 [<span data-ttu-id="016cf-149">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="016cf-149">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="016cf-150">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="016cf-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="016cf-151">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="016cf-151">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="016cf-152">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="016cf-152">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="016cf-153">Ladění</span><span class="sxs-lookup"><span data-stu-id="016cf-153">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
