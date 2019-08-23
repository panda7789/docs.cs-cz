---
title: ICLRDebugManager::BeginConnection – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37e663cbad902b5740a14b9fe60f24537d999aac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969434"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="4822d-102">ICLRDebugManager::BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="4822d-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="4822d-103">Vytvoří nové propojení mezi hostitelem a ladicím programem k přidružení seznamu úkolů s identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="4822d-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4822d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4822d-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4822d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4822d-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="4822d-106">pro Identifikátor, který se má přidružit k seznamu úloh modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4822d-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="4822d-107">pro Popisný název, který chcete přidružit k seznamu úkolů CLR.</span><span class="sxs-lookup"><span data-stu-id="4822d-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4822d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4822d-108">Return Value</span></span>  
  
|<span data-ttu-id="4822d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4822d-109">HRESULT</span></span>|<span data-ttu-id="4822d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4822d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4822d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4822d-111">S_OK</span></span>|<span data-ttu-id="4822d-112">`BeginConnection`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4822d-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="4822d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4822d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4822d-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4822d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4822d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4822d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4822d-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4822d-116">The call timed out.</span></span>|  
|<span data-ttu-id="4822d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4822d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4822d-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="4822d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4822d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4822d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4822d-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="4822d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4822d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4822d-121">E_FAIL</span></span>|<span data-ttu-id="4822d-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="4822d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4822d-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="4822d-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4822d-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4822d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4822d-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4822d-125">E_INVALIDARG</span></span>|<span data-ttu-id="4822d-126">`dwConnectionId`byla nulová nebo `BeginConnection` již byla volána pomocí této `dwConnectionId` hodnoty, nebo `szConnectionName` měla hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4822d-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="4822d-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4822d-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4822d-128">Nebylo možné přidělit dostatek paměti pro uložení seznamu úkolů přidružených k tomuto připojení.</span><span class="sxs-lookup"><span data-stu-id="4822d-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4822d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4822d-129">Remarks</span></span>  
 <span data-ttu-id="4822d-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody, `BeginConnection`, [SetConnectionTasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)a [EndConnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)pro přiřazování seznamů úkolů s identifikátory a popisnými názvy.</span><span class="sxs-lookup"><span data-stu-id="4822d-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4822d-131">Tyto tři metody musí být volány v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="4822d-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="4822d-132">`BeginConnection`se označuje jako první, aby se navázalo nové připojení.</span><span class="sxs-lookup"><span data-stu-id="4822d-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="4822d-133">`SetConnectionTasks`se volá vedle a poskytne sadu úloh, které se mají přidružit k tomuto připojení.</span><span class="sxs-lookup"><span data-stu-id="4822d-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="4822d-134">`EndConnection`je volána jako poslední k odebrání přidružení mezi seznamem úkolů a identifikátorem a popisným názvem. Volání různých připojení však mohou být vnořena.</span><span class="sxs-lookup"><span data-stu-id="4822d-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4822d-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4822d-135">Requirements</span></span>  
 <span data-ttu-id="4822d-136">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4822d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4822d-137">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4822d-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4822d-138">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4822d-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4822d-139">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4822d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4822d-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4822d-140">See also</span></span>

- [<span data-ttu-id="4822d-141">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4822d-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4822d-142">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4822d-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="4822d-143">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="4822d-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="4822d-144">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="4822d-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="4822d-145">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4822d-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
