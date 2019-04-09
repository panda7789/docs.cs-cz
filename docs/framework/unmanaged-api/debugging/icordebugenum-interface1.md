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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148808"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="7d366-102">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d366-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="7d366-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které jsou používány ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d366-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d366-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7d366-104">Methods</span></span>  
  
|<span data-ttu-id="7d366-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7d366-105">Method</span></span>|<span data-ttu-id="7d366-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7d366-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d366-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="7d366-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="7d366-108">Vytvoří kopii tohoto `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="7d366-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="7d366-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7d366-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="7d366-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="7d366-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="7d366-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="7d366-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="7d366-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="7d366-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="7d366-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="7d366-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="7d366-114">Přesune kurzor vpřed o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="7d366-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d366-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d366-115">Remarks</span></span>  
 <span data-ttu-id="7d366-116">Následující výčty jsou odvozeny z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="7d366-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="7d366-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="7d366-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="7d366-118">Icordebugassemblyenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="7d366-119">Icordebugblockingobjectenum –</span><span class="sxs-lookup"><span data-stu-id="7d366-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="7d366-120">Icordebugbreakpointenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="7d366-121">Icordebugchainenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="7d366-122">Icordebugcodeenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="7d366-123">Icordebugerrorinfoenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="7d366-124">Icordebugexceptionobjectcallstackenum –</span><span class="sxs-lookup"><span data-stu-id="7d366-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="7d366-125">Icordebugframeenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="7d366-126">Icordebuggcreferenceenum –</span><span class="sxs-lookup"><span data-stu-id="7d366-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="7d366-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="7d366-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="7d366-128">Icordebugheapenum –</span><span class="sxs-lookup"><span data-stu-id="7d366-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="7d366-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="7d366-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="7d366-130">Icordebugmoduleenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="7d366-131">Icordebugobjectenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="7d366-132">Icordebugprocessenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="7d366-133">Icordebugstepperenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="7d366-134">Icordebugthreadenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="7d366-135">Icordebugtypeenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="7d366-136">Icordebugvalueenum "–"</span><span class="sxs-lookup"><span data-stu-id="7d366-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="7d366-137">Icordebugvariablehomeenum –</span><span class="sxs-lookup"><span data-stu-id="7d366-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="7d366-138">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="7d366-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d366-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d366-139">Requirements</span></span>  
 <span data-ttu-id="7d366-140">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d366-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d366-141">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d366-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d366-142">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d366-142">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7d366-143">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7d366-143">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d366-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d366-144">See also</span></span>

- [<span data-ttu-id="7d366-145">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d366-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
