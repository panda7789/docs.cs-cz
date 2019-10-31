---
title: ICorDebugManagedCallback2::DestroyConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: a64df9f821021547efd08045e9f67fee25173e5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137441"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="db453-102">ICorDebugManagedCallback2::DestroyConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="db453-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="db453-103">Oznamuje ladicímu programu, že zadané připojení bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="db453-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db453-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db453-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db453-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db453-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="db453-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces obsahující připojení, které bylo zničeno.</span><span class="sxs-lookup"><span data-stu-id="db453-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="db453-107">pro ID připojení, které bylo zničeno.</span><span class="sxs-lookup"><span data-stu-id="db453-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db453-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db453-108">Remarks</span></span>  
 <span data-ttu-id="db453-109">Pokud hostitel volá [ICLRDebugManager:: EndConnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) v [rozhraní API pro hostování](../../../../docs/framework/unmanaged-api/hosting/index.md), bude vyvolána zpětná volání `DestroyConnection`.</span><span class="sxs-lookup"><span data-stu-id="db453-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db453-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db453-110">Requirements</span></span>  
 <span data-ttu-id="db453-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db453-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db453-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db453-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db453-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db453-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db453-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db453-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db453-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db453-115">See also</span></span>

- [<span data-ttu-id="db453-116">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db453-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="db453-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db453-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
