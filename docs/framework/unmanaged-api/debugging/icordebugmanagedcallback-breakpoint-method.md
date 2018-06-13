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
ms.openlocfilehash: 381fdecfb2cb194cd1eb00a5b55db6fb89eeebbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413914"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="9dc91-102">ICorDebugManagedCallback::Breakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="9dc91-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="9dc91-103">Ladicí program upozorní, když je došlo zarážky.</span><span class="sxs-lookup"><span data-stu-id="9dc91-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dc91-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9dc91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9dc91-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9dc91-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, která obsahuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="9dc91-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9dc91-107">[v] Ukazatel na ICorDebugThread objekt, který představuje vlákno, která obsahuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="9dc91-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="9dc91-108">[v] Ukazatel na ICorDebugBreakpoint objekt, který představuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="9dc91-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc91-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9dc91-109">Requirements</span></span>  
 <span data-ttu-id="9dc91-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc91-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc91-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dc91-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dc91-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dc91-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dc91-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc91-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc91-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dc91-114">See Also</span></span>  
 [<span data-ttu-id="9dc91-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9dc91-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
