---
title: ICorDebugEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: cc5598f9cbec4b97bb75f83fb18ccf8742904272
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783010"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="b90ff-102">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b90ff-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="b90ff-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které používá ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="b90ff-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b90ff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b90ff-104">Methods</span></span>  
  
|<span data-ttu-id="b90ff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b90ff-105">Method</span></span>|<span data-ttu-id="b90ff-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b90ff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b90ff-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="b90ff-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="b90ff-108">Vytvoří kopii tohoto objektu `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="b90ff-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="b90ff-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="b90ff-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="b90ff-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="b90ff-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="b90ff-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="b90ff-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="b90ff-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="b90ff-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="b90ff-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="b90ff-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="b90ff-114">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="b90ff-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b90ff-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b90ff-115">Remarks</span></span>  
 <span data-ttu-id="b90ff-116">Následující enumerátory jsou odvozeny z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="b90ff-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="b90ff-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="b90ff-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="b90ff-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="b90ff-119">ICorDebugBlockingObjectEnum –</span><span class="sxs-lookup"><span data-stu-id="b90ff-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="b90ff-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="b90ff-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="b90ff-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="b90ff-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="b90ff-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="b90ff-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="b90ff-126">ICorDebugGCReferenceEnum –</span><span class="sxs-lookup"><span data-stu-id="b90ff-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="b90ff-127">ICorDebugGuidToTypeEnum –</span><span class="sxs-lookup"><span data-stu-id="b90ff-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="b90ff-128">ICorDebugHeapEnum –</span><span class="sxs-lookup"><span data-stu-id="b90ff-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="b90ff-129">ICorDebugHeapSegmentEnum –</span><span class="sxs-lookup"><span data-stu-id="b90ff-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="b90ff-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="b90ff-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="b90ff-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="b90ff-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="b90ff-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="b90ff-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="b90ff-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="b90ff-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="b90ff-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="b90ff-138">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b90ff-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b90ff-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b90ff-139">Requirements</span></span>  
 <span data-ttu-id="b90ff-140">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b90ff-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b90ff-141">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b90ff-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b90ff-142">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b90ff-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b90ff-143">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b90ff-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90ff-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b90ff-144">See also</span></span>

- [<span data-ttu-id="b90ff-145">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b90ff-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
