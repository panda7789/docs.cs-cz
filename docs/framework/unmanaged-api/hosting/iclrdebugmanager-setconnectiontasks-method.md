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
ms.openlocfilehash: 81b6f009ea61294f398a21c4def927ef2609f32b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615739"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="62ff9-102">ICLRDebugManager::SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="62ff9-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="62ff9-103">Přidruží seznam instancí [ICLRTask](iclrtask-interface.md) s identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="62ff9-103">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ff9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62ff9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62ff9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62ff9-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="62ff9-106">pro Identifikátor konkrétního hostitele pro připojení, se kterým má být pole přidruženo `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="62ff9-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="62ff9-107">pro Počet členů `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="62ff9-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="62ff9-108">Toto číslo musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="62ff9-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="62ff9-109">pro Pole `ICLRTask` ukazatelů, které mají být spojeny s připojením, které identifikoval `id` .</span><span class="sxs-lookup"><span data-stu-id="62ff9-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="62ff9-110">Toto pole musí obsahovat alespoň jeden člen.</span><span class="sxs-lookup"><span data-stu-id="62ff9-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62ff9-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62ff9-111">Return Value</span></span>  
  
|<span data-ttu-id="62ff9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62ff9-112">HRESULT</span></span>|<span data-ttu-id="62ff9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="62ff9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62ff9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="62ff9-114">S_OK</span></span>|<span data-ttu-id="62ff9-115">`SetConnectionTasks`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="62ff9-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="62ff9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62ff9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62ff9-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="62ff9-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62ff9-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62ff9-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62ff9-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="62ff9-119">The call timed out.</span></span>|  
|<span data-ttu-id="62ff9-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62ff9-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62ff9-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="62ff9-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62ff9-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62ff9-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62ff9-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="62ff9-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62ff9-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62ff9-124">E_FAIL</span></span>|<span data-ttu-id="62ff9-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="62ff9-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62ff9-126">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="62ff9-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62ff9-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="62ff9-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="62ff9-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="62ff9-128">E_INVALIDARG</span></span>|<span data-ttu-id="62ff9-129">[BeginConnection –](iclrdebugmanager-beginconnection-method.md) se nevolala s použitím této hodnoty nebo `id` `dwCount` nebo `id` je nula nebo jeden z elementů má `ppCLRTask` hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="62ff9-129">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62ff9-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62ff9-130">Remarks</span></span>  
 <span data-ttu-id="62ff9-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody, `BeginConnection` , `SetConnectionTasks` a [EndConnection –](iclrdebugmanager-endconnection-method.md), pro přiřazování seznamů úkolů s identifikátory a popisnými názvy.</span><span class="sxs-lookup"><span data-stu-id="62ff9-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="62ff9-132">Tyto tři metody musí být volány v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="62ff9-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="62ff9-133">`BeginConnection`se označuje jako první, aby se navázalo nové připojení.</span><span class="sxs-lookup"><span data-stu-id="62ff9-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="62ff9-134">`SetConnectionTasks`se volá vedle a poskytne sadu úloh, které se mají přidružit k tomuto připojení.</span><span class="sxs-lookup"><span data-stu-id="62ff9-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="62ff9-135">`EndConnection`je volána jako poslední k odebrání přidružení mezi seznamem úkolů a identifikátorem a popisným názvem. Volání různých připojení však mohou být vnořena.</span><span class="sxs-lookup"><span data-stu-id="62ff9-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ff9-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62ff9-136">Requirements</span></span>  
 <span data-ttu-id="62ff9-137">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ff9-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ff9-138">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="62ff9-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62ff9-139">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="62ff9-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62ff9-140">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ff9-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ff9-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="62ff9-141">See also</span></span>

- [<span data-ttu-id="62ff9-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62ff9-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="62ff9-143">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62ff9-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="62ff9-144">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="62ff9-144">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="62ff9-145">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="62ff9-145">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="62ff9-146">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62ff9-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
