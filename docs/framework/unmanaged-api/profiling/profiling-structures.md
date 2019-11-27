---
title: Struktury pro profilaci
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 2f3e8cedcc498230311c0b52f7ecc1c2c4fc8ff1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447696"
---
# <a name="profiling-structures"></a><span data-ttu-id="f89ce-102">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f89ce-102">Profiling Structures</span></span>
<span data-ttu-id="f89ce-103">Tato část popisuje nespravované struktury, které používá profilování API.</span><span class="sxs-lookup"><span data-stu-id="f89ce-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f89ce-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f89ce-104">In This Section</span></span>  
 [<span data-ttu-id="f89ce-105">COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="f89ce-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="f89ce-106">Poskytuje modul CLR (Common Language Runtime) informace o referenčním sestavení, které by mělo být zváženo při provádění procházení uzavření odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="f89ce-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="f89ce-107">COR_PRF_CODE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="f89ce-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="f89ce-108">Představuje jeden souvislý blok nativního kódu uložený v paměti.</span><span class="sxs-lookup"><span data-stu-id="f89ce-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="f89ce-109">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="f89ce-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="f89ce-110">Ukládá informace o konkrétní instanci klauzule Exception a jejím přidruženém rámci.</span><span class="sxs-lookup"><span data-stu-id="f89ce-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="f89ce-111">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="f89ce-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="f89ce-112">Poskytuje jedinečné reprezentace funkce kombinací jejího ID s ID své znovu zkompilované verze.</span><span class="sxs-lookup"><span data-stu-id="f89ce-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="f89ce-113">COR_PRF_FUNCTION_ARGUMENT_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="f89ce-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="f89ce-114">Představuje argumenty funkce v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="f89ce-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="f89ce-115">COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="f89ce-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="f89ce-116">Představuje blok argumentů funkce uložených souvisle v pořadí v paměti zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="f89ce-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="f89ce-117">COR_PRF_GC_GENERATION_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="f89ce-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="f89ce-118">Popisuje rozsah (tj. blok) paměti, která přechází do uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f89ce-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f89ce-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f89ce-119">Related Sections</span></span>  
 <span data-ttu-id="f89ce-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="f89ce-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="f89ce-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="f89ce-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="f89ce-122">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="f89ce-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="f89ce-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f89ce-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="f89ce-124">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f89ce-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="f89ce-125">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f89ce-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
