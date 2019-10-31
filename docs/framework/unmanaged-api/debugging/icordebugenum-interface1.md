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
ms.openlocfilehash: 59dcb7ae6f27f8d049cd4dc2d313f7f1130fc503
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085266"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="1c70d-102">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c70d-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="1c70d-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které používá ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c70d-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c70d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1c70d-104">Methods</span></span>  
  
|<span data-ttu-id="1c70d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1c70d-105">Method</span></span>|<span data-ttu-id="1c70d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1c70d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c70d-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="1c70d-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="1c70d-108">Vytvoří kopii tohoto objektu `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="1c70d-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="1c70d-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="1c70d-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="1c70d-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="1c70d-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="1c70d-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="1c70d-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="1c70d-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="1c70d-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="1c70d-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="1c70d-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="1c70d-114">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="1c70d-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c70d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c70d-115">Remarks</span></span>  
 <span data-ttu-id="1c70d-116">Následující enumerátory jsou odvozeny z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="1c70d-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="1c70d-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="1c70d-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="1c70d-119">ICorDebugBlockingObjectEnum –</span><span class="sxs-lookup"><span data-stu-id="1c70d-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="1c70d-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="1c70d-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="1c70d-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="1c70d-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="1c70d-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="1c70d-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="1c70d-126">ICorDebugGCReferenceEnum –</span><span class="sxs-lookup"><span data-stu-id="1c70d-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="1c70d-127">ICorDebugGuidToTypeEnum –</span><span class="sxs-lookup"><span data-stu-id="1c70d-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="1c70d-128">ICorDebugHeapEnum –</span><span class="sxs-lookup"><span data-stu-id="1c70d-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="1c70d-129">ICorDebugHeapSegmentEnum –</span><span class="sxs-lookup"><span data-stu-id="1c70d-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="1c70d-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="1c70d-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="1c70d-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="1c70d-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="1c70d-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="1c70d-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="1c70d-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="1c70d-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="1c70d-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="1c70d-138">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1c70d-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c70d-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c70d-139">Requirements</span></span>  
 <span data-ttu-id="1c70d-140">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c70d-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c70d-141">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c70d-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c70d-142">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c70d-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c70d-143">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c70d-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c70d-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c70d-144">See also</span></span>

- [<span data-ttu-id="1c70d-145">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1c70d-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
