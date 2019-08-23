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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b25c47e101ad0fb8e8cbdbb2718a41c9be6c0c22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931988"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="72969-102">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72969-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="72969-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které používá ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="72969-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72969-104">Metody</span><span class="sxs-lookup"><span data-stu-id="72969-104">Methods</span></span>  
  
|<span data-ttu-id="72969-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="72969-105">Method</span></span>|<span data-ttu-id="72969-106">Popis</span><span class="sxs-lookup"><span data-stu-id="72969-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72969-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="72969-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="72969-108">Vytvoří kopii tohoto `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="72969-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="72969-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="72969-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="72969-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="72969-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="72969-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="72969-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="72969-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="72969-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="72969-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="72969-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="72969-114">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="72969-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72969-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72969-115">Remarks</span></span>  
 <span data-ttu-id="72969-116">Následující enumerátory jsou odvozeny `ICorDebugEnum`z:</span><span class="sxs-lookup"><span data-stu-id="72969-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="72969-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="72969-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="72969-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="72969-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="72969-119">ICorDebugBlockingObjectEnum –</span><span class="sxs-lookup"><span data-stu-id="72969-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="72969-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="72969-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="72969-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="72969-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="72969-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="72969-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="72969-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="72969-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="72969-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="72969-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="72969-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="72969-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="72969-126">ICorDebugGCReferenceEnum –</span><span class="sxs-lookup"><span data-stu-id="72969-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="72969-127">ICorDebugGuidToTypeEnum –</span><span class="sxs-lookup"><span data-stu-id="72969-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="72969-128">ICorDebugHeapEnum –</span><span class="sxs-lookup"><span data-stu-id="72969-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="72969-129">ICorDebugHeapSegmentEnum –</span><span class="sxs-lookup"><span data-stu-id="72969-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="72969-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="72969-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="72969-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="72969-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="72969-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="72969-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="72969-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="72969-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="72969-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="72969-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="72969-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="72969-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="72969-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="72969-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="72969-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="72969-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="72969-138">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="72969-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72969-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72969-139">Requirements</span></span>  
 <span data-ttu-id="72969-140">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72969-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72969-141">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72969-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72969-142">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72969-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72969-143">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72969-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72969-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72969-144">See also</span></span>

- [<span data-ttu-id="72969-145">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="72969-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
