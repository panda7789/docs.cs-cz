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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645614"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="fbbc4-102">ICorDebugArrayValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbbc4-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="fbbc4-103">Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fbbc4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fbbc4-104">Methods</span></span>  
  
|<span data-ttu-id="fbbc4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-105">Method</span></span>|<span data-ttu-id="fbbc4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fbbc4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fbbc4-107">GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="fbbc4-108">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="fbbc4-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="fbbc4-110">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="fbbc4-111">GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="fbbc4-112">Získá rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="fbbc4-113">GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="fbbc4-114">Získá hodnotu představující daný prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="fbbc4-115">GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="fbbc4-116">Získá prvek na dané pozici, zpracuje pole jako pole s nulovým základem, jednorozměrné.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="fbbc4-117">GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="fbbc4-118">Získá jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="fbbc4-119">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="fbbc4-120">Získá počet dimenzí v poli.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="fbbc4-121">HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="fbbc4-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="fbbc4-122">Určuje, zda pole obsahuje základní indexy.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbbc4-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbbc4-123">Remarks</span></span>  
 <span data-ttu-id="fbbc4-124">`ICorDebugArrayValue` podporuje jednorozměrné i vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbbc4-125">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbbc4-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbbc4-126">Requirements</span></span>  
 <span data-ttu-id="fbbc4-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbbc4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbbc4-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbbc4-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbbc4-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbbc4-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbbc4-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbbc4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbc4-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbbc4-131">See also</span></span>

- [<span data-ttu-id="fbbc4-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fbbc4-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
