---
title: ICorDebugAppDomain Interface1
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
ms.openlocfilehash: 9588ac26c698a8369f1ae4be89af7440a2dd1de4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546303"
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="463b0-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="463b0-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="463b0-103">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="463b0-104">Toto rozhraní je podtřídou třídy icordebugcontroller –.</span><span class="sxs-lookup"><span data-stu-id="463b0-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="463b0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="463b0-105">Methods</span></span>  
  
|<span data-ttu-id="463b0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-106">Method</span></span>|<span data-ttu-id="463b0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="463b0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="463b0-108">Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="463b0-109">Ladicí program připojí k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="463b0-110">EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="463b0-111">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="463b0-112">EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="463b0-113">Získá enumerátor pro všechny zarážky aktivní v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="463b0-114">EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="463b0-115">Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="463b0-116">GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="463b0-117">Získá jedinečné ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="463b0-118">GetModuleFromMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="463b0-119">Získá objekt icordebugmodule – rozhraní daná metadata.</span><span class="sxs-lookup"><span data-stu-id="463b0-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="463b0-120">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="463b0-121">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="463b0-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="463b0-123">Získá ukazatel rozhraní common language runtime (CLR) aplikační doménu.</span><span class="sxs-lookup"><span data-stu-id="463b0-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="463b0-124">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="463b0-125">Získá proces obsahující domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="463b0-126">IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="463b0-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="463b0-127">Určuje, zda ladicí program je připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="463b0-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="463b0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="463b0-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="463b0-129">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="463b0-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="463b0-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="463b0-130">Requirements</span></span>  
 <span data-ttu-id="463b0-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="463b0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="463b0-132">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="463b0-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="463b0-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="463b0-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="463b0-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="463b0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463b0-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="463b0-135">See also</span></span>
- [<span data-ttu-id="463b0-136">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="463b0-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
