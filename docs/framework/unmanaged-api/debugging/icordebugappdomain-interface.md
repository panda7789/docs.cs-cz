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
ms.openlocfilehash: 9abcb765357a0f305ae5acae77a4a13b07a003a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134686"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="66919-102">ICorDebugAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66919-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="66919-103">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="66919-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="66919-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66919-105">Metody</span><span class="sxs-lookup"><span data-stu-id="66919-105">Methods</span></span>  
  
|<span data-ttu-id="66919-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="66919-106">Method</span></span>|<span data-ttu-id="66919-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66919-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66919-108">Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="66919-109">Připojí ladicí program k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="66919-110">EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="66919-111">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="66919-112">EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="66919-113">Získá enumerátor pro všechny aktivní zarážky v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="66919-114">EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="66919-115">Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="66919-116">GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="66919-117">Získá jedinečné ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="66919-118">GetModuleFromMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="66919-119">Získá objekt ICorDebugModule se zadaným rozhraním metadat.</span><span class="sxs-lookup"><span data-stu-id="66919-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="66919-120">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="66919-121">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="66919-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="66919-123">Načte ukazatel rozhraní do aplikační domény modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="66919-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="66919-124">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="66919-125">Získá proces obsahující doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="66919-126">IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="66919-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="66919-127">Určuje, zda je ladicí program připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="66919-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66919-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66919-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66919-129">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="66919-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66919-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66919-130">Requirements</span></span>  
 <span data-ttu-id="66919-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66919-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66919-132">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66919-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66919-133">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66919-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66919-134">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66919-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66919-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66919-135">See also</span></span>

- [<span data-ttu-id="66919-136">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="66919-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
