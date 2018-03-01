---
title: ICorDebugAppDomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aab18cb1d29931a58e64561f23d91ee4eb3a4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="101b8-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="101b8-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="101b8-103">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="101b8-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="101b8-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="101b8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="101b8-105">Methods</span></span>  
  
|<span data-ttu-id="101b8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-106">Method</span></span>|<span data-ttu-id="101b8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="101b8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="101b8-108">Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="101b8-109">Připojí ladicí program do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="101b8-110">EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="101b8-111">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="101b8-112">EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="101b8-113">Získá enumerátor pro všechny aktivní zarážky v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="101b8-114">EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="101b8-115">Získá enumerátor pro všechny aktivní steppers v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="101b8-116">GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="101b8-117">Získá jedinečné ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="101b8-118">GetModuleFromMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="101b8-119">Získá objekt ICorDebugModule s rozhraním daná metadata.</span><span class="sxs-lookup"><span data-stu-id="101b8-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="101b8-120">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="101b8-121">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="101b8-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="101b8-123">Získá ukazatele rozhraní pro běžné domény aplikace language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="101b8-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="101b8-124">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="101b8-125">Získá proces obsahující domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="101b8-126">IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="101b8-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="101b8-127">Určuje, zda je ladicí program připojen do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="101b8-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="101b8-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="101b8-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="101b8-129">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="101b8-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="101b8-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="101b8-130">Requirements</span></span>  
 <span data-ttu-id="101b8-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="101b8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="101b8-132">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="101b8-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="101b8-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="101b8-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="101b8-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="101b8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101b8-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="101b8-135">See Also</span></span>  
 [<span data-ttu-id="101b8-136">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="101b8-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
