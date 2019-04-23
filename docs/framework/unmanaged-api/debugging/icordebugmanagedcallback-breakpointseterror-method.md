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
ms.openlocfilehash: 27d5b8e0127971cc3a46560590fd9d95f0ffd1f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151018"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="0e62f-102">ICorDebugManagedCallback::BreakpointSetError – metoda</span><span class="sxs-lookup"><span data-stu-id="0e62f-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="0e62f-103">Upozorní ladicí program nemohl modul common language runtime přesně svázat zarážku, která byla nastavena před funkci just-in-time (JIT) zkompilována.</span><span class="sxs-lookup"><span data-stu-id="0e62f-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e62f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e62f-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e62f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e62f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0e62f-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který obsahuje nevázaného zarážku.</span><span class="sxs-lookup"><span data-stu-id="0e62f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0e62f-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, které obsahuje nevázaného zarážku.</span><span class="sxs-lookup"><span data-stu-id="0e62f-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="0e62f-108">[in] Ukazatel na objekt ICorDebugBreakpoint představující odvázat zarážku.</span><span class="sxs-lookup"><span data-stu-id="0e62f-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="0e62f-109">[in] Celé číslo, které označuje chybu.</span><span class="sxs-lookup"><span data-stu-id="0e62f-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e62f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e62f-110">Remarks</span></span>  
 <span data-ttu-id="0e62f-111">Daném bude nikdy dosaženo zarážkou.</span><span class="sxs-lookup"><span data-stu-id="0e62f-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="0e62f-112">Ladicí program by měl deaktivovat a znovu se připojit.</span><span class="sxs-lookup"><span data-stu-id="0e62f-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e62f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e62f-113">Requirements</span></span>  
 <span data-ttu-id="0e62f-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e62f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e62f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e62f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e62f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e62f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e62f-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e62f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e62f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e62f-118">See also</span></span>

- [<span data-ttu-id="0e62f-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e62f-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
