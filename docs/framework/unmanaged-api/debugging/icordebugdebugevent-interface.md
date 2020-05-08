---
title: Rozhraní ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: a66012651d4b307d06a5a3bff675a248cc0ee376
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976353"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="6bd48-102">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="6bd48-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="6bd48-103">Definuje základní rozhraní, ze kterého jsou `ICorDebug` odvozeny všechny události ladění.</span><span class="sxs-lookup"><span data-stu-id="6bd48-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bd48-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6bd48-104">Methods</span></span>  
  
|<span data-ttu-id="6bd48-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6bd48-105">Method</span></span>|<span data-ttu-id="6bd48-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6bd48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bd48-107">GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="6bd48-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="6bd48-108">Určuje, jaký druh události tento `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="6bd48-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="6bd48-109">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="6bd48-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="6bd48-110">Získá vlákno, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="6bd48-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bd48-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bd48-111">Remarks</span></span>  
 <span data-ttu-id="6bd48-112">Následující rozhraní jsou odvozena z `ICorDebugDebugEvent` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="6bd48-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="6bd48-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="6bd48-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="6bd48-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="6bd48-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="6bd48-115">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6bd48-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="6bd48-116">Pokus o volání metody `QueryInterface` načtení ukazatele rozhraní `E_NOINTERFACE` pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6bd48-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bd48-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bd48-117">Requirements</span></span>  
 <span data-ttu-id="6bd48-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bd48-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd48-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bd48-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bd48-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6bd48-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bd48-121">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd48-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd48-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bd48-122">See also</span></span>

- [<span data-ttu-id="6bd48-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bd48-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6bd48-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="6bd48-124">Debugging</span></span>](index.md)
