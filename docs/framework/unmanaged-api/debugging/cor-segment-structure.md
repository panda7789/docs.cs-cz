---
title: COR_SEGMENT – struktura
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aabf3ac4e51280bd847d145e15ad804d514ede2c
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274007"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="ab41b-102">COR_SEGMENT – struktura</span><span class="sxs-lookup"><span data-stu-id="ab41b-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="ab41b-103">Obsahuje informace o oblasti paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="ab41b-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab41b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab41b-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="ab41b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ab41b-105">Members</span></span>  
  
|<span data-ttu-id="ab41b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ab41b-106">Member</span></span>|<span data-ttu-id="ab41b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ab41b-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="ab41b-108">Počáteční adresa oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="ab41b-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="ab41b-109">Koncová adresa oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="ab41b-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="ab41b-110">Člen výčtu [CorDebugGenerationTypes –](cordebuggenerationtypes-enumeration.md) , který označuje generování oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="ab41b-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="ab41b-111">Číslo haldy, ve které se nachází oblast paměti.</span><span class="sxs-lookup"><span data-stu-id="ab41b-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="ab41b-112">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="ab41b-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab41b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab41b-113">Remarks</span></span>  
 <span data-ttu-id="ab41b-114">`COR_SEGMENTS` Struktura představuje oblast paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="ab41b-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="ab41b-115">`COR_SEGMENTS`objekty jsou členy objektu kolekce [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) , který je vyplněn voláním metody [ICorDebugProcess5:: EnumerateHeapRegions –](icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab41b-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="ab41b-116">`heap` Pole je číslo procesoru, které odpovídá vyhlášené haldě.</span><span class="sxs-lookup"><span data-stu-id="ab41b-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="ab41b-117">Pro kolekce uvolnění paměti pracovní stanice je jeho hodnota vždycky nula, protože pracovní stanice mají jenom jednu haldu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ab41b-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="ab41b-118">Pro sběrače paměti serveru odpovídá jeho hodnota procesoru, ke kterému je halda připojena.</span><span class="sxs-lookup"><span data-stu-id="ab41b-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="ab41b-119">Všimněte si, že může existovat více nebo méně hald uvolňování paměti, než kolik existuje skutečným procesorům z důvodu podrobností implementace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ab41b-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab41b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab41b-120">Requirements</span></span>  
 <span data-ttu-id="ab41b-121">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab41b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab41b-122">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab41b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab41b-123">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab41b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab41b-124">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab41b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab41b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab41b-125">See also</span></span>

- [<span data-ttu-id="ab41b-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="ab41b-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ab41b-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="ab41b-127">Debugging</span></span>](index.md)
