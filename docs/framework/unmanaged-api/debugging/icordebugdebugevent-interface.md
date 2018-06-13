---
title: Rozhraní ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a2543a9629c60fde2b2f14c11898ba3e9df3c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419309"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="4c0e4-102">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4c0e4-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="4c0e4-103">Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` odvozena ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="4c0e4-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c0e4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4c0e4-104">Methods</span></span>  
  
|<span data-ttu-id="4c0e4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4c0e4-105">Method</span></span>|<span data-ttu-id="4c0e4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4c0e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c0e4-107">GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="4c0e4-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="4c0e4-108">Určuje, jaký druh událostí to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="4c0e4-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="4c0e4-109">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="4c0e4-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="4c0e4-110">Získá vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="4c0e4-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c0e4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c0e4-111">Remarks</span></span>  
 <span data-ttu-id="4c0e4-112">Následující rozhraní jsou odvozeny od `ICorDebugDebugEvent` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="4c0e4-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="4c0e4-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4c0e4-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="4c0e4-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4c0e4-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="4c0e4-115">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="4c0e4-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="4c0e4-116">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4c0e4-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0e4-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c0e4-117">Requirements</span></span>  
 <span data-ttu-id="4c0e4-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c0e4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0e4-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c0e4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c0e4-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c0e4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c0e4-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c0e4-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0e4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c0e4-122">See Also</span></span>  
 [<span data-ttu-id="4c0e4-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4c0e4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4c0e4-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="4c0e4-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
