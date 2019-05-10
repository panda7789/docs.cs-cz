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
ms.openlocfilehash: eb3aca0713b8b11bdfaa23bf33c8e1a0b302e272
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606528"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="6811c-102">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6811c-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="6811c-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které jsou používány ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6811c-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6811c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6811c-104">Methods</span></span>  
  
|<span data-ttu-id="6811c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6811c-105">Method</span></span>|<span data-ttu-id="6811c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6811c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6811c-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="6811c-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="6811c-108">Vytvoří kopii tohoto `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="6811c-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="6811c-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="6811c-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="6811c-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="6811c-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="6811c-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="6811c-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="6811c-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="6811c-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="6811c-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="6811c-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="6811c-114">Přesune kurzor vpřed o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="6811c-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6811c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6811c-115">Remarks</span></span>  
 <span data-ttu-id="6811c-116">Následující výčty jsou odvozeny z `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="6811c-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="6811c-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="6811c-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="6811c-118">Icordebugassemblyenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="6811c-119">Icordebugblockingobjectenum –</span><span class="sxs-lookup"><span data-stu-id="6811c-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="6811c-120">Icordebugbreakpointenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="6811c-121">Icordebugchainenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="6811c-122">Icordebugcodeenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="6811c-123">Icordebugerrorinfoenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="6811c-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="6811c-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="6811c-125">Icordebugframeenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="6811c-126">Icordebuggcreferenceenum –</span><span class="sxs-lookup"><span data-stu-id="6811c-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="6811c-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="6811c-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="6811c-128">Icordebugheapenum –</span><span class="sxs-lookup"><span data-stu-id="6811c-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="6811c-129">Icordebugheapsegmentenum –</span><span class="sxs-lookup"><span data-stu-id="6811c-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="6811c-130">Icordebugmoduleenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="6811c-131">Icordebugobjectenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="6811c-132">Icordebugprocessenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="6811c-133">Icordebugstepperenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="6811c-134">Icordebugthreadenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="6811c-135">Icordebugtypeenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="6811c-136">Icordebugvalueenum "–"</span><span class="sxs-lookup"><span data-stu-id="6811c-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="6811c-137">Icordebugvariablehomeenum –</span><span class="sxs-lookup"><span data-stu-id="6811c-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="6811c-138">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="6811c-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6811c-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6811c-139">Requirements</span></span>  
 <span data-ttu-id="6811c-140">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6811c-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6811c-141">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6811c-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6811c-142">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6811c-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6811c-143">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6811c-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6811c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6811c-144">See also</span></span>

- [<span data-ttu-id="6811c-145">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6811c-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
