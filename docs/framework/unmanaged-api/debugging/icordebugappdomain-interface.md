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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996187"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="b1192-102">ICorDebugAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1192-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="b1192-103">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="b1192-104">Toto rozhraní je podtřídou třídy icordebugcontroller –.</span><span class="sxs-lookup"><span data-stu-id="b1192-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1192-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b1192-105">Methods</span></span>  
  
|<span data-ttu-id="b1192-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-106">Method</span></span>|<span data-ttu-id="b1192-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b1192-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1192-108">Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="b1192-109">Ladicí program připojí k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="b1192-110">EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="b1192-111">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="b1192-112">EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="b1192-113">Získá enumerátor pro všechny zarážky aktivní v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="b1192-114">EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="b1192-115">Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="b1192-116">GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="b1192-117">Získá jedinečné ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="b1192-118">GetModuleFromMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="b1192-119">Získá objekt icordebugmodule – rozhraní daná metadata.</span><span class="sxs-lookup"><span data-stu-id="b1192-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="b1192-120">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="b1192-121">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="b1192-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="b1192-123">Získá ukazatel rozhraní common language runtime (CLR) aplikační doménu.</span><span class="sxs-lookup"><span data-stu-id="b1192-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="b1192-124">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="b1192-125">Získá proces obsahující domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="b1192-126">IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="b1192-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="b1192-127">Určuje, zda ladicí program je připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1192-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1192-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1192-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1192-129">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="b1192-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1192-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1192-130">Requirements</span></span>  
 <span data-ttu-id="b1192-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1192-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1192-132">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1192-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1192-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1192-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1192-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1192-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1192-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1192-135">See also</span></span>

- [<span data-ttu-id="b1192-136">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b1192-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
