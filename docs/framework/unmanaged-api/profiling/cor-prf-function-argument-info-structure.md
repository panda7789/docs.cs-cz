---
title: COR_PRF_FUNCTION_ARGUMENT_INFO – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293ad30ebf47ca8684d158b1ae1772ab245d7981
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163108"
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="90ae9-102">COR_PRF_FUNCTION_ARGUMENT_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="90ae9-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="90ae9-103">Představuje argumenty funkce, v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="90ae9-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ae9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90ae9-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="90ae9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="90ae9-105">Members</span></span>  
  
|<span data-ttu-id="90ae9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="90ae9-106">Member</span></span>|<span data-ttu-id="90ae9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="90ae9-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="90ae9-108">Počet bloků argumentů.</span><span class="sxs-lookup"><span data-stu-id="90ae9-108">The number of blocks of arguments.</span></span> <span data-ttu-id="90ae9-109">To znamená, že tato hodnota je počet [cor_prf_function_argument_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktur v `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="90ae9-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="90ae9-110">Celková velikost všech argumentů.</span><span class="sxs-lookup"><span data-stu-id="90ae9-110">The total size of all arguments.</span></span> <span data-ttu-id="90ae9-111">Jinými slovy tato hodnota je součet délek argumentů.</span><span class="sxs-lookup"><span data-stu-id="90ae9-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="90ae9-112">Pole `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, z nichž každý představuje jeden blok argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="90ae9-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90ae9-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90ae9-113">Remarks</span></span>  
 <span data-ttu-id="90ae9-114">Funkce může mít velký počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="90ae9-114">A function may have many arguments.</span></span> <span data-ttu-id="90ae9-115">Tyto argumenty nemusí uložena souvisle v paměti.</span><span class="sxs-lookup"><span data-stu-id="90ae9-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="90ae9-116">Můžete mít blok tři argumenty na jednom místě, blok dva argumenty na jiném místě a posledního bloku s jedním argumentem na jiném místě.</span><span class="sxs-lookup"><span data-stu-id="90ae9-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="90ae9-117">Všechny tyto argumenty jsou pro stejnou funkci. právě jsou uloženy na různých místech.</span><span class="sxs-lookup"><span data-stu-id="90ae9-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="90ae9-118">`COR_PRF_FUNCTION_ARGUMENT_INFO` Struktura představuje všechny argumenty jedné funkce.</span><span class="sxs-lookup"><span data-stu-id="90ae9-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="90ae9-119">Pole se používá k odkazování všechny bloky argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="90ae9-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="90ae9-120">Ano, pro jednu funkci, máte jediný `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturu, která odkazuje na více `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, každý z nich odkazuje na jeden nebo více argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="90ae9-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="90ae9-121">Argumenty, které jsou uloženy v registrech, jsou přesahovat do paměti k vytvoření struktury.</span><span class="sxs-lookup"><span data-stu-id="90ae9-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ae9-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90ae9-122">Requirements</span></span>  
 <span data-ttu-id="90ae9-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ae9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ae9-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="90ae9-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="90ae9-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90ae9-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="90ae9-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="90ae9-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="90ae9-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90ae9-127">See also</span></span>

- [<span data-ttu-id="90ae9-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="90ae9-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
