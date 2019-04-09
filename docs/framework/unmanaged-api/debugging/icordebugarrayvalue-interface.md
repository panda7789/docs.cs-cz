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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168386"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="2bc35-102">ICorDebugArrayValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bc35-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="2bc35-103">Podtřída ICorDebugHeapValue, která představuje jednorozměrné nebo vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="2bc35-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bc35-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2bc35-104">Methods</span></span>  
  
|<span data-ttu-id="2bc35-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-105">Method</span></span>|<span data-ttu-id="2bc35-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2bc35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bc35-107">GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="2bc35-108">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="2bc35-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="2bc35-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="2bc35-110">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="2bc35-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="2bc35-111">GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="2bc35-112">Získá rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="2bc35-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="2bc35-113">GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="2bc35-114">Získá hodnotu představující daný prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="2bc35-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="2bc35-115">GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="2bc35-116">Získá prvek na dané pozici, zpracuje pole jako pole s nulovým základem, jednorozměrné.</span><span class="sxs-lookup"><span data-stu-id="2bc35-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="2bc35-117">GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="2bc35-118">Získá jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="2bc35-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="2bc35-119">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="2bc35-120">Získá počet dimenzí v poli.</span><span class="sxs-lookup"><span data-stu-id="2bc35-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="2bc35-121">HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc35-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="2bc35-122">Určuje, zda pole obsahuje základní indexy.</span><span class="sxs-lookup"><span data-stu-id="2bc35-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bc35-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bc35-123">Remarks</span></span>  
 `ICorDebugArrayValue` <span data-ttu-id="2bc35-124">podporuje jednorozměrné i vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="2bc35-124">supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bc35-125">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="2bc35-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc35-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bc35-126">Requirements</span></span>  
 <span data-ttu-id="2bc35-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bc35-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc35-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bc35-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bc35-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bc35-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2bc35-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2bc35-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2bc35-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bc35-131">See also</span></span>

- [<span data-ttu-id="2bc35-132">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bc35-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
