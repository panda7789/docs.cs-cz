---
title: ICorDebugUnmanagedCallback::DebugEvent – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ec45004f5dd87983187690a0a4feefb35b05e85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748952"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="45c3f-102">ICorDebugUnmanagedCallback::DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="45c3f-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="45c3f-103">Upozorní ladicího programu, že nativní události byl aktivován.</span><span class="sxs-lookup"><span data-stu-id="45c3f-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45c3f-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45c3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45c3f-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="45c3f-106">[in] Ukazatel na nativní události.</span><span class="sxs-lookup"><span data-stu-id="45c3f-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="45c3f-107">[in] `true`, pokud po výskytu nespravované události, až do volání ladicího programu není možné interakce s daným stavem spravovaného procesu [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="45c3f-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45c3f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45c3f-108">Remarks</span></span>  
 <span data-ttu-id="45c3f-109">Vlákno Win32 při ladění vlákna se nepoužívají žádné členy Win32 ladění v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="45c3f-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="45c3f-110">Můžete volat `ICorDebugController::Continue` pouze na vlákno Win32 a pouze v případě, že budete pokračovat minulé události out-of-band.</span><span class="sxs-lookup"><span data-stu-id="45c3f-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="45c3f-111">`DebugEvent` Zpětného volání nedodržuje standardní pravidla pro zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="45c3f-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="45c3f-112">Při volání `DebugEvent`, proces bude v nezpracovaná, operační systém ladění stavu Zastaveno.</span><span class="sxs-lookup"><span data-stu-id="45c3f-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="45c3f-113">Proces se nebudou synchronizovat.</span><span class="sxs-lookup"><span data-stu-id="45c3f-113">The process will not be synchronized.</span></span> <span data-ttu-id="45c3f-114">Zadá automaticky synchronizované stavové, když je potřeba splnit požadavky na informace o spravovaného kódu, který může vést k jiné vnořené `DebugEvent` zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="45c3f-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="45c3f-115">Volání [icordebugprocess::clearcurrentexception –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) na postup ignorovat události výjimky před pokračováním procesu.</span><span class="sxs-lookup"><span data-stu-id="45c3f-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="45c3f-116">Voláním této metody odesílá DBG_CONTINUE místo DBG_EXCEPTION_NOT_HANDLED v požadavku pokračovat a automaticky vymaže out-of-band zarážky a krokování výjimky.</span><span class="sxs-lookup"><span data-stu-id="45c3f-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="45c3f-117">Out-of-band události můžou mít v každém okamžiku i v případě, že právě laděné aplikace, zobrazí se zastavila, a když nezpracovaných událostí ve vzdálené již existuje.</span><span class="sxs-lookup"><span data-stu-id="45c3f-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="45c3f-118">V rozhraní .NET Framework verze 2.0 by měl ladicí program okamžitě pokračovat po zarážku out-of-band událost.</span><span class="sxs-lookup"><span data-stu-id="45c3f-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="45c3f-119">Ladicí program by měl používat [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) a [icordebugprocess2::clearunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metody pro přidání a odebrání zarážky.</span><span class="sxs-lookup"><span data-stu-id="45c3f-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="45c3f-120">Tyto metody se přeskočit všechny zarážky out-of-band automaticky.</span><span class="sxs-lookup"><span data-stu-id="45c3f-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="45c3f-121">Proto pouze out-of-band zarážek, které získáte odeslaných by měl být nezpracovaná zarážky, které jsou již ve službě stream instrukce, jako je například voláním rozhraní Win32 `DebugBreak` funkce.</span><span class="sxs-lookup"><span data-stu-id="45c3f-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="45c3f-122">Nepokoušejte se použít `ICorDebugProcess::ClearCurrentException`, [icordebugprocess::getthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [icordebugprocess::setthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), nebo libovolný jiný člen [ladění v rozhraní API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="45c3f-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45c3f-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45c3f-123">Requirements</span></span>  
 <span data-ttu-id="45c3f-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45c3f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45c3f-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45c3f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45c3f-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45c3f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45c3f-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45c3f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c3f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45c3f-128">See also</span></span>

- [<span data-ttu-id="45c3f-129">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45c3f-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
