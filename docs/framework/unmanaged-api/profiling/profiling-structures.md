---
title: Struktury pro profilaci
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 229218cb15963846da91f688b0d2faacb20031c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000438"
---
# <a name="profiling-structures"></a><span data-ttu-id="3aecb-102">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3aecb-102">Profiling Structures</span></span>
<span data-ttu-id="3aecb-103">Tato část popisuje nespravované struktury, které používá profilování API.</span><span class="sxs-lookup"><span data-stu-id="3aecb-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3aecb-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3aecb-104">In This Section</span></span>  
 [<span data-ttu-id="3aecb-105">COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="3aecb-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="3aecb-106">Modul common language runtime poskytuje informace o referenční sestavení, byste měli zvážit při procházení uzavření odkaz sestavení.</span><span class="sxs-lookup"><span data-stu-id="3aecb-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="3aecb-107">COR_PRF_CODE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="3aecb-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="3aecb-108">Představuje jeden souvislý blok nativní kód uložen v paměti.</span><span class="sxs-lookup"><span data-stu-id="3aecb-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="3aecb-109">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="3aecb-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="3aecb-110">Ukládá informace o instanci klauzule specifickou výjimku a jeho přidružené rámce.</span><span class="sxs-lookup"><span data-stu-id="3aecb-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="3aecb-111">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="3aecb-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="3aecb-112">Poskytuje reprezentaci jedinečné funkce kombinací jeho ID, identifikátorem její překompilovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="3aecb-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="3aecb-113">COR_PRF_FUNCTION_ARGUMENT_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="3aecb-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="3aecb-114">Představuje argumenty funkce, v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="3aecb-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="3aecb-115">COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="3aecb-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="3aecb-116">Představuje blok argumentů funkce, které jsou uložena souvisle v pořadí zleva doprava v paměti.</span><span class="sxs-lookup"><span data-stu-id="3aecb-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="3aecb-117">COR_PRF_GC_GENERATION_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="3aecb-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="3aecb-118">Popisuje rozsahu (bloku) prochází uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3aecb-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3aecb-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3aecb-119">Related Sections</span></span>  
 <span data-ttu-id="3aecb-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="3aecb-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="3aecb-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="3aecb-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="3aecb-122">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="3aecb-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="3aecb-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3aecb-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="3aecb-124">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3aecb-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="3aecb-125">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3aecb-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
