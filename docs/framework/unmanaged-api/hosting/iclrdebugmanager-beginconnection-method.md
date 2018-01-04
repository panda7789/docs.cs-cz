---
title: "ICLRDebugManager::BeginConnection – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.BeginConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a637ba71dc966cf311526f468393ef4207e10460
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="4a987-102">ICLRDebugManager::BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="4a987-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="4a987-103">Vytvoří nové připojení mezi hostitelem a ladicí program, spolu s identifikátorem a popisný název seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="4a987-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a987-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a987-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a987-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a987-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="4a987-106">[v] Identifikátor pro přidružení seznamu běžných úloh language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4a987-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="4a987-107">[v] Popisný název, který přidružit seznam úloh CLR.</span><span class="sxs-lookup"><span data-stu-id="4a987-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a987-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4a987-108">Return Value</span></span>  
  
|<span data-ttu-id="4a987-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a987-109">HRESULT</span></span>|<span data-ttu-id="4a987-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4a987-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a987-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a987-111">S_OK</span></span>|<span data-ttu-id="4a987-112">`BeginConnection`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4a987-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="4a987-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a987-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a987-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4a987-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a987-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a987-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a987-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4a987-116">The call timed out.</span></span>|  
|<span data-ttu-id="4a987-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a987-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a987-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="4a987-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a987-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a987-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a987-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="4a987-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a987-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a987-121">E_FAIL</span></span>|<span data-ttu-id="4a987-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="4a987-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a987-123">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4a987-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a987-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a987-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a987-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4a987-125">E_INVALIDARG</span></span>|<span data-ttu-id="4a987-126">`dwConnectionId`byl nula, nebo `BeginConnection` již byla volána pomocí této `dwConnectionId` hodnotu, nebo `szConnectionName` měl hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4a987-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="4a987-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4a987-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4a987-128">Seznam úloh přidružených k tomuto připojení může být přiděleno není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="4a987-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a987-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a987-129">Remarks</span></span>  
 <span data-ttu-id="4a987-130">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, [setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), a [endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), pro přidružení s identifikátory a popisné názvy seznam úloh.</span><span class="sxs-lookup"><span data-stu-id="4a987-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a987-131">Tyto tři metody musí být voláno v určitém pořadí pro jednotlivé skupiny úloh.</span><span class="sxs-lookup"><span data-stu-id="4a987-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="4a987-132">`BeginConnection`je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="4a987-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="4a987-133">`SetConnectionTasks`je volána vedle zajistit sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="4a987-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="4a987-134">`EndConnection`je volána poslední k odstranění přidružení mezi seznamu úloh a identifikátor a popisný název. Však mohou být vnořené volání pro různá připojení.</span><span class="sxs-lookup"><span data-stu-id="4a987-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a987-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a987-135">Requirements</span></span>  
 <span data-ttu-id="4a987-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a987-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a987-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a987-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a987-138">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a987-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a987-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a987-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a987-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a987-140">See Also</span></span>  
 [<span data-ttu-id="4a987-141">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a987-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="4a987-142">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a987-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="4a987-143">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="4a987-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="4a987-144">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="4a987-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="4a987-145">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a987-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
