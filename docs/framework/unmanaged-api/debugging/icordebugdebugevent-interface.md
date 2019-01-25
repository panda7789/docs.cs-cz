---
title: Rozhraní ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e9a7efadea7960eadccfa1637489ed14bbeb26f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576314"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="ab2db-102">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ab2db-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="ab2db-103">Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` výjimky ladění jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="ab2db-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab2db-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab2db-104">Methods</span></span>  
  
|<span data-ttu-id="ab2db-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab2db-105">Method</span></span>|<span data-ttu-id="ab2db-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ab2db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab2db-107">GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="ab2db-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="ab2db-108">Jaký druh událostí označuje to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="ab2db-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="ab2db-109">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="ab2db-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="ab2db-110">Získá vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="ab2db-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab2db-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab2db-111">Remarks</span></span>  
 <span data-ttu-id="ab2db-112">Následující rozhraní jsou odvozeny z `ICorDebugDebugEvent` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="ab2db-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="ab2db-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ab2db-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="ab2db-114">Icordebugmoduledebugevent –</span><span class="sxs-lookup"><span data-stu-id="ab2db-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="ab2db-115">Rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ab2db-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="ab2db-116">Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ab2db-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab2db-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab2db-117">Requirements</span></span>  
 <span data-ttu-id="ab2db-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab2db-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab2db-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab2db-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab2db-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab2db-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab2db-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab2db-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2db-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab2db-122">See also</span></span>
- [<span data-ttu-id="ab2db-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ab2db-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ab2db-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="ab2db-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
