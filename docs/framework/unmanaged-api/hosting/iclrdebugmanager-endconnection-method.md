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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf21e1844ea99b231054f8350ddacb8bb707a94e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969868"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="8000e-102">ICLRDebugManager::EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="8000e-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="8000e-103">Odebere přidružení mezi seznam úkolů a identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="8000e-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8000e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8000e-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8000e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8000e-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="8000e-106">[in] Identifikátor konkrétního hostitele pro připojení a přidružený seznam běžné language runtime (CLR) úlohy.</span><span class="sxs-lookup"><span data-stu-id="8000e-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8000e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8000e-107">Return Value</span></span>  
  
|<span data-ttu-id="8000e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8000e-108">HRESULT</span></span>|<span data-ttu-id="8000e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8000e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8000e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8000e-110">S_OK</span></span>|<span data-ttu-id="8000e-111">`EndConnection` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8000e-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="8000e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8000e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8000e-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8000e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8000e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8000e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8000e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8000e-115">The call timed out.</span></span>|  
|<span data-ttu-id="8000e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8000e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8000e-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8000e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8000e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8000e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8000e-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8000e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8000e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8000e-120">E_FAIL</span></span>|<span data-ttu-id="8000e-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8000e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8000e-122">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8000e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8000e-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8000e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8000e-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8000e-124">E_INVALIDARG</span></span>|<span data-ttu-id="8000e-125">[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nikdy byla vyvolána pomocí prvku `dwConnectionId`, nebo `dwConnectionId` je nulový.</span><span class="sxs-lookup"><span data-stu-id="8000e-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8000e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8000e-126">Remarks</span></span>  
 <span data-ttu-id="8000e-127">[Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, [setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), a `EndConnection`, pro seznamy úloh přidružení s identifikátory a popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="8000e-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8000e-128">Tyto tři metody musí být volána v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="8000e-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="8000e-129">`BeginConnection` je volána nejprve vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="8000e-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="8000e-130">`SetConnectionTasks` je volána dále k poskytování sadu úloh, který se má přidružit toto připojení.</span><span class="sxs-lookup"><span data-stu-id="8000e-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="8000e-131">`EndConnection` Chcete-li odebrat přidružení seznamu úkolů a identifikátor a popisný název se nazývá poslední. Volání pro různá připojení však mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="8000e-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8000e-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8000e-132">Requirements</span></span>  
 <span data-ttu-id="8000e-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8000e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8000e-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8000e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8000e-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8000e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8000e-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8000e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8000e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8000e-137">See also</span></span>

- [<span data-ttu-id="8000e-138">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8000e-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8000e-139">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8000e-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="8000e-140">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="8000e-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="8000e-141">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="8000e-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="8000e-142">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8000e-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
