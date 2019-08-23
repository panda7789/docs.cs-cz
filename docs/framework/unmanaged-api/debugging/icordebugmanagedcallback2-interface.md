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
ms.openlocfilehash: ca33436d98edf5844a5ca27c9ac89648f10ec0c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909987"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="991a0-102">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="991a0-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="991a0-103">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="991a0-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="991a0-104">`ICorDebugManagedCallback2`je logickým rozšířením rozhraní [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="991a0-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="991a0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="991a0-105">Methods</span></span>  
  
|<span data-ttu-id="991a0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-106">Method</span></span>|<span data-ttu-id="991a0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="991a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="991a0-108">ChangeConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="991a0-109">Oznamuje ladicímu programu, že se změnila sada úloh přidružených k zadanému připojení.</span><span class="sxs-lookup"><span data-stu-id="991a0-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="991a0-110">CreateConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="991a0-111">Oznamuje ladicímu programu, že bylo vytvořeno nové připojení.</span><span class="sxs-lookup"><span data-stu-id="991a0-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="991a0-112">DestroyConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="991a0-113">Oznamuje ladicímu programu, že zadané připojení bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="991a0-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="991a0-114">Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="991a0-115">Oznamuje ladicímu programu, že bylo zahájeno hledání obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="991a0-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="991a0-116">ExceptionUnwind – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="991a0-117">Poskytuje oznámení o stavu během procesu odvíjení výjimky.</span><span class="sxs-lookup"><span data-stu-id="991a0-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="991a0-118">FunctionRemapComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="991a0-119">Oznamuje ladicímu programu, že provádění kódu se přepnulo na novou verzi upravované funkce.</span><span class="sxs-lookup"><span data-stu-id="991a0-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="991a0-120">FunctionRemapOpportunity – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="991a0-121">Oznamuje ladicímu programu, že provádění kódu dosáhlo bodu sekvence ve starší verzi upravované funkce.</span><span class="sxs-lookup"><span data-stu-id="991a0-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="991a0-122">MDANotification – metoda</span><span class="sxs-lookup"><span data-stu-id="991a0-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="991a0-123">Poskytuje oznámení o tom, že při provádění kódu došlo ke zprávě pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="991a0-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="991a0-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="991a0-124">Remarks</span></span>  
 <span data-ttu-id="991a0-125">`ICorDebugManagedCallback2` Rozhraní`ICorDebugManagedCallback` rozšiřuje rozhraní tak, aby zpracovávala nové události ladění představené ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="991a0-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="991a0-126">Ladicí program musí implementovat `ICorDebugManagedCallback2` , pokud ladí aplikace .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="991a0-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="991a0-127">Instance `ICorDebugManagedCallback` nebo`ICorDebugManagedCallback2` je předána jako objekt zpětného volání do [ICorDebug:: SetManagedHandler –](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="991a0-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="991a0-128">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="991a0-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="991a0-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="991a0-129">Requirements</span></span>  
 <span data-ttu-id="991a0-130">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="991a0-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="991a0-131">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="991a0-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="991a0-132">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="991a0-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="991a0-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="991a0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991a0-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="991a0-134">See also</span></span>

- [<span data-ttu-id="991a0-135">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="991a0-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="991a0-136">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="991a0-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="991a0-137">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="991a0-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
