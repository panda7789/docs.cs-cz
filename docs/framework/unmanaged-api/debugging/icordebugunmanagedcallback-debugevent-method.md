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
ms.openlocfilehash: cb52150a17c9ec8f4bbc25c13b85bce56b221eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791196"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="f592d-102">ICorDebugUnmanagedCallback::DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="f592d-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="f592d-103">Oznamuje ladicímu programu, že byla vyvolána nativní událost.</span><span class="sxs-lookup"><span data-stu-id="f592d-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f592d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f592d-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f592d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f592d-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="f592d-106">pro Ukazatel na nativní událost.</span><span class="sxs-lookup"><span data-stu-id="f592d-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="f592d-107">[in] `true`, pokud interakce se stavem spravovaného procesu není nemožné po výskytu nespravované události, dokud ladicí program nevolá [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="f592d-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f592d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f592d-108">Remarks</span></span>  
 <span data-ttu-id="f592d-109">Pokud vlákno, které je laděno, je vlákno Win32, nepoužívejte žádné členy ladicího rozhraní Win32.</span><span class="sxs-lookup"><span data-stu-id="f592d-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="f592d-110">Můžete volat `ICorDebugController::Continue` pouze ve vlákně Win32 a pouze v případě, že budete pokračovat po událostech mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="f592d-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="f592d-111">Zpětné volání `DebugEvent` nedodržuje standardní pravidla pro zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="f592d-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="f592d-112">Když zavoláte `DebugEvent`, proces bude ve stavu raw, zastaveno a ladění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f592d-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="f592d-113">Proces nebude synchronizován.</span><span class="sxs-lookup"><span data-stu-id="f592d-113">The process will not be synchronized.</span></span> <span data-ttu-id="f592d-114">Automaticky zadá synchronizovaný stav, pokud je to nutné k tomu, aby splňoval požadavky na informace o spravovaném kódu, což může vést k dalším vnořeným zpětným voláním `DebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="f592d-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="f592d-115">Před pokračováním procesu zavolejte [ICorDebugProcess:: ClearCurrentException –](icordebugprocess-clearcurrentexception-method.md) na proces, aby se ignorovala událost výjimky.</span><span class="sxs-lookup"><span data-stu-id="f592d-115">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="f592d-116">Volání této metody odesílá DBG_CONTINUE místo DBG_EXCEPTION_NOT_HANDLED v žádosti o pokračování a automaticky vymaže zarážky mimo pásmo a výjimky s jedním krokem.</span><span class="sxs-lookup"><span data-stu-id="f592d-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="f592d-117">Události mimo pásmo můžou přijít kdykoli, a to i v případě, že se vyladěná aplikace zastaví a když už existuje zbývající událost v pásmu.</span><span class="sxs-lookup"><span data-stu-id="f592d-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="f592d-118">V .NET Framework verze 2,0 by měl ladicí program hned pokračovat v minulosti událost zarážky mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="f592d-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="f592d-119">Ladicí program by měl používat metody [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md) a [ICorDebugProcess2:: ClearUnmanagedBreakpoint –](icordebugprocess2-clearunmanagedbreakpoint-method.md) k přidávání a odebírání zarážek.</span><span class="sxs-lookup"><span data-stu-id="f592d-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="f592d-120">Tyto metody přeskočí všechny zarážky mimo pásmo automaticky.</span><span class="sxs-lookup"><span data-stu-id="f592d-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="f592d-121">Proto musí být pouze nezpracované zarážky mimo pásmo, které byly odeslány, nezpracované zarážky, které jsou již v datovém proudu instrukcí, například volání funkce Win32 `DebugBreak`.</span><span class="sxs-lookup"><span data-stu-id="f592d-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="f592d-122">Nepokoušejte se používat `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext –](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext –](icordebugprocess-setthreadcontext-method.md)nebo jakéhokoli jiného člena [rozhraní API pro ladění](index.md).</span><span class="sxs-lookup"><span data-stu-id="f592d-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f592d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f592d-123">Requirements</span></span>  
 <span data-ttu-id="f592d-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f592d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f592d-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f592d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f592d-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f592d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f592d-127">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f592d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f592d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f592d-128">See also</span></span>

- [<span data-ttu-id="f592d-129">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f592d-129">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
