---
title: "ICorDebugManagedCallback::ExitAppDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07f76d8add6c8b0e44eba241b7787b8e8a2de570
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="413e6-102">ICorDebugManagedCallback::ExitAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="413e6-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="413e6-103">Upozorní ladicí program, aby byl ukončen domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="413e6-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="413e6-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="413e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="413e6-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="413e6-106">[v] Ukazatel na ICorDebugProcess objekt, který představuje proces, který obsahuje doménu dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="413e6-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="413e6-107">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, který byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="413e6-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="413e6-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="413e6-108">Requirements</span></span>  
 <span data-ttu-id="413e6-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="413e6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="413e6-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="413e6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="413e6-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="413e6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="413e6-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="413e6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413e6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="413e6-113">See Also</span></span>  
 [<span data-ttu-id="413e6-114">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="413e6-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
