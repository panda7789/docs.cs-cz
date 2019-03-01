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
ms.openlocfilehash: 73898bf5f4303d677787bae587a16f2f325dee9e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970841"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="8f810-102">ICorDebugArrayValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f810-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="8f810-103">Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="8f810-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f810-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8f810-104">Methods</span></span>  
  
|<span data-ttu-id="8f810-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-105">Method</span></span>|<span data-ttu-id="8f810-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8f810-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f810-107">GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="8f810-108">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="8f810-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="8f810-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="8f810-110">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="8f810-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="8f810-111">GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="8f810-112">Získá rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="8f810-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="8f810-113">GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="8f810-114">Získá hodnotu představující daný prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="8f810-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="8f810-115">GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="8f810-116">Získá prvek na dané pozici, zpracuje pole jako pole s nulovým základem, jednorozměrné.</span><span class="sxs-lookup"><span data-stu-id="8f810-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="8f810-117">GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="8f810-118">Získá jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="8f810-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="8f810-119">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="8f810-120">Získá počet dimenzí v poli.</span><span class="sxs-lookup"><span data-stu-id="8f810-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="8f810-121">HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="8f810-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="8f810-122">Určuje, zda pole obsahuje základní indexy.</span><span class="sxs-lookup"><span data-stu-id="8f810-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f810-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f810-123">Remarks</span></span>  
 <span data-ttu-id="8f810-124">`ICorDebugArrayValue` podporuje jednorozměrné i vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="8f810-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f810-125">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="8f810-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f810-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f810-126">Requirements</span></span>  
 <span data-ttu-id="8f810-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f810-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f810-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f810-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f810-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f810-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f810-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f810-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f810-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f810-131">See also</span></span>
- [<span data-ttu-id="8f810-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8f810-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
