---
title: ICorDebugManagedCallback::ExitAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aed6ccd938761385aafd21802829bd741847b4ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110237"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="14862-102">ICorDebugManagedCallback::ExitAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="14862-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="14862-103">Upozorní ladicího programu, že byl ukončen domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="14862-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14862-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14862-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14862-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14862-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="14862-106">[in] Ukazatel na objekt ICorDebugProcess, který představuje proces, který obsahuje doménu dané aplikace.</span><span class="sxs-lookup"><span data-stu-id="14862-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="14862-107">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="14862-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14862-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14862-108">Requirements</span></span>  
 <span data-ttu-id="14862-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14862-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14862-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14862-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14862-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14862-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14862-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14862-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14862-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14862-113">See also</span></span>

- [<span data-ttu-id="14862-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14862-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
