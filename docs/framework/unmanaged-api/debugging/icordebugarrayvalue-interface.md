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
ms.openlocfilehash: 0944f3379c18cba56ab65fe40a5b94a64d8a8991
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778193"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="6b7b8-102">ICorDebugArrayValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b7b8-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="6b7b8-103">Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b7b8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6b7b8-104">Methods</span></span>  
  
|<span data-ttu-id="6b7b8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-105">Method</span></span>|<span data-ttu-id="6b7b8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6b7b8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b7b8-107">GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="6b7b8-108">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="6b7b8-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="6b7b8-110">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="6b7b8-111">GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="6b7b8-112">Získá rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="6b7b8-113">GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="6b7b8-114">Získá hodnotu reprezentující daný prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="6b7b8-115">GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="6b7b8-116">Získá prvek na dané pozici, což zpracuje pole jako jednorozměrné jednorozměrné pole s nulovým základem.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="6b7b8-117">GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="6b7b8-118">Získá jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="6b7b8-119">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="6b7b8-120">Získá počet rozměrů v poli.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="6b7b8-121">HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="6b7b8-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="6b7b8-122">Určuje, zda pole obsahuje základní indexy.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b7b8-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b7b8-123">Remarks</span></span>  
 <span data-ttu-id="6b7b8-124">`ICorDebugArrayValue` podporuje jak jednorozměrná, tak multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b7b8-125">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6b7b8-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b7b8-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b7b8-126">Requirements</span></span>  
 <span data-ttu-id="6b7b8-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b7b8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b7b8-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b7b8-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b7b8-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6b7b8-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b7b8-130">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b7b8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7b8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b7b8-131">See also</span></span>

- [<span data-ttu-id="6b7b8-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6b7b8-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
