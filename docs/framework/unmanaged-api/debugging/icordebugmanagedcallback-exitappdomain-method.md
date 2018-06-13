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
ms.openlocfilehash: f909eddde182a73709be9ca5cafec6285db46b4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412851"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="d534c-102">ICorDebugManagedCallback::ExitAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="d534c-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="d534c-103">Upozorní ladicí program, aby byl ukončen domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d534c-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d534c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d534c-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d534c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d534c-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d534c-106">[v] Ukazatel na ICorDebugProcess objekt, který představuje proces, který obsahuje doménu dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d534c-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="d534c-107">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, který byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="d534c-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d534c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d534c-108">Requirements</span></span>  
 <span data-ttu-id="d534c-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d534c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d534c-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d534c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d534c-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d534c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d534c-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d534c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d534c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d534c-113">See Also</span></span>  
 [<span data-ttu-id="d534c-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d534c-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
