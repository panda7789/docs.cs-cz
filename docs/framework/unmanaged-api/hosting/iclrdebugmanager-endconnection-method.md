---
title: ICLRDebugManager::EndConnection – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: 425f40da7a53aa4af1bd14964a8136add2f59f0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135220"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="fb94a-102">ICLRDebugManager::EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="fb94a-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="fb94a-103">Odebere přidružení mezi seznamem úkolů a identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="fb94a-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb94a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb94a-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb94a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb94a-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="fb94a-106">pro Identifikátor konkrétního hostitele pro připojení a přidružený seznam úloh modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="fb94a-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb94a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb94a-107">Return Value</span></span>  
  
|<span data-ttu-id="fb94a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb94a-108">HRESULT</span></span>|<span data-ttu-id="fb94a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fb94a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb94a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb94a-110">S_OK</span></span>|<span data-ttu-id="fb94a-111">`EndConnection` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="fb94a-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="fb94a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb94a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb94a-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fb94a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb94a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb94a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb94a-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fb94a-115">The call timed out.</span></span>|  
|<span data-ttu-id="fb94a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb94a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb94a-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="fb94a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb94a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb94a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb94a-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="fb94a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb94a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb94a-120">E_FAIL</span></span>|<span data-ttu-id="fb94a-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="fb94a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb94a-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="fb94a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb94a-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb94a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fb94a-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fb94a-124">E_INVALIDARG</span></span>|<span data-ttu-id="fb94a-125">[BeginConnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) se nikdy nevolal pomocí `dwConnectionId`, nebo `dwConnectionId` byla nulová.</span><span class="sxs-lookup"><span data-stu-id="fb94a-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb94a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb94a-126">Remarks</span></span>  
 <span data-ttu-id="fb94a-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody, `BeginConnection`, [SetConnectionTasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)a `EndConnection`, pro přiřazování seznamů úkolů s identifikátory a popisnými názvy.</span><span class="sxs-lookup"><span data-stu-id="fb94a-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fb94a-128">Tyto tři metody musí být volány v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="fb94a-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="fb94a-129">`BeginConnection` se označuje jako první, aby se navázalo nové připojení.</span><span class="sxs-lookup"><span data-stu-id="fb94a-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="fb94a-130">`SetConnectionTasks` se volá vedle, která poskytne sadu úloh, které se mají přidružit k tomuto připojení.</span><span class="sxs-lookup"><span data-stu-id="fb94a-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="fb94a-131">`EndConnection` je volána jako poslední pro odebrání přidružení mezi seznamem úkolů a identifikátorem a popisným názvem. Volání různých připojení však mohou být vnořena.</span><span class="sxs-lookup"><span data-stu-id="fb94a-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb94a-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb94a-132">Requirements</span></span>  
 <span data-ttu-id="fb94a-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb94a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb94a-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb94a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb94a-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fb94a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb94a-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb94a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb94a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb94a-137">See also</span></span>

- [<span data-ttu-id="fb94a-138">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb94a-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fb94a-139">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb94a-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="fb94a-140">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="fb94a-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="fb94a-141">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="fb94a-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="fb94a-142">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb94a-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
