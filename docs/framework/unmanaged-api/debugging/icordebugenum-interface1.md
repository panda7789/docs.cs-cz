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
ms.openlocfilehash: 9afaeebfdb98a404ea53b0b5ec147f8c8104e14d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148808"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="b8de9-102">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8de9-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="b8de9-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které jsou používány ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8de9-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8de9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b8de9-104">Methods</span></span>  
  
|<span data-ttu-id="b8de9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b8de9-105">Method</span></span>|<span data-ttu-id="b8de9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b8de9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8de9-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="b8de9-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="b8de9-108">Vytvoří kopii tohoto `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="b8de9-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="b8de9-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="b8de9-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="b8de9-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="b8de9-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="b8de9-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="b8de9-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="b8de9-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="b8de9-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="b8de9-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="b8de9-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="b8de9-114">Přesune kurzor vpřed o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="b8de9-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8de9-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8de9-115">Remarks</span></span>  
 <span data-ttu-id="b8de9-116">Následující výčty jsou odvozeny z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="b8de9-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="b8de9-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="b8de9-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-118">Icordebugassemblyenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="b8de9-119">Icordebugblockingobjectenum –</span><span class="sxs-lookup"><span data-stu-id="b8de9-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="b8de9-120">Icordebugbreakpointenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-121">Icordebugchainenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-122">Icordebugcodeenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-123">Icordebugerrorinfoenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="b8de9-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="b8de9-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="b8de9-125">Icordebugframeenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="b8de9-126">Icordebuggcreferenceenum –</span><span class="sxs-lookup"><span data-stu-id="b8de9-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="b8de9-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="b8de9-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="b8de9-128">Icordebugheapenum –</span><span class="sxs-lookup"><span data-stu-id="b8de9-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="b8de9-129">Icordebugheapsegmentenum –</span><span class="sxs-lookup"><span data-stu-id="b8de9-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="b8de9-130">Icordebugmoduleenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-131">Icordebugobjectenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-132">Icordebugprocessenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-133">Icordebugstepperenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-134">Icordebugthreadenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-135">Icordebugtypeenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="b8de9-136">Icordebugvalueenum "–"</span><span class="sxs-lookup"><span data-stu-id="b8de9-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="b8de9-137">Icordebugvariablehomeenum –</span><span class="sxs-lookup"><span data-stu-id="b8de9-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="b8de9-138">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="b8de9-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8de9-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8de9-139">Requirements</span></span>  
 <span data-ttu-id="b8de9-140">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8de9-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8de9-141">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8de9-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8de9-142">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8de9-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8de9-143">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8de9-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8de9-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8de9-144">See also</span></span>

- [<span data-ttu-id="b8de9-145">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b8de9-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
