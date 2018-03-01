---
title: "ICorDebugManagedCallback2::ChangeConnection – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ba7e84c11f2fc8619b7046e222a742ee3298554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="a72d3-102">ICorDebugManagedCallback2::ChangeConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="a72d3-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="a72d3-103">Upozorní ladicí program, že se změnila sadu úloh, které jsou přidružené k zadané připojení.</span><span class="sxs-lookup"><span data-stu-id="a72d3-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a72d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a72d3-104">Syntax</span></span>  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a72d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a72d3-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a72d3-106">[v] Ukazatel na objekt "ICorDebugProcess", který představuje proces obsahující připojení, který změnil.</span><span class="sxs-lookup"><span data-stu-id="a72d3-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="a72d3-107">[v] ID připojení, který změnil.</span><span class="sxs-lookup"><span data-stu-id="a72d3-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a72d3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a72d3-108">Remarks</span></span>  
 <span data-ttu-id="a72d3-109">A `ChangeConnection` zpětného volání nebudou vydány v některém z následujících případech:</span><span class="sxs-lookup"><span data-stu-id="a72d3-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="a72d3-110">Když ladicí program připojí k procesu, který obsahuje připojení.</span><span class="sxs-lookup"><span data-stu-id="a72d3-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="a72d3-111">V takovém případě bude modulu runtime generování a odesílání [icordebugmanagedcallback2::createconnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) událostí a `ChangeConnection` událost pro každé připojení v procesu.</span><span class="sxs-lookup"><span data-stu-id="a72d3-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="a72d3-112">A `ChangeConnection` se vyvolá událost pro každý existující připojení, bez ohledu na to, jestli toto připojení sadu úloh se změnil od svého vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a72d3-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
-   <span data-ttu-id="a72d3-113">Když hostitel volá [iclrdebugmanager::setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) v [hostování rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="a72d3-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="a72d3-114">Ladicí program by měl kontrolu všech vláken v procesu vybrat nové změny.</span><span class="sxs-lookup"><span data-stu-id="a72d3-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a72d3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a72d3-115">Requirements</span></span>  
 <span data-ttu-id="a72d3-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a72d3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a72d3-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a72d3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a72d3-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a72d3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a72d3-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a72d3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a72d3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a72d3-120">See Also</span></span>  
 [<span data-ttu-id="a72d3-121">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a72d3-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="a72d3-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a72d3-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
