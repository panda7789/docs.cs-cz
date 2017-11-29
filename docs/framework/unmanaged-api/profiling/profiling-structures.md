---
title: Struktury pro profilaci
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42762812c9d27073fac34b20df5011b386f05740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-structures"></a><span data-ttu-id="c8f42-102">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c8f42-102">Profiling Structures</span></span>
<span data-ttu-id="c8f42-103">Tato část popisuje nespravované struktury, které používá profilaci API.</span><span class="sxs-lookup"><span data-stu-id="c8f42-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8f42-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c8f42-104">In This Section</span></span>  
 [<span data-ttu-id="c8f42-105">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="c8f42-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="c8f42-106">Poskytuje modul common language runtime s informacemi o odkaz na sestavení, které ho měli zvážit při procházení uzavření odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="c8f42-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="c8f42-107">Cor_prf_code_info – struktura</span><span class="sxs-lookup"><span data-stu-id="c8f42-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="c8f42-108">Představuje jeden souvislý blok nativního kódu, které jsou uložené v paměti.</span><span class="sxs-lookup"><span data-stu-id="c8f42-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="c8f42-109">Cor_prf_ex_clause_info – struktura</span><span class="sxs-lookup"><span data-stu-id="c8f42-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="c8f42-110">Obsahuje informace o instanci klauzule určité výjimky a jeho přidružené rámečku.</span><span class="sxs-lookup"><span data-stu-id="c8f42-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="c8f42-111">Cor_prf_function – struktura</span><span class="sxs-lookup"><span data-stu-id="c8f42-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="c8f42-112">Poskytuje jedinečný reprezentace funkce kombinací jeho ID s ID jeho Rekompilované verze.</span><span class="sxs-lookup"><span data-stu-id="c8f42-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="c8f42-113">Cor_prf_function_argument_info – struktura</span><span class="sxs-lookup"><span data-stu-id="c8f42-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="c8f42-114">Představuje argumenty funkcí v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="c8f42-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="c8f42-115">Cor_prf_function_argument_range – struktura</span><span class="sxs-lookup"><span data-stu-id="c8f42-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="c8f42-116">Představuje blok argumenty funkce souvisle uložené v pořadí zleva doprava v paměti.</span><span class="sxs-lookup"><span data-stu-id="c8f42-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="c8f42-117">Cor_prf_gc_generation_range – struktura</span><span class="sxs-lookup"><span data-stu-id="c8f42-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="c8f42-118">Popisuje rozsah (blok) paměti, která probíhá uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c8f42-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8f42-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c8f42-119">Related Sections</span></span>  
 <span data-ttu-id="c8f42-120">COR_DEBUG_IL_TO_NATIVE_MAP –</span><span class="sxs-lookup"><span data-stu-id="c8f42-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="c8f42-121">COR_IL_MAP –</span><span class="sxs-lookup"><span data-stu-id="c8f42-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="c8f42-122">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="c8f42-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="c8f42-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c8f42-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="c8f42-124">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="c8f42-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="c8f42-125">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="c8f42-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
