---
title: "ICorDebugManagedCallback2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2
helpviewer_keywords: ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d5b8ac63d200e54d25b58870089f6c062397186
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="bd7f3-102">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd7f3-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="bd7f3-103">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="bd7f3-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="bd7f3-104">`ICorDebugManagedCallback2`je logické rozšíření [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd7f3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bd7f3-105">Methods</span></span>  
  
|<span data-ttu-id="bd7f3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-106">Method</span></span>|<span data-ttu-id="bd7f3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bd7f3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd7f3-108">Changeconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="bd7f3-109">Upozorní ladicí program, že se změnila sadu úloh, které jsou přidružené k zadané připojení.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="bd7f3-110">Createconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="bd7f3-111">Upozorní ladicího programu vytvořený nové připojení.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="bd7f3-112">Destroyconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="bd7f3-113">Upozorní ladicí program, že zadané připojení se ukončilo.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="bd7f3-114">Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="bd7f3-115">Aby bylo zahájeno hledání pro obslužnou rutinu výjimky upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="bd7f3-116">Exceptionunwind – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="bd7f3-117">Poskytuje oznámení o stavu během procesu unwinding výjimka.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="bd7f3-118">Functionremapcomplete – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="bd7f3-119">Upozorní ladicí program, že provádění kódu přepnul na novou verzi upravená funkce.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="bd7f3-120">Functionremapopportunity – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="bd7f3-121">Upozorní ladicí program, že provádění kódu dosáhl bod sekvence ve starší verzi upravená funkce.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="bd7f3-122">Mdanotification – metoda</span><span class="sxs-lookup"><span data-stu-id="bd7f3-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="bd7f3-123">Poskytuje oznámení, že provádění kódu se vyskytla spravované ladění zprávy pomocníka (MDA).</span><span class="sxs-lookup"><span data-stu-id="bd7f3-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd7f3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd7f3-124">Remarks</span></span>  
 <span data-ttu-id="bd7f3-125">`ICorDebugManagedCallback2` Rozšiřuje rozhraní `ICorDebugManagedCallback` rozhraní pro zpracování nové události ladění byla zavedená v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="bd7f3-126">Ladicí program musí implementovat `ICorDebugManagedCallback2` pokud ho je ladění aplikací rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="bd7f3-127">Instance `ICorDebugManagedCallback` nebo `ICorDebugManagedCallback2` se předá jako objekt zpětného volání, který má [icordebug::setmanagedhandler –](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="bd7f3-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd7f3-128">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="bd7f3-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd7f3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd7f3-129">Requirements</span></span>  
 <span data-ttu-id="bd7f3-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd7f3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd7f3-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd7f3-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd7f3-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd7f3-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd7f3-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd7f3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7f3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd7f3-134">See Also</span></span>  
 [<span data-ttu-id="bd7f3-135">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="bd7f3-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="bd7f3-136">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd7f3-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bd7f3-137">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd7f3-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
