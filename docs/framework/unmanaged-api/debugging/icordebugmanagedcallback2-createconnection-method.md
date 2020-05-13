---
title: ICorDebugManagedCallback2::CreateConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: 51d34e68851bc6a60d25f643f63d112396abdc4e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209068"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="85e7b-102">ICorDebugManagedCallback2::CreateConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="85e7b-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="85e7b-103">Oznamuje ladicímu programu, že bylo vytvořeno nové připojení.</span><span class="sxs-lookup"><span data-stu-id="85e7b-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85e7b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85e7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85e7b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="85e7b-106">pro Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém bylo vytvořeno připojení</span><span class="sxs-lookup"><span data-stu-id="85e7b-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="85e7b-107">pro ID nového připojení</span><span class="sxs-lookup"><span data-stu-id="85e7b-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="85e7b-108">pro Ukazatel na název nového připojení.</span><span class="sxs-lookup"><span data-stu-id="85e7b-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e7b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85e7b-109">Remarks</span></span>  
 <span data-ttu-id="85e7b-110">`CreateConnection`Zpětné volání bude aktivováno v jednom z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="85e7b-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="85e7b-111">Když se ladicí program připojí k procesu, který obsahuje připojení.</span><span class="sxs-lookup"><span data-stu-id="85e7b-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="85e7b-112">V tomto případě modul runtime vytvoří a odešle `CreateConnection` událost a událost [ICorDebugManagedCallback2:: ChangeConnection –](icordebugmanagedcallback2-changeconnection-method.md) pro každé připojení v procesu.</span><span class="sxs-lookup"><span data-stu-id="85e7b-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="85e7b-113">Když hostitel volá [ICLRDebugManager:: BeginConnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) v [rozhraní API hostování](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="85e7b-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85e7b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85e7b-114">Requirements</span></span>  
 <span data-ttu-id="85e7b-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85e7b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85e7b-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85e7b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85e7b-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85e7b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85e7b-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e7b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e7b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="85e7b-119">See also</span></span>

- [<span data-ttu-id="85e7b-120">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85e7b-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="85e7b-121">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85e7b-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
