---
title: ICorDebugManagedCallback2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c9b81536bd39c6879161526cc96c136b71b3172
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547995"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="7c85d-102">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c85d-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="7c85d-103">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="7c85d-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="7c85d-104">`ICorDebugManagedCallback2` je logickým rozšířením [icordebugmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c85d-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c85d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7c85d-105">Methods</span></span>  
  
|<span data-ttu-id="7c85d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-106">Method</span></span>|<span data-ttu-id="7c85d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7c85d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c85d-108">ChangeConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="7c85d-109">Upozorní ladicího programu, že se změnila sadu úkolů přidružených k zadané připojení.</span><span class="sxs-lookup"><span data-stu-id="7c85d-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="7c85d-110">CreateConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="7c85d-111">Upozorní ladicího programu, že se vytvořila nová připojení.</span><span class="sxs-lookup"><span data-stu-id="7c85d-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="7c85d-112">DestroyConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="7c85d-113">Upozorní ladicího programu, že zadané připojení se ukončilo.</span><span class="sxs-lookup"><span data-stu-id="7c85d-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="7c85d-114">Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="7c85d-115">Upozorní ladicího programu, že bylo zahájeno hledání pro obslužnou rutinu výjimky.</span><span class="sxs-lookup"><span data-stu-id="7c85d-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="7c85d-116">ExceptionUnwind – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="7c85d-117">Poskytuje stavu oznámení během procesu odvíjení výjimky.</span><span class="sxs-lookup"><span data-stu-id="7c85d-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="7c85d-118">FunctionRemapComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="7c85d-119">Upozorní ladicího programu, že spuštění kódu se přepnulo na novou verzi funkce se upravila.</span><span class="sxs-lookup"><span data-stu-id="7c85d-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="7c85d-120">FunctionRemapOpportunity – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="7c85d-121">Upozorní ladicího programu, že spuštění kódu bylo dosaženo bodu sekvence. ve starší verzi funkce se upravila.</span><span class="sxs-lookup"><span data-stu-id="7c85d-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="7c85d-122">MDANotification – metoda</span><span class="sxs-lookup"><span data-stu-id="7c85d-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="7c85d-123">Poskytuje oznámení, že spuštění kódu došlo k spravovaného ladění zprávu Pomocníka s nastavením (MDA).</span><span class="sxs-lookup"><span data-stu-id="7c85d-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c85d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c85d-124">Remarks</span></span>  
 <span data-ttu-id="7c85d-125">`ICorDebugManagedCallback2` Rozhraní rozšiřuje `ICorDebugManagedCallback` rozhraní pro zpracovávání nových událostí ladění zavedena v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="7c85d-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="7c85d-126">Ladicí program musí implementovat `ICorDebugManagedCallback2` pokud ji je ladění aplikace rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="7c85d-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="7c85d-127">Instance `ICorDebugManagedCallback` nebo `ICorDebugManagedCallback2` je předán jako objekt zpětného volání k [icordebug::setmanagedhandler –](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="7c85d-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c85d-128">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="7c85d-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c85d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c85d-129">Requirements</span></span>  
 <span data-ttu-id="7c85d-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c85d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c85d-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c85d-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c85d-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c85d-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c85d-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c85d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c85d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c85d-134">See also</span></span>
- [<span data-ttu-id="7c85d-135">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7c85d-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7c85d-136">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7c85d-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7c85d-137">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c85d-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
