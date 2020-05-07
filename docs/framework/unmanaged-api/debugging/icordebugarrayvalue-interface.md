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
ms.openlocfilehash: bd1e86b83c43af20604416f158ab9e74f399821b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894968"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="15da4-102">ICorDebugArrayValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15da4-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="15da4-103">Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="15da4-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15da4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="15da4-104">Methods</span></span>  
  
|<span data-ttu-id="15da4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-105">Method</span></span>|<span data-ttu-id="15da4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="15da4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15da4-107">GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="15da4-108">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="15da4-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="15da4-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="15da4-110">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="15da4-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="15da4-111">GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="15da4-112">Získá rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="15da4-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="15da4-113">GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="15da4-114">Získá hodnotu reprezentující daný prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="15da4-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="15da4-115">GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="15da4-116">Získá prvek na dané pozici, což zpracuje pole jako jednorozměrné jednorozměrné pole s nulovým základem.</span><span class="sxs-lookup"><span data-stu-id="15da4-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="15da4-117">GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="15da4-118">Získá jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="15da4-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="15da4-119">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="15da4-120">Získá počet rozměrů v poli.</span><span class="sxs-lookup"><span data-stu-id="15da4-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="15da4-121">HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="15da4-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="15da4-122">Určuje, zda pole obsahuje základní indexy.</span><span class="sxs-lookup"><span data-stu-id="15da4-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15da4-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15da4-123">Remarks</span></span>  
 <span data-ttu-id="15da4-124">`ICorDebugArrayValue`podporuje jak jednorozměrná, tak multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="15da4-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15da4-125">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="15da4-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15da4-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15da4-126">Requirements</span></span>  
 <span data-ttu-id="15da4-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15da4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15da4-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15da4-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15da4-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15da4-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15da4-130">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15da4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15da4-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="15da4-131">See also</span></span>

- [<span data-ttu-id="15da4-132">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15da4-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
