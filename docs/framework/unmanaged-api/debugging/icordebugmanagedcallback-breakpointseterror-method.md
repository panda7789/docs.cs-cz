---
title: ICorDebugManagedCallback::BreakpointSetError – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc437f63621c451c0af796513d4646fe0668c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418376"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="399f2-102">ICorDebugManagedCallback::BreakpointSetError – metoda</span><span class="sxs-lookup"><span data-stu-id="399f2-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="399f2-103">Upozorní ladicí program nemohl modul common language runtime pro vazbu přesně zarážku nastavený před funkci v běhu (JIT) zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="399f2-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="399f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="399f2-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="399f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="399f2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="399f2-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, která obsahuje nevázaný zarážek.</span><span class="sxs-lookup"><span data-stu-id="399f2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="399f2-107">[v] Ukazatel na ICorDebugThread objekt, který představuje vlákno, které obsahuje nevázaný zarážek.</span><span class="sxs-lookup"><span data-stu-id="399f2-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="399f2-108">[v] Ukazatel na ICorDebugBreakpoint objekt, který reprezentuje nevázaný zarážek.</span><span class="sxs-lookup"><span data-stu-id="399f2-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="399f2-109">[v] Celé číslo, které označuje chybu.</span><span class="sxs-lookup"><span data-stu-id="399f2-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="399f2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="399f2-110">Remarks</span></span>  
 <span data-ttu-id="399f2-111">Daný zarážek se nikdy se setkají.</span><span class="sxs-lookup"><span data-stu-id="399f2-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="399f2-112">Ladicí program by měl deaktivovat a znovu ji svázat.</span><span class="sxs-lookup"><span data-stu-id="399f2-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="399f2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="399f2-113">Requirements</span></span>  
 <span data-ttu-id="399f2-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="399f2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="399f2-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="399f2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="399f2-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="399f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="399f2-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="399f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399f2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="399f2-118">See Also</span></span>  
 [<span data-ttu-id="399f2-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="399f2-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
