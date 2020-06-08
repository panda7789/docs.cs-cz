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
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501921"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="fa4e7-102">ICorDebugManagedCallback2::CreateConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="fa4e7-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="fa4e7-103">Oznamuje ladicímu programu, že bylo vytvořeno nové připojení.</span><span class="sxs-lookup"><span data-stu-id="fa4e7-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa4e7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa4e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa4e7-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="fa4e7-106">pro Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém bylo vytvořeno připojení</span><span class="sxs-lookup"><span data-stu-id="fa4e7-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="fa4e7-107">pro ID nového připojení</span><span class="sxs-lookup"><span data-stu-id="fa4e7-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="fa4e7-108">pro Ukazatel na název nového připojení.</span><span class="sxs-lookup"><span data-stu-id="fa4e7-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa4e7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa4e7-109">Remarks</span></span>  
 <span data-ttu-id="fa4e7-110">`CreateConnection`Zpětné volání bude aktivováno v jednom z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="fa4e7-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="fa4e7-111">Když se ladicí program připojí k procesu, který obsahuje připojení.</span><span class="sxs-lookup"><span data-stu-id="fa4e7-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="fa4e7-112">V tomto případě modul runtime vytvoří a odešle `CreateConnection` událost a událost [ICorDebugManagedCallback2:: ChangeConnection –](icordebugmanagedcallback2-changeconnection-method.md) pro každé připojení v procesu.</span><span class="sxs-lookup"><span data-stu-id="fa4e7-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="fa4e7-113">Když hostitel volá [ICLRDebugManager:: BeginConnection –](../hosting/iclrdebugmanager-beginconnection-method.md) v [rozhraní API hostování](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="fa4e7-113">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa4e7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa4e7-114">Requirements</span></span>  
 <span data-ttu-id="fa4e7-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa4e7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa4e7-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fa4e7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa4e7-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fa4e7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa4e7-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa4e7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4e7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa4e7-119">See also</span></span>

- [<span data-ttu-id="fa4e7-120">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa4e7-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="fa4e7-121">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa4e7-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
