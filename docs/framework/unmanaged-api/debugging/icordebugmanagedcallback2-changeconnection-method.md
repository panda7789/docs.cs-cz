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
ms.openlocfilehash: 2c6ed14f9238d653b15d26dec9d954c05238817c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213449"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="40359-102">ICorDebugManagedCallback2::ChangeConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="40359-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="40359-103">Oznamuje ladicímu programu, že se změnila sada úloh přidružených k zadanému připojení.</span><span class="sxs-lookup"><span data-stu-id="40359-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40359-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40359-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40359-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40359-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="40359-106">pro Ukazatel na objekt "ICorDebugProcess", který představuje proces obsahující připojení, které bylo změněno.</span><span class="sxs-lookup"><span data-stu-id="40359-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="40359-107">pro ID připojení, které bylo změněno.</span><span class="sxs-lookup"><span data-stu-id="40359-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40359-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40359-108">Remarks</span></span>  
 <span data-ttu-id="40359-109">`ChangeConnection`Zpětné volání bude aktivováno v jednom z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="40359-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="40359-110">Když se ladicí program připojí k procesu, který obsahuje připojení.</span><span class="sxs-lookup"><span data-stu-id="40359-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="40359-111">V tomto případě modul runtime vygeneruje a odešle událost [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) a `ChangeConnection` událost pro každé připojení v procesu.</span><span class="sxs-lookup"><span data-stu-id="40359-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="40359-112">`ChangeConnection`Událost se generuje pro každé existující připojení, bez ohledu na to, jestli se od jejího vytvoření změnila sada úkolů daného připojení.</span><span class="sxs-lookup"><span data-stu-id="40359-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="40359-113">Když hostitel volá [ICLRDebugManager:: SetConnectionTasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) v [rozhraní API hostování](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="40359-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
 <span data-ttu-id="40359-114">Ladicí program by měl zkontrolovat všechny podprocesy v procesu a vybrat nové změny.</span><span class="sxs-lookup"><span data-stu-id="40359-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40359-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40359-115">Requirements</span></span>  
 <span data-ttu-id="40359-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40359-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40359-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40359-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40359-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40359-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40359-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40359-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40359-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="40359-120">See also</span></span>

- [<span data-ttu-id="40359-121">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40359-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="40359-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40359-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
