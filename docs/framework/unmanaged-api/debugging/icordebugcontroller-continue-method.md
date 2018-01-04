---
title: "ICorDebugController::Continue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Continue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6a96145801aa8ef6482e30e9c00b763d2501f36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="269d7-102">ICorDebugController::Continue – metoda</span><span class="sxs-lookup"><span data-stu-id="269d7-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="269d7-103">Pokračuje v provádění spravovaných vláknech po volání [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="269d7-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="269d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="269d7-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="269d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="269d7-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="269d7-106">[v] Nastavte na `true` Pokud budete pokračovat z události out-of-band; jinak hodnota nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="269d7-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="269d7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="269d7-107">Remarks</span></span>  
 <span data-ttu-id="269d7-108">`Continue`pokračuje v procesu po volání `ICorDebugController::Stop` metoda.</span><span class="sxs-lookup"><span data-stu-id="269d7-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="269d7-109">Při provádění modulu ladění ve smíšeném režimu, nevolejte `Continue` na Win32 událostí vláken, pokud jsou pokračováním z out-of-band události.</span><span class="sxs-lookup"><span data-stu-id="269d7-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="269d7-110">*Integrované událostí* spravované události nebo normální nespravované událostí, během které ladicí program podporuje interakci s spravované stavu procesu.</span><span class="sxs-lookup"><span data-stu-id="269d7-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="269d7-111">V takovém případě obdrží ladicí program [icordebugunmanagedcallback::debugevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) zpětné volání s jeho `fOutOfBand` parametr nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="269d7-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="269d7-112">*Out-of-band událostí* je událost nespravované, během kterého není možné interakci s spravované stav procesu, když je ukončen z důvodu události.</span><span class="sxs-lookup"><span data-stu-id="269d7-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="269d7-113">V takovém případě obdrží ladicí program `ICorDebugUnmanagedCallback::DebugEvent` zpětné volání s jeho `fOutOfBand` parametr nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="269d7-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="269d7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="269d7-114">Requirements</span></span>  
 <span data-ttu-id="269d7-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="269d7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="269d7-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="269d7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="269d7-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="269d7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="269d7-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="269d7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269d7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="269d7-119">See Also</span></span>  
 
