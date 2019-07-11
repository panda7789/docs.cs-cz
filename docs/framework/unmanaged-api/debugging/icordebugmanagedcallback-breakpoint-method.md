---
title: ICorDebugManagedCallback::Breakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f49fac3951c130c3cf06b6861beb06b89c27dfb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759890"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="cf14d-102">ICorDebugManagedCallback::Breakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="cf14d-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="cf14d-103">Ladicí program upozorní, když zarážky.</span><span class="sxs-lookup"><span data-stu-id="cf14d-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf14d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf14d-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf14d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf14d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cf14d-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který obsahuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="cf14d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cf14d-107">[in] Ukazatel na objekt icordebugthread –, který představuje podproces, který obsahuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="cf14d-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="cf14d-108">[in] Ukazatel na objekt ICorDebugBreakpoint představující zarážku.</span><span class="sxs-lookup"><span data-stu-id="cf14d-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf14d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf14d-109">Requirements</span></span>  
 <span data-ttu-id="cf14d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf14d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf14d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf14d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf14d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf14d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf14d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf14d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf14d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf14d-114">See also</span></span>

- [<span data-ttu-id="cf14d-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf14d-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
