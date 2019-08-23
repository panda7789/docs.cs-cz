---
title: Rozhraní ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f838c9c2775023583b6879ea4c4a52727065114
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911267"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="756b7-102">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="756b7-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="756b7-103">Definuje základní rozhraní, ze kterého jsou `ICorDebug` odvozeny všechny události ladění.</span><span class="sxs-lookup"><span data-stu-id="756b7-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="756b7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="756b7-104">Methods</span></span>  
  
|<span data-ttu-id="756b7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="756b7-105">Method</span></span>|<span data-ttu-id="756b7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="756b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="756b7-107">GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="756b7-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="756b7-108">Určuje, jaký druh události tento `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="756b7-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="756b7-109">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="756b7-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="756b7-110">Získá vlákno, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="756b7-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="756b7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="756b7-111">Remarks</span></span>  
 <span data-ttu-id="756b7-112">Následující rozhraní jsou odvozena z `ICorDebugDebugEvent` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="756b7-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="756b7-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="756b7-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="756b7-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="756b7-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="756b7-115">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="756b7-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="756b7-116">Pokus o volání metody `QueryInterface` načtení `E_NOINTERFACE` ukazatele rozhraní pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="756b7-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="756b7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="756b7-117">Requirements</span></span>  
 <span data-ttu-id="756b7-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="756b7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="756b7-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="756b7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="756b7-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="756b7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="756b7-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="756b7-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756b7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="756b7-122">See also</span></span>

- [<span data-ttu-id="756b7-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="756b7-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="756b7-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="756b7-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
