---
title: "ICLRDebugManager::EndConnection – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.EndConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 114f2217d22fc270b03d271db4acc44f0edbcca8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="9a06a-102">ICLRDebugManager::EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="9a06a-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="9a06a-103">Odebere přidružení mezi seznamu úloh a identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="9a06a-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a06a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a06a-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a06a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a06a-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="9a06a-106">[v] Identifikátor specifický pro hostitele pro připojení a přidružené seznamu běžných úloh language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9a06a-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a06a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9a06a-107">Return Value</span></span>  
  
|<span data-ttu-id="9a06a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a06a-108">HRESULT</span></span>|<span data-ttu-id="9a06a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9a06a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a06a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a06a-110">S_OK</span></span>|<span data-ttu-id="9a06a-111">`EndConnection`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9a06a-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="9a06a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a06a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a06a-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9a06a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a06a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a06a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a06a-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9a06a-115">The call timed out.</span></span>|  
|<span data-ttu-id="9a06a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a06a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a06a-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9a06a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a06a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a06a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a06a-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9a06a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a06a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a06a-120">E_FAIL</span></span>|<span data-ttu-id="9a06a-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9a06a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a06a-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9a06a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a06a-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9a06a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a06a-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9a06a-124">E_INVALIDARG</span></span>|<span data-ttu-id="9a06a-125">[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) se nikdy volat pomocí `dwConnectionId`, nebo `dwConnectionId` byl nula.</span><span class="sxs-lookup"><span data-stu-id="9a06a-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a06a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a06a-126">Remarks</span></span>  
 <span data-ttu-id="9a06a-127">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, [setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), a `EndConnection`, pro přidružení s identifikátory a popisné názvy seznam úloh.</span><span class="sxs-lookup"><span data-stu-id="9a06a-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a06a-128">Tyto tři metody musí být voláno v určitém pořadí pro jednotlivé skupiny úloh.</span><span class="sxs-lookup"><span data-stu-id="9a06a-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="9a06a-129">`BeginConnection`je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="9a06a-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="9a06a-130">`SetConnectionTasks`je volána vedle zajistit sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="9a06a-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="9a06a-131">`EndConnection`je volána poslední k odstranění přidružení mezi seznamu úloh a identifikátor a popisný název. Však mohou být vnořené volání pro různá připojení.</span><span class="sxs-lookup"><span data-stu-id="9a06a-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a06a-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a06a-132">Requirements</span></span>  
 <span data-ttu-id="9a06a-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a06a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a06a-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a06a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a06a-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a06a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a06a-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a06a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a06a-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a06a-137">See Also</span></span>  
 [<span data-ttu-id="9a06a-138">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a06a-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9a06a-139">Iclrdebugmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a06a-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="9a06a-140">Beginconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="9a06a-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="9a06a-141">Setconnectiontasks – metoda</span><span class="sxs-lookup"><span data-stu-id="9a06a-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="9a06a-142">Ihostcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a06a-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
