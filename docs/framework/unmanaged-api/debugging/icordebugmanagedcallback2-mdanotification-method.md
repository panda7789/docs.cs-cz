---
title: ICorDebugManagedCallback2::MDANotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15addd0b35c43945f643386f8983fc14c9312bae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492332"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="b30ba-102">ICorDebugManagedCallback2::MDANotification – metoda</span><span class="sxs-lookup"><span data-stu-id="b30ba-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="b30ba-103">Poskytuje oznámení, že spuštění kódu došlo k Pomocník spravovaného ladění (MDA) v aplikaci, která je právě laděna.</span><span class="sxs-lookup"><span data-stu-id="b30ba-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b30ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b30ba-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b30ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b30ba-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="b30ba-106">[in] Ukazatel na icordebugcontroller – rozhraní, která zveřejňuje proces nebo doménu aplikace, ve kterém MDA došlo.</span><span class="sxs-lookup"><span data-stu-id="b30ba-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="b30ba-107">Ladicí program by neměla provést nevyvozujte předpoklady o tom, jestli je kontroler proces nebo doménu aplikace, i když ho vždy dotazování rozhraní pro určení.</span><span class="sxs-lookup"><span data-stu-id="b30ba-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b30ba-108">[in] Ukazatel na icordebugthread – rozhraní, která zveřejňuje spravované vlákno, na kterém došlo k události ladění.</span><span class="sxs-lookup"><span data-stu-id="b30ba-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="b30ba-109">Pokud MDA došlo k chybě na nespravované vlákna, hodnota `pThread` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b30ba-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="b30ba-110">ID vlákna operačního systému (OS) musí získat od samotného objektu MDA.</span><span class="sxs-lookup"><span data-stu-id="b30ba-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="b30ba-111">[in] Ukazatel [icordebugmda –](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) rozhraní, které zveřejňuje informace o MDA.</span><span class="sxs-lookup"><span data-stu-id="b30ba-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b30ba-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b30ba-112">Remarks</span></span>  
 <span data-ttu-id="b30ba-113">MDA heuristické upozornění a nevyžaduje žádnou akci explicitní ladicího programu s výjimkou volání [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) pokračovat provádění aplikace, která je právě laděna.</span><span class="sxs-lookup"><span data-stu-id="b30ba-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="b30ba-114">Modul CLR (CLR) můžete určit, které jsou vyvolávány mda a která data se v jakékoli dané MDA v libovolném bodě.</span><span class="sxs-lookup"><span data-stu-id="b30ba-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="b30ba-115">Proto by neměl ladicí programy sestavení všechny funkce, které vyžadují specifické vzory MDA.</span><span class="sxs-lookup"><span data-stu-id="b30ba-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="b30ba-116">Mda mohou být zařazeny do fronty a krátce po narazí MDA aktivuje.</span><span class="sxs-lookup"><span data-stu-id="b30ba-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="b30ba-117">Může k tomu dojít, pokud modul runtime musí čekat, dokud nedosáhne bod bezpečné pro aktivaci MDA, místo spouštění MDA, pokud se setká.</span><span class="sxs-lookup"><span data-stu-id="b30ba-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="b30ba-118">Také znamená, že modul runtime může vyvolat počet mda v jediné sady kontrolních zařazených do fronty zpětná volání (podobné události operace "připojit").</span><span class="sxs-lookup"><span data-stu-id="b30ba-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="b30ba-119">Ladicí program by měla uvolnit odkaz na `ICorDebugMDA` instance ihned po vrácení z `MDANotification` zpětné volání, chcete-li povolit modul CLR recyklace paměti používané MDA.</span><span class="sxs-lookup"><span data-stu-id="b30ba-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="b30ba-120">Uvolnění instance může zvýšit výkon, pokud se ohlásí mnoho mda.</span><span class="sxs-lookup"><span data-stu-id="b30ba-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b30ba-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b30ba-121">Requirements</span></span>  
 <span data-ttu-id="b30ba-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b30ba-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b30ba-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b30ba-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b30ba-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b30ba-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b30ba-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b30ba-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b30ba-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b30ba-126">See also</span></span>
- [<span data-ttu-id="b30ba-127">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="b30ba-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b30ba-128">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b30ba-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b30ba-129">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b30ba-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
