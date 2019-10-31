---
title: ICorDebugArrayValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: e41bb5ca0fdd999692395239304f50a6f745a4f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088269"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="74333-102">ICorDebugArrayValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74333-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="74333-103">Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="74333-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74333-104">Metody</span><span class="sxs-lookup"><span data-stu-id="74333-104">Methods</span></span>  
  
|<span data-ttu-id="74333-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="74333-105">Method</span></span>|<span data-ttu-id="74333-106">Popis</span><span class="sxs-lookup"><span data-stu-id="74333-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74333-107">GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="74333-108">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="74333-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="74333-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="74333-110">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="74333-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="74333-111">GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="74333-112">Získá rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="74333-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="74333-113">GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="74333-114">Získá hodnotu reprezentující daný prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="74333-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="74333-115">GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="74333-116">Získá prvek na dané pozici, což zpracuje pole jako jednorozměrné jednorozměrné pole s nulovým základem.</span><span class="sxs-lookup"><span data-stu-id="74333-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="74333-117">GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="74333-118">Získá jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="74333-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="74333-119">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="74333-120">Získá počet rozměrů v poli.</span><span class="sxs-lookup"><span data-stu-id="74333-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="74333-121">HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="74333-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="74333-122">Určuje, zda pole obsahuje základní indexy.</span><span class="sxs-lookup"><span data-stu-id="74333-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74333-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74333-123">Remarks</span></span>  
 <span data-ttu-id="74333-124">`ICorDebugArrayValue` podporuje jak jednorozměrná, tak multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="74333-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74333-125">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="74333-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74333-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74333-126">Requirements</span></span>  
 <span data-ttu-id="74333-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74333-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74333-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74333-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74333-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="74333-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74333-130">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74333-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74333-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74333-131">See also</span></span>

- [<span data-ttu-id="74333-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="74333-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
