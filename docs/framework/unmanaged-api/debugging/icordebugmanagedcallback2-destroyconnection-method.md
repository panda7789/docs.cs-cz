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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6d4acb7d1156babbd698201c5aea2810644db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415399"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="f79a4-102">ICorDebugManagedCallback2::DestroyConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="f79a4-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="f79a4-103">Upozorní ladicí program, že zadané připojení se ukončilo.</span><span class="sxs-lookup"><span data-stu-id="f79a4-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f79a4-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f79a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f79a4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f79a4-106">[v] Ukazatel na ICorDebugProcess objekt, který představuje proces obsahující na připojení, byl zničen.</span><span class="sxs-lookup"><span data-stu-id="f79a4-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="f79a4-107">[v] ID připojení, který byl zničen.</span><span class="sxs-lookup"><span data-stu-id="f79a4-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f79a4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f79a4-108">Remarks</span></span>  
 <span data-ttu-id="f79a4-109">A `DestroyConnection` zpětného volání budou aktivována, jestliže hostitel volá [iclrdebugmanager::endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) v [hostování rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="f79a4-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f79a4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f79a4-110">Requirements</span></span>  
 <span data-ttu-id="f79a4-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f79a4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f79a4-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f79a4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f79a4-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f79a4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f79a4-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f79a4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79a4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f79a4-115">See Also</span></span>  
 [<span data-ttu-id="f79a4-116">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f79a4-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="f79a4-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f79a4-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
