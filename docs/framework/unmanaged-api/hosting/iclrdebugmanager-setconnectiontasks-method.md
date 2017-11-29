---
title: "ICLRDebugManager::SetConnectionTasks – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetConnectionTasks
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 354e876bf69a82bf1eb0ed3907a03e4b94d60f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="3545d-102">ICLRDebugManager::SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="3545d-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="3545d-103">Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="3545d-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3545d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3545d-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3545d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3545d-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="3545d-106">[v] Identifikátor specifický pro hostitele pro připojení ke které chcete přidružit `ppCLRTask` pole.</span><span class="sxs-lookup"><span data-stu-id="3545d-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="3545d-107">[v] Počet členů `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="3545d-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="3545d-108">Toto číslo musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="3545d-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="3545d-109">[v] Pole `ICLRTask` ukazatele na přidružte připojení identifikovaný `id`.</span><span class="sxs-lookup"><span data-stu-id="3545d-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="3545d-110">Toto pole musí obsahovat alespoň jeden člen.</span><span class="sxs-lookup"><span data-stu-id="3545d-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3545d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3545d-111">Return Value</span></span>  
  
|<span data-ttu-id="3545d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3545d-112">HRESULT</span></span>|<span data-ttu-id="3545d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3545d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3545d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3545d-114">S_OK</span></span>|<span data-ttu-id="3545d-115">`SetConnectionTasks`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3545d-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="3545d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3545d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3545d-117">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3545d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3545d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3545d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3545d-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3545d-119">The call timed out.</span></span>|  
|<span data-ttu-id="3545d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3545d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3545d-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="3545d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3545d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3545d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3545d-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="3545d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3545d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3545d-124">E_FAIL</span></span>|<span data-ttu-id="3545d-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="3545d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3545d-126">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3545d-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3545d-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3545d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3545d-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3545d-128">E_INVALIDARG</span></span>|<span data-ttu-id="3545d-129">[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nebyla zavolána pomocí hodnota `id`, nebo `dwCount` nebo `id` je nula nebo jeden z elementů `ppCLRTask` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3545d-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3545d-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3545d-130">Remarks</span></span>  
 <span data-ttu-id="3545d-131">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, `SetConnectionTasks`, a [endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), pro přidružení s identifikátory a popisné názvy seznam úloh.</span><span class="sxs-lookup"><span data-stu-id="3545d-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3545d-132">Tyto tři metody musí být voláno v určitém pořadí pro jednotlivé skupiny úloh.</span><span class="sxs-lookup"><span data-stu-id="3545d-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="3545d-133">`BeginConnection`je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="3545d-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="3545d-134">`SetConnectionTasks`je volána vedle zajistit sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="3545d-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="3545d-135">`EndConnection`je volána poslední k odstranění přidružení mezi seznamu úloh a identifikátor a popisný název. Však mohou být vnořené volání pro různá připojení.</span><span class="sxs-lookup"><span data-stu-id="3545d-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3545d-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3545d-136">Requirements</span></span>  
 <span data-ttu-id="3545d-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3545d-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3545d-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3545d-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3545d-139">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3545d-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3545d-140">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3545d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3545d-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="3545d-141">See Also</span></span>  
 [<span data-ttu-id="3545d-142">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3545d-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3545d-143">Iclrdebugmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3545d-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="3545d-144">Beginconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="3545d-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="3545d-145">Endconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="3545d-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="3545d-146">Ihostcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3545d-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
