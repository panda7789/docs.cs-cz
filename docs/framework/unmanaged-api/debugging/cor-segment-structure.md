---
title: "COR_SEGMENT – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc7a749f92149d7f0f5725aec6d90d72e0582c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="9ea56-102">COR_SEGMENT – struktura</span><span class="sxs-lookup"><span data-stu-id="9ea56-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="9ea56-103">Obsahuje informace o oblasti spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ea56-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="9ea56-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9ea56-105">Members</span></span>  
  
|<span data-ttu-id="9ea56-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9ea56-106">Member</span></span>|<span data-ttu-id="9ea56-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9ea56-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="9ea56-108">Počáteční adresa oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="9ea56-109">Koncová adresa oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="9ea56-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) – člen výčtu určující generování oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="9ea56-111">Číslo haldy, ve kterém se nachází oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="9ea56-112">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="9ea56-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ea56-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ea56-113">Remarks</span></span>  
 <span data-ttu-id="9ea56-114">`COR_SEGMENTS` Struktura představuje oblast spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="9ea56-115">`COR_SEGMENTS`objekty jsou členy [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) kolekce objektu, který je naplněn volání[icordebugprocess5::enumerateheapregions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="9ea56-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="9ea56-116">`heap` Pole je číslo procesoru, který odpovídá haldě nehlásí.</span><span class="sxs-lookup"><span data-stu-id="9ea56-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="9ea56-117">Kolektory uvolňování paměti pracovních stanic jeho hodnota je vždy nula, protože pracovní stanice mají jenom jeden kolekce halda paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="9ea56-118">Pro Kolektory paměti serveru jeho hodnota odpovídá procesoru, který halda je připojen k.</span><span class="sxs-lookup"><span data-stu-id="9ea56-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="9ea56-119">Všimněte si, že může existovat více nebo méně uvolňování haldách, než je skutečný procesory z důvodu podrobnosti implementace systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9ea56-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ea56-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ea56-120">Requirements</span></span>  
 <span data-ttu-id="9ea56-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ea56-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ea56-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ea56-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ea56-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ea56-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ea56-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ea56-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea56-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ea56-125">See Also</span></span>  
 [<span data-ttu-id="9ea56-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="9ea56-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="9ea56-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="9ea56-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
