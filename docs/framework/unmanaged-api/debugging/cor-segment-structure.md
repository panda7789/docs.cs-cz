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
ms.openlocfilehash: faf1be65d308b223490f3ae67eed3d8a2b1688b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223066"
---
# <a name="corsegment-structure"></a><span data-ttu-id="b37c0-102">COR_SEGMENT – struktura</span><span class="sxs-lookup"><span data-stu-id="b37c0-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="b37c0-103">Obsahuje informace o oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="b37c0-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b37c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b37c0-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="b37c0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b37c0-105">Members</span></span>  
  
|<span data-ttu-id="b37c0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b37c0-106">Member</span></span>|<span data-ttu-id="b37c0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b37c0-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="b37c0-108">Počáteční adresa oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="b37c0-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="b37c0-109">Koncová adresa oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="b37c0-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="b37c0-110">A [cordebuggenerationtypes –](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) člen výčtu, která určuje generování oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="b37c0-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="b37c0-111">Číslo haldy, ve kterém se nachází oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="b37c0-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="b37c0-112">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="b37c0-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b37c0-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b37c0-113">Remarks</span></span>  
 <span data-ttu-id="b37c0-114">`COR_SEGMENTS` Struktura představuje oblast paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="b37c0-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  `COR_SEGMENTS` <span data-ttu-id="b37c0-115">objekty jsou členy [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) kolekci objektu, který je vyplněn volání [icordebugprocess5::enumerateheapregions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b37c0-115">objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="b37c0-116">`heap` Pole je číslo procesoru, které odpovídá haldy hlásí.</span><span class="sxs-lookup"><span data-stu-id="b37c0-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="b37c0-117">Pro kolekce uvolnění paměti pracovní stanice, jeho hodnota je vždy nula, protože mají pouze jednu haldě uvolňování paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="b37c0-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="b37c0-118">Pro kolekce uvolnění paměti serveru jeho hodnota odpovídá procesor, haldy je připojeno k.</span><span class="sxs-lookup"><span data-stu-id="b37c0-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="b37c0-119">Všimněte si, že může existovat více nebo méně kolekce paměti haldy, než je skutečný procesory z důvodu podrobnosti implementace systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b37c0-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b37c0-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b37c0-120">Requirements</span></span>  
 <span data-ttu-id="b37c0-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b37c0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b37c0-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b37c0-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b37c0-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b37c0-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b37c0-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b37c0-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b37c0-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b37c0-125">See also</span></span>

- [<span data-ttu-id="b37c0-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="b37c0-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b37c0-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="b37c0-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
