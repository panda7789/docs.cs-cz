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
ms.openlocfilehash: dae04e1809c1bb3260461086a4953b8b4e5cce52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122575"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="b4230-102">ICorDebugManagedCallback::BreakpointSetError – metoda</span><span class="sxs-lookup"><span data-stu-id="b4230-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="b4230-103">Oznamuje ladicímu programu, že modul CLR (Common Language Runtime) nedokázal přesně navazovat zarážku, která byla nastavena předtím, než byla funkce kompilována za běhu (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="b4230-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4230-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4230-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4230-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4230-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b4230-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující nevázanou zarážku.</span><span class="sxs-lookup"><span data-stu-id="b4230-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b4230-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno obsahující nevázanou zarážku.</span><span class="sxs-lookup"><span data-stu-id="b4230-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="b4230-108">pro Ukazatel na objekt ICorDebugBreakpoint, který představuje nevázanou zarážku.</span><span class="sxs-lookup"><span data-stu-id="b4230-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="b4230-109">pro Celé číslo, které označuje chybu.</span><span class="sxs-lookup"><span data-stu-id="b4230-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4230-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4230-110">Remarks</span></span>  
 <span data-ttu-id="b4230-111">Tato zarážka nebude nikdy dosaženo.</span><span class="sxs-lookup"><span data-stu-id="b4230-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="b4230-112">Ladicí program by měl ho deaktivovat a znovu vytvořit.</span><span class="sxs-lookup"><span data-stu-id="b4230-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4230-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4230-113">Requirements</span></span>  
 <span data-ttu-id="b4230-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4230-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4230-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4230-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4230-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4230-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4230-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4230-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4230-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4230-118">See also</span></span>

- [<span data-ttu-id="b4230-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4230-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
