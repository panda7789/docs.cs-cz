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
ms.openlocfilehash: b365aaa13b3070662a74ebcfc914f5ed3d291d76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133988"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="a9b1f-102">ICLRDebugManager::BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="a9b1f-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="a9b1f-103">Vytvoří nové připojení mezi hostitelem a ladicí program přidružit identifikátor a popisný název seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9b1f-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9b1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9b1f-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="a9b1f-106">[in] Identifikátor pro přidružení k seznamu běžné language runtime (CLR) úlohy.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="a9b1f-107">[in] Popisný název pro přidružení k seznamu úkolů CLR.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9b1f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a9b1f-108">Return Value</span></span>  
  
|<span data-ttu-id="a9b1f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9b1f-109">HRESULT</span></span>|<span data-ttu-id="a9b1f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a9b1f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9b1f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9b1f-111">S_OK</span></span>|`BeginConnection` <span data-ttu-id="a9b1f-112">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-112">returned successfully.</span></span>|  
|<span data-ttu-id="a9b1f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9b1f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9b1f-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9b1f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9b1f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9b1f-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-116">The call timed out.</span></span>|  
|<span data-ttu-id="a9b1f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9b1f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9b1f-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9b1f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9b1f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9b1f-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9b1f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9b1f-121">E_FAIL</span></span>|<span data-ttu-id="a9b1f-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9b1f-123">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9b1f-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9b1f-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a9b1f-125">E_INVALIDARG</span></span>|`dwConnectionId` <span data-ttu-id="a9b1f-126">je nulový, nebo `BeginConnection` již byla volána pomocí tohoto `dwConnectionId` hodnotu, nebo `szConnectionName` měl hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-126">was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="a9b1f-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a9b1f-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a9b1f-128">Seznam úkolů přidružených k tomuto připojení může být přiděleno není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9b1f-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9b1f-129">Remarks</span></span>  
 <span data-ttu-id="a9b1f-130">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, [setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), a [endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), pro seznamy úloh přidružení s identifikátory a popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9b1f-131">Tyto tři metody musí být volána v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-131">These three methods must be called in a specific order for each set of tasks.</span></span> `BeginConnection` <span data-ttu-id="a9b1f-132">je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-132">is called first to establish a new connection.</span></span> `SetConnectionTasks` <span data-ttu-id="a9b1f-133">je volána dále k poskytování sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-133">is called next to provide the set of tasks to be associated with that connection.</span></span> `EndConnection` <span data-ttu-id="a9b1f-134">Chcete-li odebrat přidružení seznamu úkolů a identifikátor a popisný název se nazývá poslední. Volání pro různá připojení však mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="a9b1f-134">is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9b1f-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9b1f-135">Requirements</span></span>  
 <span data-ttu-id="a9b1f-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9b1f-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b1f-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9b1f-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9b1f-138">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9b1f-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a9b1f-139">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a9b1f-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a9b1f-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9b1f-140">See also</span></span>

- [<span data-ttu-id="a9b1f-141">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9b1f-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a9b1f-142">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9b1f-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="a9b1f-143">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="a9b1f-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="a9b1f-144">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="a9b1f-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="a9b1f-145">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9b1f-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
