---
title: "Rozhraní ICorDebugExceptionDebugEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c485338f196e4748805231a8391645fdc182d70d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="51135-102">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="51135-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="51135-103">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí výjimky.</span><span class="sxs-lookup"><span data-stu-id="51135-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51135-104">Metody</span><span class="sxs-lookup"><span data-stu-id="51135-104">Methods</span></span>  
  
|<span data-ttu-id="51135-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="51135-105">Method</span></span>|<span data-ttu-id="51135-106">Popis</span><span class="sxs-lookup"><span data-stu-id="51135-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51135-107">Getflags – metoda</span><span class="sxs-lookup"><span data-stu-id="51135-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="51135-108">Získá a příznak, který určuje, zda výjimku může zachytit.</span><span class="sxs-lookup"><span data-stu-id="51135-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="51135-109">GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="51135-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="51135-110">Získá ukazatel nativní rozhraní pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="51135-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="51135-111">GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="51135-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="51135-112">Získá ukazatel zásobníku pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="51135-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51135-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51135-113">Remarks</span></span>  
 <span data-ttu-id="51135-114">`ICorDebugExceptionDebugEvent` Rozhraní je implementováno modulem následující typy událostí:</span><span class="sxs-lookup"><span data-stu-id="51135-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="51135-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="51135-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="51135-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="51135-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="51135-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="51135-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="51135-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="51135-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="51135-119">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="51135-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="51135-120">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="51135-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51135-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51135-121">Requirements</span></span>  
 <span data-ttu-id="51135-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51135-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51135-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51135-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51135-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51135-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51135-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51135-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51135-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="51135-126">See Also</span></span>  
 [<span data-ttu-id="51135-127">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="51135-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="51135-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="51135-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
