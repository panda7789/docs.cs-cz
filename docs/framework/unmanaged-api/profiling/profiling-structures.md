---
title: Struktury pro profilaci
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: c3bbc66079e05abf494ad112b8aa0ac68e3c3e2f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868106"
---
# <a name="profiling-structures"></a><span data-ttu-id="739db-102">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="739db-102">Profiling Structures</span></span>
<span data-ttu-id="739db-103">Tato část popisuje nespravované struktury, které používá profilování API.</span><span class="sxs-lookup"><span data-stu-id="739db-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="739db-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="739db-104">In This Section</span></span>  
 [<span data-ttu-id="739db-105">COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="739db-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="739db-106">Poskytuje modul CLR (Common Language Runtime) informace o referenčním sestavení, které by mělo být zváženo při provádění procházení uzavření odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="739db-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="739db-107">COR_PRF_CODE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="739db-107">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="739db-108">Představuje jeden souvislý blok nativního kódu uložený v paměti.</span><span class="sxs-lookup"><span data-stu-id="739db-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="739db-109">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="739db-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="739db-110">Ukládá informace o konkrétní instanci klauzule Exception a jejím přidruženém rámci.</span><span class="sxs-lookup"><span data-stu-id="739db-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="739db-111">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="739db-111">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="739db-112">Poskytuje jedinečné reprezentace funkce kombinací jejího ID s ID své znovu zkompilované verze.</span><span class="sxs-lookup"><span data-stu-id="739db-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="739db-113">COR_PRF_FUNCTION_ARGUMENT_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="739db-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="739db-114">Představuje argumenty funkce v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="739db-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="739db-115">COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="739db-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="739db-116">Představuje blok argumentů funkce uložených souvisle v pořadí v paměti zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="739db-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="739db-117">COR_PRF_GC_GENERATION_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="739db-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="739db-118">Popisuje rozsah (tj. blok) paměti, která přechází do uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="739db-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="739db-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="739db-119">Related Sections</span></span>  
 <span data-ttu-id="739db-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="739db-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="739db-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="739db-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="739db-122">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="739db-122">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="739db-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="739db-123">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="739db-124">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="739db-124">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="739db-125">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="739db-125">Profiling Enumerations</span></span>](profiling-enumerations.md)
