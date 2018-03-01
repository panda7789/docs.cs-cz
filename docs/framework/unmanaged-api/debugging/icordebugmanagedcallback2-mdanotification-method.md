---
title: "ICorDebugManagedCallback2::MDANotification – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a58e286feb3387557d0a37c463f2af67abf8cc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="a9687-102">ICorDebugManagedCallback2::MDANotification – metoda</span><span class="sxs-lookup"><span data-stu-id="a9687-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="a9687-103">Poskytuje oznámení, že provádění kódu se vyskytla spravované ladění pomocníka (MDA) v aplikaci, která je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="a9687-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9687-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9687-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9687-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9687-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="a9687-106">[v] Ukazatel na ICorDebugController rozhraní, které zpřístupňuje proces nebo doménu aplikace, ve kterém MDA došlo.</span><span class="sxs-lookup"><span data-stu-id="a9687-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="a9687-107">Ladicí program neprovádějte žádné předpoklady o tom, zda je řadič procesu nebo doménu aplikace, i když může se vždy dotázat rozhraní pro určení.</span><span class="sxs-lookup"><span data-stu-id="a9687-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a9687-108">[v] Ukazatel na ICorDebugThread rozhraní, které vystavuje spravovaných vláken, na kterém došlo k události ladění.</span><span class="sxs-lookup"><span data-stu-id="a9687-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="a9687-109">Pokud MDA došlo k chybě na nespravované vláken, hodnota `pThread` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a9687-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="a9687-110">ID vlákna operační systém (OS), musíte si z samotného objektu (mda).</span><span class="sxs-lookup"><span data-stu-id="a9687-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="a9687-111">[v] Ukazatel na [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) rozhraní, která zveřejňuje informace (mda).</span><span class="sxs-lookup"><span data-stu-id="a9687-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9687-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9687-112">Remarks</span></span>  
 <span data-ttu-id="a9687-113">MDA je Heuristická upozornění a nevyžaduje žádné explicitní ladicí program akce s výjimkou volání [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) Chcete-li pokračovat v provádění aplikace, která je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="a9687-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="a9687-114">Modul CLR (CLR) můžete určit, který při vyvolání mda a data, která je v jakékoli dané MDA v libovolném bodě.</span><span class="sxs-lookup"><span data-stu-id="a9687-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="a9687-115">Proto by nemělo ladicí programy sestavení žádné funkce, které vyžadují určité vzory (mda).</span><span class="sxs-lookup"><span data-stu-id="a9687-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="a9687-116">Mda mohou být zařazeny do fronty a aktivováno krátce po narazí (mda).</span><span class="sxs-lookup"><span data-stu-id="a9687-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="a9687-117">Toto může nastat, pokud modul runtime musí počkat, dokud nebude dosaženo bod bezpečné pro ohlásí MDA, místo aktivuje MDA, když se zjistí.</span><span class="sxs-lookup"><span data-stu-id="a9687-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="a9687-118">Taky to znamená, že modul runtime může aktivovat počet mda v jedné sadě zařazených do fronty zpětných volání (podobně jako událost operace "připojit").</span><span class="sxs-lookup"><span data-stu-id="a9687-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="a9687-119">Ladicí program by měl verze odkaz na `ICorDebugMDA` instance ihned po vrácení z `MDANotification` zpětné volání, chcete-li povolit modul CLR recyklace paměťové nároky (mda).</span><span class="sxs-lookup"><span data-stu-id="a9687-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="a9687-120">Uvolnění instance může zvýšit výkon, pokud se aktivuje mnoho mda.</span><span class="sxs-lookup"><span data-stu-id="a9687-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9687-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9687-121">Requirements</span></span>  
 <span data-ttu-id="a9687-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9687-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9687-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9687-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9687-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9687-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9687-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9687-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9687-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9687-126">See Also</span></span>  
 [<span data-ttu-id="a9687-127">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a9687-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a9687-128">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9687-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="a9687-129">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9687-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
