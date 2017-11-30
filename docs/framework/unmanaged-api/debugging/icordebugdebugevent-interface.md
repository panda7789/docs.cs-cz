---
title: "Rozhraní ICorDebugDebugEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4422b165f06b60dedff95fc3de58e5627db7fac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="9ab73-102">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="9ab73-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="9ab73-103">Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` odvozena ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="9ab73-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ab73-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9ab73-104">Methods</span></span>  
  
|<span data-ttu-id="9ab73-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ab73-105">Method</span></span>|<span data-ttu-id="9ab73-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9ab73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ab73-107">Metoda GetEventKind</span><span class="sxs-lookup"><span data-stu-id="9ab73-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="9ab73-108">Určuje, jaký druh událostí to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="9ab73-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="9ab73-109">Getthread – metoda</span><span class="sxs-lookup"><span data-stu-id="9ab73-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="9ab73-110">Získá vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="9ab73-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ab73-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ab73-111">Remarks</span></span>  
 <span data-ttu-id="9ab73-112">Následující rozhraní jsou odvozeny od `ICorDebugDebugEvent` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="9ab73-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="9ab73-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="9ab73-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="9ab73-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="9ab73-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="9ab73-115">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="9ab73-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="9ab73-116">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9ab73-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ab73-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ab73-117">Requirements</span></span>  
 <span data-ttu-id="9ab73-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ab73-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab73-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ab73-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ab73-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ab73-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ab73-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab73-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab73-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ab73-122">See Also</span></span>  
 [<span data-ttu-id="9ab73-123">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ab73-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9ab73-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="9ab73-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
