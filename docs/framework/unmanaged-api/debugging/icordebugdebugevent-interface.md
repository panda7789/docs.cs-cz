---
title: Rozhraní ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: ea42faa4001fa880354690df1551de3be767e683
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137041"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="db189-102">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="db189-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="db189-103">Definuje základní rozhraní, ze kterého jsou odvozeny všechny události `ICorDebug` ladění.</span><span class="sxs-lookup"><span data-stu-id="db189-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db189-104">Metody</span><span class="sxs-lookup"><span data-stu-id="db189-104">Methods</span></span>  
  
|<span data-ttu-id="db189-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="db189-105">Method</span></span>|<span data-ttu-id="db189-106">Popis</span><span class="sxs-lookup"><span data-stu-id="db189-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db189-107">GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="db189-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="db189-108">Určuje, jaký typ události tento objekt `ICorDebugDebugEvent` představuje.</span><span class="sxs-lookup"><span data-stu-id="db189-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="db189-109">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="db189-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="db189-110">Získá vlákno, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="db189-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db189-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db189-111">Remarks</span></span>  
 <span data-ttu-id="db189-112">Následující rozhraní jsou odvozena z rozhraní `ICorDebugDebugEvent`:</span><span class="sxs-lookup"><span data-stu-id="db189-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="db189-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="db189-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="db189-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="db189-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="db189-115">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="db189-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="db189-116">Pokus o volání `QueryInterface` pro načtení ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="db189-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db189-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db189-117">Requirements</span></span>  
 <span data-ttu-id="db189-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db189-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db189-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db189-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db189-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db189-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db189-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db189-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db189-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db189-122">See also</span></span>

- [<span data-ttu-id="db189-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="db189-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="db189-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="db189-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
