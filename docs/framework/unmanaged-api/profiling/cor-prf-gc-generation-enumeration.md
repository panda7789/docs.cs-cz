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
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867206"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="64e51-102">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="64e51-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="64e51-103">Identifikuje generování kolekce uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="64e51-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64e51-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="64e51-105">Členové</span><span class="sxs-lookup"><span data-stu-id="64e51-105">Members</span></span>  
  
|<span data-ttu-id="64e51-106">Člen</span><span class="sxs-lookup"><span data-stu-id="64e51-106">Member</span></span>|<span data-ttu-id="64e51-107">Popis</span><span class="sxs-lookup"><span data-stu-id="64e51-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="64e51-108">Objekt je uložen jako generace 0.</span><span class="sxs-lookup"><span data-stu-id="64e51-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="64e51-109">Objekt je uložen jako generace 1.</span><span class="sxs-lookup"><span data-stu-id="64e51-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="64e51-110">Objekt je uložen jako generace 2.</span><span class="sxs-lookup"><span data-stu-id="64e51-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="64e51-111">Objekt je uložen v haldě velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="64e51-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64e51-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64e51-112">Remarks</span></span>  
 <span data-ttu-id="64e51-113">Systém uvolňování paměti vylepšuje výkon správy paměti vydělením objektů do generací na základě stáří.</span><span class="sxs-lookup"><span data-stu-id="64e51-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="64e51-114">Systém uvolňování paměti aktuálně používá tři generace, očíslované 0, 1 a 2, a navíc speciální segment haldy, který se používá pro velké objekty.</span><span class="sxs-lookup"><span data-stu-id="64e51-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="64e51-115">Objekty, jejichž velikost je větší než konkrétní hodnota, jsou uloženy v haldě velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="64e51-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="64e51-116">Ostatní přidělené objekty začínají mimo generaci 0.</span><span class="sxs-lookup"><span data-stu-id="64e51-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="64e51-117">Všechny objekty, které existují po uvolnění paměti, jsou v generaci 0 povýšeny na generaci 1.</span><span class="sxs-lookup"><span data-stu-id="64e51-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="64e51-118">Objekty, které existují po uvolnění paměti, dojde v 1. generaci do generace 2.</span><span class="sxs-lookup"><span data-stu-id="64e51-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="64e51-119">Použití generací znamená, že systém uvolňování paměti musí v jednom okamžiku pracovat pouze s podmnožinou přidělených objektů.</span><span class="sxs-lookup"><span data-stu-id="64e51-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="64e51-120">`COR_PRF_GC_GENERATION` výčet používá struktura [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="64e51-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e51-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64e51-121">Requirements</span></span>  
 <span data-ttu-id="64e51-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64e51-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e51-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="64e51-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64e51-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="64e51-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64e51-125">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64e51-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e51-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64e51-126">See also</span></span>

- [<span data-ttu-id="64e51-127">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="64e51-127">Profiling Enumerations</span></span>](profiling-enumerations.md)
