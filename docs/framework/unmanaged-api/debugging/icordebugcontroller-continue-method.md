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
ms.openlocfilehash: 7eacffe5769bc77ab626f6adbc99db1137da565f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749667"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="e7ebc-102">ICorDebugController::Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="e7ebc-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="e7ebc-103">Pokračuje v provádění spravovaná vlákna po volání [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="e7ebc-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ebc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7ebc-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7ebc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7ebc-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="e7ebc-106">[in] Nastavte na `true` Pokud budete pokračovat z události out-of-band; v opačném případě nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="e7ebc-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7ebc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7ebc-107">Remarks</span></span>  
 <span data-ttu-id="e7ebc-108">`Continue` pokračuje v procesu po volání `ICorDebugController::Stop` metody.</span><span class="sxs-lookup"><span data-stu-id="e7ebc-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="e7ebc-109">Při ladění ve smíšeném režimu, nevolejte `Continue` na Win32 události vlákna, pokud se dál pokračuje z out-of-band události.</span><span class="sxs-lookup"><span data-stu-id="e7ebc-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="e7ebc-110">*Integrovaných událostí* je spravovaná událost nebo normální nespravované události, během které ladicí program podporuje interakci s spravovaného stavu zpracování.</span><span class="sxs-lookup"><span data-stu-id="e7ebc-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="e7ebc-111">V takovém případě ladicí program přijímá [icordebugunmanagedcallback::debugevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) zpětného volání s jeho `fOutOfBand` parametr nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="e7ebc-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="e7ebc-112">*Out-of-band události* nespravované události během které je možné interakce s spravované stav procesu, zatímco je ukončen z důvodu události.</span><span class="sxs-lookup"><span data-stu-id="e7ebc-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="e7ebc-113">V takovém případě ladicí program přijímá `ICorDebugUnmanagedCallback::DebugEvent` zpětného volání s jeho `fOutOfBand` parametr nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="e7ebc-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7ebc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7ebc-114">Requirements</span></span>  
 <span data-ttu-id="e7ebc-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7ebc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7ebc-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7ebc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7ebc-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7ebc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7ebc-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7ebc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ebc-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7ebc-119">See also</span></span>
