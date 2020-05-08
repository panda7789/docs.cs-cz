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
ms.openlocfilehash: 7575be3f5074243b251c80b8dd5bdbb12e5d50fd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976320"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="3a6f8-102">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a6f8-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="3a6f8-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které používá ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a6f8-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a6f8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3a6f8-104">Methods</span></span>  
  
|<span data-ttu-id="3a6f8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3a6f8-105">Method</span></span>|<span data-ttu-id="3a6f8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3a6f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a6f8-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="3a6f8-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="3a6f8-108">Vytvoří kopii tohoto `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="3a6f8-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="3a6f8-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="3a6f8-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="3a6f8-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="3a6f8-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="3a6f8-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="3a6f8-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="3a6f8-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="3a6f8-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="3a6f8-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="3a6f8-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="3a6f8-114">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="3a6f8-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a6f8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a6f8-115">Remarks</span></span>  
 <span data-ttu-id="3a6f8-116">Následující enumerátory jsou odvozeny `ICorDebugEnum`z:</span><span class="sxs-lookup"><span data-stu-id="3a6f8-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="3a6f8-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="3a6f8-119">ICorDebugBlockingObjectEnum –</span><span class="sxs-lookup"><span data-stu-id="3a6f8-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="3a6f8-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="3a6f8-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="3a6f8-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="3a6f8-126">ICorDebugGCReferenceEnum –</span><span class="sxs-lookup"><span data-stu-id="3a6f8-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="3a6f8-127">ICorDebugGuidToTypeEnum –</span><span class="sxs-lookup"><span data-stu-id="3a6f8-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="3a6f8-128">ICorDebugHeapEnum –</span><span class="sxs-lookup"><span data-stu-id="3a6f8-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="3a6f8-129">ICorDebugHeapSegmentEnum –</span><span class="sxs-lookup"><span data-stu-id="3a6f8-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="3a6f8-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="3a6f8-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="3a6f8-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="3a6f8-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="3a6f8-138">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3a6f8-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a6f8-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a6f8-139">Requirements</span></span>  
 <span data-ttu-id="3a6f8-140">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a6f8-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a6f8-141">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a6f8-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a6f8-142">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a6f8-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a6f8-143">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a6f8-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6f8-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a6f8-144">See also</span></span>

- [<span data-ttu-id="3a6f8-145">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a6f8-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
