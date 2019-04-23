---
title: ICorDebugAppDomain – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40619aa40f9924d94c82541eb8d30790e774a675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141495"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="cc7c4-102">ICorDebugAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc7c4-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="cc7c4-103">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="cc7c4-104">Toto rozhraní je podtřídou třídy icordebugcontroller –.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc7c4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cc7c4-105">Methods</span></span>  
  
|<span data-ttu-id="cc7c4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-106">Method</span></span>|<span data-ttu-id="cc7c4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cc7c4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc7c4-108">Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="cc7c4-109">Ladicí program připojí k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-110">EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="cc7c4-111">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-112">EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="cc7c4-113">Získá enumerátor pro všechny zarážky aktivní v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-114">EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="cc7c4-115">Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-116">GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="cc7c4-117">Získá jedinečné ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-118">GetModuleFromMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="cc7c4-119">Získá objekt icordebugmodule – rozhraní daná metadata.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="cc7c4-120">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="cc7c4-121">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="cc7c4-123">Získá ukazatel rozhraní common language runtime (CLR) aplikační doménu.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-124">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="cc7c4-125">Získá proces obsahující domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="cc7c4-126">IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7c4-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="cc7c4-127">Určuje, zda ladicí program je připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc7c4-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc7c4-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc7c4-129">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="cc7c4-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7c4-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc7c4-130">Requirements</span></span>  
 <span data-ttu-id="cc7c4-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7c4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7c4-132">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc7c4-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc7c4-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc7c4-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc7c4-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7c4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7c4-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc7c4-135">See also</span></span>

- [<span data-ttu-id="cc7c4-136">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cc7c4-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
