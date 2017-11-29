---
title: "ICorDebugManagedCallback2::CreateConnection – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.CreateConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 716321508c18a415dc8e5c1c3e7e350deaf00a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="7d32c-102">ICorDebugManagedCallback2::CreateConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="7d32c-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="7d32c-103">Upozorní ladicího programu vytvořený nové připojení.</span><span class="sxs-lookup"><span data-stu-id="7d32c-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d32c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d32c-104">Syntax</span></span>  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d32c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d32c-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7d32c-106">[v] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém byla vytvořena připojení</span><span class="sxs-lookup"><span data-stu-id="7d32c-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="7d32c-107">[v] ID nové připojení.</span><span class="sxs-lookup"><span data-stu-id="7d32c-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="7d32c-108">[v] Ukazatel na název nového připojení.</span><span class="sxs-lookup"><span data-stu-id="7d32c-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d32c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d32c-109">Remarks</span></span>  
 <span data-ttu-id="7d32c-110">A `CreateConnection` zpětného volání nebudou vydány v některém z následujících případech:</span><span class="sxs-lookup"><span data-stu-id="7d32c-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="7d32c-111">Když ladicí program připojí k procesu, který obsahuje připojení.</span><span class="sxs-lookup"><span data-stu-id="7d32c-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="7d32c-112">V takovém případě bude modulu runtime generování a odesílání `CreateConnection` událostí a [icordebugmanagedcallback2::changeconnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) událost pro každé připojení v procesu.</span><span class="sxs-lookup"><span data-stu-id="7d32c-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
-   <span data-ttu-id="7d32c-113">Když hostitel volá [iclrdebugmanager::beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) v [hostování rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="7d32c-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d32c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d32c-114">Requirements</span></span>  
 <span data-ttu-id="7d32c-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d32c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d32c-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d32c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d32c-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d32c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d32c-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d32c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d32c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d32c-119">See Also</span></span>  
 [<span data-ttu-id="7d32c-120">ICorDebugManagedCallback2 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d32c-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="7d32c-121">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d32c-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
