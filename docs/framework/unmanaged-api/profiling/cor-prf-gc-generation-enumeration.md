---
title: COR_PRF_GC_GENERATION – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74e70f58600205d44a9ba052981b2cc67b3a44ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753818"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="a27de-102">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="a27de-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="a27de-103">Identifikuje uvolnění paměti generace.</span><span class="sxs-lookup"><span data-stu-id="a27de-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a27de-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="a27de-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a27de-105">Members</span></span>  
  
|<span data-ttu-id="a27de-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a27de-106">Member</span></span>|<span data-ttu-id="a27de-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a27de-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="a27de-108">Objekt se uloží jako 0. generace.</span><span class="sxs-lookup"><span data-stu-id="a27de-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="a27de-109">Objekt se uloží jako 1. generace.</span><span class="sxs-lookup"><span data-stu-id="a27de-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="a27de-110">Objekt se uloží jako 2. generace.</span><span class="sxs-lookup"><span data-stu-id="a27de-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="a27de-111">Objekt se uloží ve velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="a27de-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a27de-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a27de-112">Remarks</span></span>  
 <span data-ttu-id="a27de-113">Systému uvolňování paměti zlepšuje výkon správy paměti dělicí objekty do generací podle věku.</span><span class="sxs-lookup"><span data-stu-id="a27de-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="a27de-114">Uvolňování paměti aktuálně používá tři generace číslované 0, 1 a 2 plus zvláštní haldy segment, který se používá pro velké objekty.</span><span class="sxs-lookup"><span data-stu-id="a27de-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="a27de-115">Objekty, jejichž velikost je větší než konkrétní hodnoty jsou uloženy v velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="a27de-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="a27de-116">Další přidělené objekty se začínají patřící do 0. generace.</span><span class="sxs-lookup"><span data-stu-id="a27de-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="a27de-117">Všechny objekty, které existují, jakmile dojde k uvolnění paměti generace 0 jsou povýšeny do generace 1.</span><span class="sxs-lookup"><span data-stu-id="a27de-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="a27de-118">Objekty, které existují, jakmile dojde k uvolnění paměti v generaci 1 přesunout do 2. generace.</span><span class="sxs-lookup"><span data-stu-id="a27de-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="a27de-119">Použití generace znamená, že má systému uvolňování paměti pro práci s pouze podmnožinu přidělených objektů v daný okamžik.</span><span class="sxs-lookup"><span data-stu-id="a27de-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="a27de-120">`COR_PRF_GC_GENERATION` Výčet je používán [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="a27de-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a27de-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a27de-121">Requirements</span></span>  
 <span data-ttu-id="a27de-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a27de-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a27de-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a27de-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a27de-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a27de-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a27de-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a27de-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27de-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a27de-126">See also</span></span>

- [<span data-ttu-id="a27de-127">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a27de-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
