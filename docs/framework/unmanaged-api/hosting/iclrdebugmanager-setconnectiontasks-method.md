---
title: ICLRDebugManager::SetConnectionTasks – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aeb66e6c5b8ce6312ec9fad65d79e32a4fbe0576
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773087"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="185be-102">ICLRDebugManager::SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="185be-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="185be-103">Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="185be-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="185be-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="185be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="185be-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="185be-106">[in] Identifikátor konkrétního hostitele pro připojení ke které chcete přidružit `ppCLRTask` pole.</span><span class="sxs-lookup"><span data-stu-id="185be-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="185be-107">[in] Počet členů `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="185be-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="185be-108">Tato hodnota musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="185be-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="185be-109">[in] Pole `ICLRTask` ukazatele pro přidružení k připojení identifikovaný `id`.</span><span class="sxs-lookup"><span data-stu-id="185be-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="185be-110">Toto pole musí obsahovat alespoň jeden člen.</span><span class="sxs-lookup"><span data-stu-id="185be-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="185be-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="185be-111">Return Value</span></span>  
  
|<span data-ttu-id="185be-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="185be-112">HRESULT</span></span>|<span data-ttu-id="185be-113">Popis</span><span class="sxs-lookup"><span data-stu-id="185be-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="185be-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="185be-114">S_OK</span></span>|<span data-ttu-id="185be-115">`SetConnectionTasks` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="185be-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="185be-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="185be-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="185be-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="185be-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="185be-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="185be-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="185be-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="185be-119">The call timed out.</span></span>|  
|<span data-ttu-id="185be-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="185be-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="185be-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="185be-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="185be-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="185be-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="185be-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="185be-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="185be-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="185be-124">E_FAIL</span></span>|<span data-ttu-id="185be-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="185be-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="185be-126">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="185be-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="185be-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="185be-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="185be-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="185be-128">E_INVALIDARG</span></span>|<span data-ttu-id="185be-129">[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nebyla volána pomocí této hodnoty `id`, nebo `dwCount` nebo `id` se žádný nebo jeden z prvků `ppCLRTask` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="185be-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="185be-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="185be-130">Remarks</span></span>  
 <span data-ttu-id="185be-131">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, `SetConnectionTasks`, a [endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), pro seznamy úloh přidružení s identifikátory a popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="185be-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="185be-132">Tyto tři metody musí být volána v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="185be-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="185be-133">`BeginConnection` je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="185be-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="185be-134">`SetConnectionTasks` je volána dále k poskytování sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="185be-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="185be-135">`EndConnection` Chcete-li odebrat přidružení seznamu úkolů a identifikátor a popisný název se nazývá poslední. Volání pro různá připojení však mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="185be-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185be-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="185be-136">Requirements</span></span>  
 <span data-ttu-id="185be-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="185be-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="185be-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="185be-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="185be-139">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="185be-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="185be-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="185be-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185be-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="185be-141">See also</span></span>

- [<span data-ttu-id="185be-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="185be-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="185be-143">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="185be-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="185be-144">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="185be-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="185be-145">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="185be-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="185be-146">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="185be-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
