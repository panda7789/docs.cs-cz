---
title: "ICLRDebugManager::SetConnectionTasks – metoda"
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
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09f7e47acfcfbde8d5d9724c3a37303f1a584adb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="db11a-102">ICLRDebugManager::SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="db11a-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="db11a-103">Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="db11a-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db11a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db11a-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db11a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db11a-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="db11a-106">[v] Identifikátor specifický pro hostitele pro připojení ke které chcete přidružit `ppCLRTask` pole.</span><span class="sxs-lookup"><span data-stu-id="db11a-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="db11a-107">[v] Počet členů `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="db11a-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="db11a-108">Toto číslo musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="db11a-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="db11a-109">[v] Pole `ICLRTask` ukazatele na přidružte připojení identifikovaný `id`.</span><span class="sxs-lookup"><span data-stu-id="db11a-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="db11a-110">Toto pole musí obsahovat alespoň jeden člen.</span><span class="sxs-lookup"><span data-stu-id="db11a-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db11a-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db11a-111">Return Value</span></span>  
  
|<span data-ttu-id="db11a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db11a-112">HRESULT</span></span>|<span data-ttu-id="db11a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="db11a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db11a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="db11a-114">S_OK</span></span>|<span data-ttu-id="db11a-115">`SetConnectionTasks`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="db11a-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="db11a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db11a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db11a-117">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="db11a-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db11a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db11a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db11a-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="db11a-119">The call timed out.</span></span>|  
|<span data-ttu-id="db11a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db11a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db11a-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="db11a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db11a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db11a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db11a-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="db11a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db11a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db11a-124">E_FAIL</span></span>|<span data-ttu-id="db11a-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="db11a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db11a-126">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="db11a-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db11a-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db11a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="db11a-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="db11a-128">E_INVALIDARG</span></span>|<span data-ttu-id="db11a-129">[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nebyla zavolána pomocí hodnota `id`, nebo `dwCount` nebo `id` je nula nebo jeden z elementů `ppCLRTask` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="db11a-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db11a-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db11a-130">Remarks</span></span>  
 <span data-ttu-id="db11a-131">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, `SetConnectionTasks`, a [endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), pro přidružení s identifikátory a popisné názvy seznam úloh.</span><span class="sxs-lookup"><span data-stu-id="db11a-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="db11a-132">Tyto tři metody musí být voláno v určitém pořadí pro jednotlivé skupiny úloh.</span><span class="sxs-lookup"><span data-stu-id="db11a-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="db11a-133">`BeginConnection`je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="db11a-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="db11a-134">`SetConnectionTasks`je volána vedle zajistit sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="db11a-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="db11a-135">`EndConnection`je volána poslední k odstranění přidružení mezi seznamu úloh a identifikátor a popisný název. Však mohou být vnořené volání pro různá připojení.</span><span class="sxs-lookup"><span data-stu-id="db11a-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db11a-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db11a-136">Requirements</span></span>  
 <span data-ttu-id="db11a-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db11a-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db11a-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db11a-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db11a-139">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db11a-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db11a-140">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db11a-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db11a-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="db11a-141">See Also</span></span>  
 [<span data-ttu-id="db11a-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db11a-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="db11a-143">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db11a-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="db11a-144">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="db11a-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="db11a-145">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="db11a-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="db11a-146">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db11a-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
