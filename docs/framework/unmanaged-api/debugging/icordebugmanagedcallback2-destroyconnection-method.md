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
ms.openlocfilehash: c5527f3bd0b04857a1ebc520016b81ddbe3c23f8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208847"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="0c659-102">ICorDebugManagedCallback2::DestroyConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="0c659-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="0c659-103">Oznamuje ladicímu programu, že zadané připojení bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="0c659-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c659-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c659-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c659-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c659-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="0c659-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces obsahující připojení, které bylo zničeno.</span><span class="sxs-lookup"><span data-stu-id="0c659-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="0c659-107">pro ID připojení, které bylo zničeno.</span><span class="sxs-lookup"><span data-stu-id="0c659-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c659-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c659-108">Remarks</span></span>  
 <span data-ttu-id="0c659-109">`DestroyConnection`Zpětné volání bude vyvoláno, když hostitel zavolá [ICLRDebugManager:: EndConnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) v [rozhraní API hostování](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="0c659-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c659-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c659-110">Requirements</span></span>  
 <span data-ttu-id="0c659-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c659-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c659-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c659-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c659-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c659-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c659-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c659-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c659-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c659-115">See also</span></span>

- [<span data-ttu-id="0c659-116">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c659-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="0c659-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c659-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
