---
title: ICorDebugAppDomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19cf38920ed818dfbba9cd83bd64fdc408281e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="10594-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="10594-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="10594-103">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="10594-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="10594-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10594-105">Metody</span><span class="sxs-lookup"><span data-stu-id="10594-105">Methods</span></span>  
  
|<span data-ttu-id="10594-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="10594-106">Method</span></span>|<span data-ttu-id="10594-107">Popis</span><span class="sxs-lookup"><span data-stu-id="10594-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10594-108">Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="10594-109">Připojí ladicí program do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="10594-110">Enumerateassemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="10594-111">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="10594-112">Enumeratebreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="10594-113">Získá enumerátor pro všechny aktivní zarážky v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="10594-114">Enumeratesteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="10594-115">Získá enumerátor pro všechny aktivní steppers v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="10594-116">Getid – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="10594-117">Získá jedinečné ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="10594-118">Getmodulefrommetadatainterface – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="10594-119">Získá objekt ICorDebugModule s rozhraním daná metadata.</span><span class="sxs-lookup"><span data-stu-id="10594-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="10594-120">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="10594-121">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="10594-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="10594-123">Získá ukazatele rozhraní pro běžné domény aplikace language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="10594-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="10594-124">Getprocess – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="10594-125">Získá proces obsahující domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="10594-126">Isattached – metoda</span><span class="sxs-lookup"><span data-stu-id="10594-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="10594-127">Určuje, zda je ladicí program připojen do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="10594-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10594-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10594-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10594-129">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="10594-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10594-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10594-130">Requirements</span></span>  
 <span data-ttu-id="10594-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10594-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10594-132">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10594-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10594-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10594-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10594-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10594-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10594-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="10594-135">See Also</span></span>  
 [<span data-ttu-id="10594-136">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="10594-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
