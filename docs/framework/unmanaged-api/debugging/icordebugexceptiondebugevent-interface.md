---
title: Rozhraní ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e2a147d46412eb4feb192070ff8420cab842a6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995883"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="ba1e4-102">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ba1e4-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="ba1e4-103">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu události výjimky.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba1e4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ba1e4-104">Methods</span></span>  
  
|<span data-ttu-id="ba1e4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ba1e4-105">Method</span></span>|<span data-ttu-id="ba1e4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ba1e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba1e4-107">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="ba1e4-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="ba1e4-108">Získá příznak, který označuje, zda výjimku může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="ba1e4-109">GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="ba1e4-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="ba1e4-110">Získá ukazatel nativní rozhraní pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="ba1e4-111">GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="ba1e4-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="ba1e4-112">Získá ukazatel zásobníku pro události ladění této výjimky.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba1e4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba1e4-113">Remarks</span></span>  
 <span data-ttu-id="ba1e4-114">`ICorDebugExceptionDebugEvent` Rozhraní je implementováno následující typy událostí:</span><span class="sxs-lookup"><span data-stu-id="ba1e4-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="ba1e4-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ba1e4-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ba1e4-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ba1e4-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ba1e4-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="ba1e4-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ba1e4-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="ba1e4-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="ba1e4-119">Rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="ba1e4-120">Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba1e4-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba1e4-121">Requirements</span></span>  
 <span data-ttu-id="ba1e4-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba1e4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba1e4-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba1e4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba1e4-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba1e4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba1e4-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba1e4-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1e4-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba1e4-126">See also</span></span>

- [<span data-ttu-id="ba1e4-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ba1e4-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ba1e4-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="ba1e4-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
