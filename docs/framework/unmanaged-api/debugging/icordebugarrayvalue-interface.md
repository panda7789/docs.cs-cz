---
title: ICorDebugArrayValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35169f0dd2ca71400d3aebddf9d5e2ae6b72be07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="894d6-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="894d6-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="894d6-103">Podtřídou třídy icordebugheapvalue –, který představuje jednorozměrná nebo multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="894d6-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="894d6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="894d6-104">Methods</span></span>  
  
|<span data-ttu-id="894d6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-105">Method</span></span>|<span data-ttu-id="894d6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="894d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="894d6-107">GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="894d6-108">Získá základní index Každá dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="894d6-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="894d6-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="894d6-110">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="894d6-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="894d6-111">GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="894d6-112">Získá rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="894d6-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="894d6-113">GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="894d6-114">Získá hodnotu představující daného elementu v poli.</span><span class="sxs-lookup"><span data-stu-id="894d6-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="894d6-115">GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="894d6-116">Získá element na dané pozici, považuje pole jako pole jednorozměrná, počítáno od nuly.</span><span class="sxs-lookup"><span data-stu-id="894d6-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="894d6-117">GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="894d6-118">Získá jednoduchý typ elementů v poli.</span><span class="sxs-lookup"><span data-stu-id="894d6-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="894d6-119">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="894d6-120">Získá počet dimenzí v poli.</span><span class="sxs-lookup"><span data-stu-id="894d6-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="894d6-121">HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="894d6-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="894d6-122">Určuje, zda pole má základní indexy.</span><span class="sxs-lookup"><span data-stu-id="894d6-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="894d6-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="894d6-123">Remarks</span></span>  
 <span data-ttu-id="894d6-124">`ICorDebugArrayValue`podporuje jednorozměrná i vícerozměrných polí.</span><span class="sxs-lookup"><span data-stu-id="894d6-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="894d6-125">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="894d6-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="894d6-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="894d6-126">Requirements</span></span>  
 <span data-ttu-id="894d6-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="894d6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="894d6-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="894d6-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="894d6-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="894d6-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="894d6-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="894d6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894d6-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="894d6-131">See Also</span></span>  
 [<span data-ttu-id="894d6-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="894d6-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
