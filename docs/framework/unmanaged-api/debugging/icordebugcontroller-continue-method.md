---
title: ICorDebugController::Continue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62e2be44165472e2fbf368f61b865d39a5e9fc28
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395468"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="5cc65-102">ICorDebugController::Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="5cc65-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="5cc65-103">Pokračuje v provádění spravovaných vláken po volání [metody Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="5cc65-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="5cc65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cc65-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="5cc65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cc65-105">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="5cc65-106">pro Nastavte na `true`, pokud budete pokračovat v události mimo IP síť. v opačném případě nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="5cc65-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5cc65-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cc65-107">Remarks</span></span>

<span data-ttu-id="5cc65-108">`Continue` pokračuje v procesu po volání metody `ICorDebugController::Stop`.</span><span class="sxs-lookup"><span data-stu-id="5cc65-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="5cc65-109">Při ladění v kombinovaném režimu Nevolejte `Continue` ve vlákně události Win32, pokud nebudete pokračovat z události mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="5cc65-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="5cc65-110">Integrovaná *událost* je buď spravovaná událost, nebo normální nespravovanou událost, během které ladicí program podporuje interakci se spravovaným stavem procesu.</span><span class="sxs-lookup"><span data-stu-id="5cc65-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="5cc65-111">V tomto případě ladicí program obdrží zpětné volání [ICorDebugUnmanagedCallback –::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) s parametrem `fOutOfBand` nastaveným na `false`.</span><span class="sxs-lookup"><span data-stu-id="5cc65-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="5cc65-112">*Událost mimo pásmo* je nespravovaná událost, během které je interakce se spravovaným stavem procesu neproveditelná v době, kdy se proces zastavil kvůli události.</span><span class="sxs-lookup"><span data-stu-id="5cc65-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="5cc65-113">V tomto případě ladicí program obdrží zpětné volání `ICorDebugUnmanagedCallback::DebugEvent` s parametrem `fOutOfBand` nastaveným na `true`.</span><span class="sxs-lookup"><span data-stu-id="5cc65-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5cc65-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cc65-114">Requirements</span></span>

<span data-ttu-id="5cc65-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc65-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5cc65-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5cc65-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5cc65-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5cc65-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5cc65-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc65-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
