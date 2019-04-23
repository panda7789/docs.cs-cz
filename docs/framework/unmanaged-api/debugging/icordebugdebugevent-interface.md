---
title: Rozhraní ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550cb6379ef0d5d17a3446b3f21120208b5a3dad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110185"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="6695a-102">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="6695a-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="6695a-103">Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` výjimky ladění jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="6695a-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6695a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6695a-104">Methods</span></span>  
  
|<span data-ttu-id="6695a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6695a-105">Method</span></span>|<span data-ttu-id="6695a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6695a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6695a-107">GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="6695a-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="6695a-108">Jaký druh událostí označuje to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="6695a-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="6695a-109">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="6695a-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="6695a-110">Získá vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="6695a-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6695a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6695a-111">Remarks</span></span>  
 <span data-ttu-id="6695a-112">Následující rozhraní jsou odvozeny z `ICorDebugDebugEvent` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="6695a-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="6695a-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="6695a-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="6695a-114">Icordebugmoduledebugevent –</span><span class="sxs-lookup"><span data-stu-id="6695a-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="6695a-115">Rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6695a-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="6695a-116">Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6695a-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6695a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6695a-117">Requirements</span></span>  
 <span data-ttu-id="6695a-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6695a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6695a-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6695a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6695a-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6695a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6695a-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6695a-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6695a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6695a-122">See also</span></span>

- [<span data-ttu-id="6695a-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6695a-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6695a-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="6695a-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
