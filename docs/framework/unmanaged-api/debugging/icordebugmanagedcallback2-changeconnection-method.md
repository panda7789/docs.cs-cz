---
title: ICorDebugManagedCallback2::ChangeConnection – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8a8f84d3dfd8f1e64197078d7e20d2aebef2323
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761220"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="62205-102">ICorDebugManagedCallback2::ChangeConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="62205-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="62205-103">Upozorní ladicího programu, že se změnila sadu úkolů přidružených k zadané připojení.</span><span class="sxs-lookup"><span data-stu-id="62205-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62205-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62205-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62205-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62205-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="62205-106">[in] Ukazatel na objekt "ICorDebugProcess", který reprezentuje proces obsahující připojení, která se změnila.</span><span class="sxs-lookup"><span data-stu-id="62205-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="62205-107">[in] ID připojení, která se změnila.</span><span class="sxs-lookup"><span data-stu-id="62205-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62205-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62205-108">Remarks</span></span>  
 <span data-ttu-id="62205-109">A `ChangeConnection` aktivuje zpětného volání v některém z následujících případech:</span><span class="sxs-lookup"><span data-stu-id="62205-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="62205-110">Pokud ladicí program připojí k procesu, který obsahuje připojení.</span><span class="sxs-lookup"><span data-stu-id="62205-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="62205-111">V takovém případě modul runtime bude generovat a odeslání [icordebugmanagedcallback2::createconnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) událostí a `ChangeConnection` události pro každé připojení v procesu.</span><span class="sxs-lookup"><span data-stu-id="62205-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="62205-112">A `ChangeConnection` vygenerování události pro každé existující připojení, bez ohledu na to, zda toto připojení sady úloh změnila od jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="62205-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="62205-113">Když hostitel volá [iclrdebugmanager::setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) v [API pro hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="62205-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="62205-114">Ladicí program byste nechat zkontrolovat všechna vlákna v procesu, aby se získaly nové změny.</span><span class="sxs-lookup"><span data-stu-id="62205-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62205-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62205-115">Requirements</span></span>  
 <span data-ttu-id="62205-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62205-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62205-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62205-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62205-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62205-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62205-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62205-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62205-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62205-120">See also</span></span>

- [<span data-ttu-id="62205-121">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62205-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="62205-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62205-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
