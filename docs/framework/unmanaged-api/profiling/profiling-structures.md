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
ms.workload: dotnet
ms.openlocfilehash: b29c63ea9dfbd69863aad1afa712444405be763e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-structures"></a><span data-ttu-id="20fa0-102">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="20fa0-102">Profiling Structures</span></span>
<span data-ttu-id="20fa0-103">Tato část popisuje nespravované struktury, které používá profilaci API.</span><span class="sxs-lookup"><span data-stu-id="20fa0-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20fa0-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="20fa0-104">In This Section</span></span>  
 [<span data-ttu-id="20fa0-105">COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="20fa0-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="20fa0-106">Poskytuje modul common language runtime s informacemi o odkaz na sestavení, které ho měli zvážit při procházení uzavření odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="20fa0-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="20fa0-107">COR_PRF_CODE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="20fa0-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="20fa0-108">Představuje jeden souvislý blok nativního kódu, které jsou uložené v paměti.</span><span class="sxs-lookup"><span data-stu-id="20fa0-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="20fa0-109">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="20fa0-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="20fa0-110">Obsahuje informace o instanci klauzule určité výjimky a jeho přidružené rámečku.</span><span class="sxs-lookup"><span data-stu-id="20fa0-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="20fa0-111">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="20fa0-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="20fa0-112">Poskytuje jedinečný reprezentace funkce kombinací jeho ID s ID jeho Rekompilované verze.</span><span class="sxs-lookup"><span data-stu-id="20fa0-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="20fa0-113">COR_PRF_FUNCTION_ARGUMENT_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="20fa0-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="20fa0-114">Představuje argumenty funkcí v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="20fa0-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="20fa0-115">COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="20fa0-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="20fa0-116">Představuje blok argumenty funkce souvisle uložené v pořadí zleva doprava v paměti.</span><span class="sxs-lookup"><span data-stu-id="20fa0-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="20fa0-117">COR_PRF_GC_GENERATION_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="20fa0-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="20fa0-118">Popisuje rozsah (blok) paměti, která probíhá uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="20fa0-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="20fa0-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="20fa0-119">Related Sections</span></span>  
 <span data-ttu-id="20fa0-120">COR_DEBUG_IL_TO_NATIVE_MAP –</span><span class="sxs-lookup"><span data-stu-id="20fa0-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="20fa0-121">COR_IL_MAP –</span><span class="sxs-lookup"><span data-stu-id="20fa0-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="20fa0-122">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="20fa0-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="20fa0-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="20fa0-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="20fa0-124">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="20fa0-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="20fa0-125">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="20fa0-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
