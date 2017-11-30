---
title: "Struktury pro ladění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0293a20f5f735dd38b1d167ebc5057f645fa011a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-structures"></a><span data-ttu-id="f41c4-102">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="f41c4-102">Debugging Structures</span></span>
<span data-ttu-id="f41c4-103">Tato část popisuje nespravované struktury, která používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f41c4-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f41c4-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f41c4-104">In This Section</span></span>  
 [<span data-ttu-id="f41c4-105">Clr_debugging_version – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="f41c4-106">Definuje verze produktu common language runtime (CLR) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="f41c4-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="f41c4-107">Codechunkinfo – – Struktura1</span><span class="sxs-lookup"><span data-stu-id="f41c4-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="f41c4-108">Představuje jeden blok kódu v paměti.</span><span class="sxs-lookup"><span data-stu-id="f41c4-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="f41c4-109">Cordebugblockingobject – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="f41c4-110">Definuje objekt, který je blokování vlákna a důvod, proč je blokován vlákno.</span><span class="sxs-lookup"><span data-stu-id="f41c4-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="f41c4-111">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="f41c4-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="f41c4-112">Představuje výjimku zpracování (EH) klauzuli pro určitou část převodní jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="f41c4-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="f41c4-113">Cordebugexceptionobjectstackframe – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="f41c4-114">Představuje zásobníku rámce informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="f41c4-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="f41c4-115">Cordebugexceptionobjectstackframe – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="f41c4-116">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID do její odpovídající [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="f41c4-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="f41c4-117">COR_ACTIVE_FUNCTION –</span><span class="sxs-lookup"><span data-stu-id="f41c4-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="f41c4-118">Obsahuje informace o funkcích, které jsou momentálně aktivní v podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="f41c4-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="f41c4-119">Cor_array_layout – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="f41c4-120">Poskytuje informace o rozložení objektu pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="f41c4-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="f41c4-121">COR_DEBUG_IL_TO_NATIVE_MAP –</span><span class="sxs-lookup"><span data-stu-id="f41c4-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="f41c4-122">Obsahuje posuny, které se používají pro mapování kódu Microsoft (MSIL intermediate language) do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="f41c4-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="f41c4-123">COR_DEBUG_STEP_RANGE –</span><span class="sxs-lookup"><span data-stu-id="f41c4-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="f41c4-124">Obsahuje informace o posunu pro řadu kódu.</span><span class="sxs-lookup"><span data-stu-id="f41c4-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="f41c4-125">Cor_field – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="f41c4-126">Poskytuje informace o pole v objektu.</span><span class="sxs-lookup"><span data-stu-id="f41c4-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="f41c4-127">Cor_gc_reference – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="f41c4-128">Obsahuje informace o objekt, který má být uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f41c4-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="f41c4-129">Cor_heapinfo – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="f41c4-130">Poskytuje obecné informace o kolekci halda paměti, včetně toho, jestli je vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="f41c4-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="f41c4-131">Cor_heapobject – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="f41c4-132">Poskytuje informace o objekt na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="f41c4-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="f41c4-133">COR_IL_MAP –</span><span class="sxs-lookup"><span data-stu-id="f41c4-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="f41c4-134">Určuje změny v relativní posun funkce.</span><span class="sxs-lookup"><span data-stu-id="f41c4-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="f41c4-135">Cor_segment – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="f41c4-136">Obsahuje informace o oblasti spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="f41c4-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="f41c4-137">Cor_typeid – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="f41c4-138">Obsahuje identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="f41c4-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="f41c4-139">Cor_type_layout – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="f41c4-140">Poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="f41c4-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="f41c4-141">COR_VERSION –</span><span class="sxs-lookup"><span data-stu-id="f41c4-141">COR_VERSION</span></span>  
 <span data-ttu-id="f41c4-142">Ukládá číslo standardní sestávající ze čtyř částí verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f41c4-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="f41c4-143">Stacktrace_simplecontext – struktura</span><span class="sxs-lookup"><span data-stu-id="f41c4-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="f41c4-144">Poskytuje jednoduché kontext, který jde použít místo úplné `CONTEXT` struktura.</span><span class="sxs-lookup"><span data-stu-id="f41c4-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f41c4-145">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f41c4-145">Related Sections</span></span>  
 [<span data-ttu-id="f41c4-146">Ladění tříd typu coclass</span><span class="sxs-lookup"><span data-stu-id="f41c4-146">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="f41c4-147">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="f41c4-147">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="f41c4-148">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="f41c4-148">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="f41c4-149">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="f41c4-149">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="f41c4-150">Ladění</span><span class="sxs-lookup"><span data-stu-id="f41c4-150">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
