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
ms.workload: dotnet
ms.openlocfilehash: 97bbd9374b8a3f938f42b8ddd001049a2e7a324c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="9e477-102">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="9e477-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="9e477-103">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí výjimky.</span><span class="sxs-lookup"><span data-stu-id="9e477-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e477-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9e477-104">Methods</span></span>  
  
|<span data-ttu-id="9e477-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e477-105">Method</span></span>|<span data-ttu-id="9e477-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9e477-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e477-107">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="9e477-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="9e477-108">Získá a příznak, který určuje, zda výjimku může zachytit.</span><span class="sxs-lookup"><span data-stu-id="9e477-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="9e477-109">GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="9e477-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="9e477-110">Získá ukazatel nativní rozhraní pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="9e477-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="9e477-111">GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="9e477-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="9e477-112">Získá ukazatel zásobníku pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="9e477-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e477-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e477-113">Remarks</span></span>  
 <span data-ttu-id="9e477-114">`ICorDebugExceptionDebugEvent` Rozhraní je implementováno modulem následující typy událostí:</span><span class="sxs-lookup"><span data-stu-id="9e477-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="9e477-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="9e477-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="9e477-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="9e477-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="9e477-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="9e477-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="9e477-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="9e477-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="9e477-119">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="9e477-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="9e477-120">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9e477-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e477-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e477-121">Requirements</span></span>  
 <span data-ttu-id="9e477-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e477-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e477-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e477-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e477-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e477-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e477-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e477-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e477-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e477-126">See Also</span></span>  
 [<span data-ttu-id="9e477-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9e477-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9e477-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="9e477-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
