---
title: "ICorDebugUnmanagedCallback::DebugEvent – metoda"
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
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49c3386fcda0bc731935ec9db7d029d0e619ef14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="b43e2-102">ICorDebugUnmanagedCallback::DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="b43e2-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="b43e2-103">Upozorní ladicí program, že nativní událostí je aktivován.</span><span class="sxs-lookup"><span data-stu-id="b43e2-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b43e2-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b43e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b43e2-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="b43e2-106">[v] Ukazatel na nativní událostí.</span><span class="sxs-lookup"><span data-stu-id="b43e2-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="b43e2-107">[v] `true`, pokud interakci s stavu spravovaného procesu není možné po nespravované události dojde, dokud volání ladicí program [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md), jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="b43e2-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b43e2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b43e2-108">Remarks</span></span>  
 <span data-ttu-id="b43e2-109">Pokud je vlákno laděné Win32 vlákno, nepoužívejte žádné členy Win32 ladění v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b43e2-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="b43e2-110">Můžete volat `ICorDebugController::Continue` pouze ve vlákně Win32 a pouze v případě, že budete pokračovat po out-of-band událost.</span><span class="sxs-lookup"><span data-stu-id="b43e2-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="b43e2-111">`DebugEvent` Zpětného volání nedodrží standardní pravidla pro zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="b43e2-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="b43e2-112">Při volání `DebugEvent`, proces bude v nezpracovaná, OS-debug zastaveno stavu.</span><span class="sxs-lookup"><span data-stu-id="b43e2-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="b43e2-113">Proces se nebudou synchronizovat.</span><span class="sxs-lookup"><span data-stu-id="b43e2-113">The process will not be synchronized.</span></span> <span data-ttu-id="b43e2-114">Zadá automaticky synchronizovaného stavu, když je potřeba splnit požadavky na informace o spravovaného kódu, což může vést k jiné vnořené `DebugEvent` zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="b43e2-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="b43e2-115">Volání [icordebugprocess::clearcurrentexception –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) na procesu, ignorovat událost výjimky před pokračováním procesu.</span><span class="sxs-lookup"><span data-stu-id="b43e2-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="b43e2-116">Voláním této metody odešle DBG_CONTINUE místo DBG_EXCEPTION_NOT_HANDLED u požadavku pokračovat a automaticky vymaže krokování výjimek a out-of-band zarážky.</span><span class="sxs-lookup"><span data-stu-id="b43e2-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="b43e2-117">Out-of-band události můžou mít kdykoli, i v případě, že laděné aplikace se zobrazí ukončeno, a když nevyřízené události integrované již existuje.</span><span class="sxs-lookup"><span data-stu-id="b43e2-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="b43e2-118">V rozhraní .NET Framework verze 2.0 by měly ladicího programu okamžitě pokračovat po zarážku – out-of-band událost.</span><span class="sxs-lookup"><span data-stu-id="b43e2-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="b43e2-119">Ladicí program by měl používat [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) a [icordebugprocess2::clearunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metody pro přidání a odebrání zarážky.</span><span class="sxs-lookup"><span data-stu-id="b43e2-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="b43e2-120">Tyto metody automaticky přeskočí přes všechny out-of-band zarážky.</span><span class="sxs-lookup"><span data-stu-id="b43e2-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="b43e2-121">Proto pouze out-of-band zarážky, které získat odeslaných by měla být nezpracovaná zarážky, které jsou již v datovém proudu instrukce, jako je například volání Win32 `DebugBreak` funkce.</span><span class="sxs-lookup"><span data-stu-id="b43e2-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="b43e2-122">Nepokoušejte se použít `ICorDebugProcess::ClearCurrentException`, [icordebugprocess::getthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [icordebugprocess::setthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), nebo jakékoli jiné člen [rozhraní API pro ladění](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="b43e2-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43e2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b43e2-123">Requirements</span></span>  
 <span data-ttu-id="b43e2-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b43e2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43e2-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b43e2-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b43e2-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b43e2-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b43e2-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43e2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43e2-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b43e2-128">See Also</span></span>  
 [<span data-ttu-id="b43e2-129">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b43e2-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
