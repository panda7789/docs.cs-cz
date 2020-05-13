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
ms.openlocfilehash: d8e62499a813419ecc30924624da553ca9f2c7b2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213397"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="23660-102">ICorDebugManagedCallback::Breakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="23660-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="23660-103">Upozorní ladicí program, když dojde k zarážce.</span><span class="sxs-lookup"><span data-stu-id="23660-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23660-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23660-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23660-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23660-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="23660-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující zarážku.</span><span class="sxs-lookup"><span data-stu-id="23660-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="23660-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, které obsahuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="23660-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="23660-108">pro Ukazatel na objekt ICorDebugBreakpoint, který představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="23660-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23660-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23660-109">Requirements</span></span>  
 <span data-ttu-id="23660-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23660-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23660-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="23660-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23660-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="23660-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23660-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23660-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23660-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="23660-114">See also</span></span>

- [<span data-ttu-id="23660-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23660-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
