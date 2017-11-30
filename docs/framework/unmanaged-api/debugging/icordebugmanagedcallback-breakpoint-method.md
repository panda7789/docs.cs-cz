---
title: "ICorDebugManagedCallback::Breakpoint – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Breakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 081e5bf9f119e1a2f2012166a5b27b34718751bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="34c00-102">ICorDebugManagedCallback::Breakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="34c00-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="34c00-103">Ladicí program upozorní, když je došlo zarážky.</span><span class="sxs-lookup"><span data-stu-id="34c00-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34c00-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34c00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34c00-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="34c00-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, která obsahuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="34c00-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="34c00-107">[v] Ukazatel na ICorDebugThread objekt, který představuje vlákno, která obsahuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="34c00-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="34c00-108">[v] Ukazatel na ICorDebugBreakpoint objekt, který představuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="34c00-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34c00-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34c00-109">Requirements</span></span>  
 <span data-ttu-id="34c00-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34c00-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34c00-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34c00-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34c00-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34c00-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34c00-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34c00-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c00-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="34c00-114">See Also</span></span>  
 [<span data-ttu-id="34c00-115">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="34c00-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
