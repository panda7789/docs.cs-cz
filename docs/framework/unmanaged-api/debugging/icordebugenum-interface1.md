---
title: ICorDebugEnum Interface1
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
ms.openlocfilehash: a4659bbc9c2e3c71a6cf85e51a06bee4f789356b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422302"
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="a5c6d-102">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="a5c6d-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="a5c6d-103">Slouží jako abstraktní základní rozhraní pro výčty, které jsou používány ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5c6d-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5c6d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a5c6d-104">Methods</span></span>  
  
|<span data-ttu-id="a5c6d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a5c6d-105">Method</span></span>|<span data-ttu-id="a5c6d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a5c6d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5c6d-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="a5c6d-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="a5c6d-108">Vytvoří kopii tohoto `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="a5c6d-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="a5c6d-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="a5c6d-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="a5c6d-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="a5c6d-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="a5c6d-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="a5c6d-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="a5c6d-112">Posune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="a5c6d-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="a5c6d-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="a5c6d-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="a5c6d-114">Přesune kurzor dál o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="a5c6d-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5c6d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5c6d-115">Remarks</span></span>  
 <span data-ttu-id="a5c6d-116">Následující výčty odvozena od `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="a5c6d-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="a5c6d-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="a5c6d-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="a5c6d-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="a5c6d-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-122">Icordebugcodeenum "–"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="a5c6d-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="a5c6d-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="a5c6d-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="a5c6d-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="a5c6d-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="a5c6d-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="a5c6d-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="a5c6d-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="a5c6d-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="a5c6d-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="a5c6d-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="a5c6d-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="a5c6d-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="a5c6d-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="a5c6d-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="a5c6d-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="a5c6d-138">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a5c6d-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c6d-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5c6d-139">Requirements</span></span>  
 <span data-ttu-id="a5c6d-140">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5c6d-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c6d-141">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5c6d-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5c6d-142">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5c6d-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5c6d-143">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c6d-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c6d-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5c6d-144">See Also</span></span>  
 [<span data-ttu-id="a5c6d-145">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a5c6d-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
