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
ms.openlocfilehash: 9fca75ae59b95a226b51768b3e1bfb220d9926f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500959"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="529ed-102">COR_PRF_FUNCTION_ARGUMENT_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="529ed-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="529ed-103">Představuje argumenty funkce v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="529ed-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="529ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="529ed-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="529ed-105">Členové</span><span class="sxs-lookup"><span data-stu-id="529ed-105">Members</span></span>  
  
|<span data-ttu-id="529ed-106">Člen</span><span class="sxs-lookup"><span data-stu-id="529ed-106">Member</span></span>|<span data-ttu-id="529ed-107">Description</span><span class="sxs-lookup"><span data-stu-id="529ed-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="529ed-108">Počet bloků argumentů.</span><span class="sxs-lookup"><span data-stu-id="529ed-108">The number of blocks of arguments.</span></span> <span data-ttu-id="529ed-109">To znamená, že tato hodnota je počet [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) struktur v `ranges` poli.</span><span class="sxs-lookup"><span data-stu-id="529ed-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="529ed-110">Celková velikost všech argumentů.</span><span class="sxs-lookup"><span data-stu-id="529ed-110">The total size of all arguments.</span></span> <span data-ttu-id="529ed-111">Jinými slovy je tato hodnota součtem délek argumentů.</span><span class="sxs-lookup"><span data-stu-id="529ed-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="529ed-112">Pole `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktur, z nichž každý představuje jeden blok argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="529ed-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="529ed-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="529ed-113">Remarks</span></span>  
 <span data-ttu-id="529ed-114">Funkce může mít mnoho argumentů.</span><span class="sxs-lookup"><span data-stu-id="529ed-114">A function may have many arguments.</span></span> <span data-ttu-id="529ed-115">Tyto argumenty nemusí být uloženy souvisle v paměti.</span><span class="sxs-lookup"><span data-stu-id="529ed-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="529ed-116">Můžete mít blok tří argumentů na jednom místě, blok dvou argumentů na jiném místě a konečný blok jednoho argumentu na jiném místě.</span><span class="sxs-lookup"><span data-stu-id="529ed-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="529ed-117">Tyto argumenty jsou všechny pro stejnou funkci. jsou právě uloženy na různých místech.</span><span class="sxs-lookup"><span data-stu-id="529ed-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="529ed-118">`COR_PRF_FUNCTION_ARGUMENT_INFO`Struktura představuje všechny argumenty jediné funkce.</span><span class="sxs-lookup"><span data-stu-id="529ed-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="529ed-119">Používá pole k odkazování na všechny bloky argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="529ed-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="529ed-120">Pro jedinou funkci tedy máte jedinou `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturu, která odkazuje na více `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktur, každý z nich odkazuje na jeden nebo více argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="529ed-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="529ed-121">Argumenty, které jsou uloženy v registrech, jsou přerozděleny do paměti pro sestavení struktur.</span><span class="sxs-lookup"><span data-stu-id="529ed-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="529ed-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="529ed-122">Requirements</span></span>  
 <span data-ttu-id="529ed-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="529ed-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="529ed-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="529ed-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="529ed-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="529ed-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="529ed-126">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="529ed-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529ed-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="529ed-127">See also</span></span>

- [<span data-ttu-id="529ed-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="529ed-128">Profiling Structures</span></span>](profiling-structures.md)
