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
ms.openlocfilehash: f850b3cd35fda8bd554b99e14553100008cb4eca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208522"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="892c0-102">ICorDebugManagedCallback2::MDANotification – metoda</span><span class="sxs-lookup"><span data-stu-id="892c0-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="892c0-103">Poskytuje oznámení o tom, že provádění kódu zjistilo v aplikaci, která je laděna, pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="892c0-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="892c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="892c0-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="892c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="892c0-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="892c0-106">pro Ukazatel na rozhraní ICorDebugController, které zpřístupňuje proces nebo doménu aplikace, ve které došlo k MDA.</span><span class="sxs-lookup"><span data-stu-id="892c0-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="892c0-107">Ladicí program by neměl dělat žádné předpoklady o tom, zda je kontroler nebo doména aplikace, i když se může vždy dotázat na rozhraní, aby bylo možné provést určení.</span><span class="sxs-lookup"><span data-stu-id="892c0-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="892c0-108">pro Ukazatel na rozhraní ICorDebugThread, které zveřejňuje spravované vlákno, na kterém došlo k události ladění.</span><span class="sxs-lookup"><span data-stu-id="892c0-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="892c0-109">Pokud k MDA došlo na nespravovaném vlákně, hodnota `pThread` bude null.</span><span class="sxs-lookup"><span data-stu-id="892c0-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="892c0-110">Musíte získat ID vlákna operačního systému (OS) z samotného objektu MDA.</span><span class="sxs-lookup"><span data-stu-id="892c0-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="892c0-111">pro Ukazatel na rozhraní [ICorDebugMDA](icordebugmda-interface.md) , které zpřístupňuje informace MDA.</span><span class="sxs-lookup"><span data-stu-id="892c0-111">[in] A pointer to an [ICorDebugMDA](icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="892c0-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="892c0-112">Remarks</span></span>  
 <span data-ttu-id="892c0-113">MDA je heuristické upozornění a nevyžaduje žádnou explicitní akci ladicího programu s výjimkou volání [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) pro pokračování v provádění aplikace, která se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="892c0-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="892c0-114">Modul CLR (Common Language Runtime) může určit, které MDA jsou vyvolány a která data jsou v jakémkoli okamžiku v daném bodě.</span><span class="sxs-lookup"><span data-stu-id="892c0-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="892c0-115">Proto by ladicí program neměl vytvářet žádné funkce vyžadující konkrétní vzory MDA.</span><span class="sxs-lookup"><span data-stu-id="892c0-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="892c0-116">MDA se může zařadit do fronty a aktivovat krátce po zjištění MDA.</span><span class="sxs-lookup"><span data-stu-id="892c0-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="892c0-117">K tomu může dojít v případě, že modul runtime potřebuje počkat, dokud nedosáhne bezpečného bodu pro vypálení služby MDA, namísto toho, aby se při jeho výskytu neiniciovala operace MDA.</span><span class="sxs-lookup"><span data-stu-id="892c0-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="892c0-118">Také to znamená, že modul runtime může v jedné sadě zpětných volání ve frontě aktivovat určitý počet MDA (podobně jako operace "připojit").</span><span class="sxs-lookup"><span data-stu-id="892c0-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="892c0-119">Ladicí program by měl vydat odkaz na `ICorDebugMDA` instanci hned po návratu ze `MDANotification` zpětného volání, aby mohl modul CLR recyklovat paměť spotřebovaná pomocí MDA.</span><span class="sxs-lookup"><span data-stu-id="892c0-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="892c0-120">Uvolnění instance může zlepšit výkon, pokud se právě MDA spousta.</span><span class="sxs-lookup"><span data-stu-id="892c0-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="892c0-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="892c0-121">Requirements</span></span>  
 <span data-ttu-id="892c0-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="892c0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="892c0-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="892c0-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="892c0-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="892c0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="892c0-125">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="892c0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892c0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="892c0-126">See also</span></span>

- [<span data-ttu-id="892c0-127">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="892c0-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="892c0-128">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="892c0-128">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="892c0-129">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="892c0-129">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
