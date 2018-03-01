---
title: "ICLRSyncManager::GetMonitorOwner – metoda"
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
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b998a26056aec739587b77c1b1b39f0e9392a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="53553-102">ICLRSyncManager::GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="53553-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="53553-103">Získá [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, který vlastní monitorování identifikovaný zadaný soubor cookie.</span><span class="sxs-lookup"><span data-stu-id="53553-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53553-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53553-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53553-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53553-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="53553-106">[v] Soubor cookie přidružených k monitorování.</span><span class="sxs-lookup"><span data-stu-id="53553-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="53553-107">[out] Ukazatel `IHostTask` , který aktuálně je vlastníkem monitorování nebo hodnota null, pokud žádné úlohy má vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="53553-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53553-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="53553-108">Return Value</span></span>  
  
|<span data-ttu-id="53553-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53553-109">HRESULT</span></span>|<span data-ttu-id="53553-110">Popis</span><span class="sxs-lookup"><span data-stu-id="53553-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53553-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="53553-111">S_OK</span></span>|<span data-ttu-id="53553-112">`GetMonitorOwner`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="53553-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="53553-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53553-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53553-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="53553-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53553-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53553-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53553-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="53553-116">The call timed out.</span></span>|  
|<span data-ttu-id="53553-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53553-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53553-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="53553-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53553-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53553-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53553-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="53553-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53553-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53553-121">E_FAIL</span></span>|<span data-ttu-id="53553-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="53553-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53553-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="53553-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53553-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53553-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53553-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53553-125">Remarks</span></span>  
 <span data-ttu-id="53553-126">Hostitel obvykle volá `GetMonitorOwner` jako součást zjišťování zablokování mechanismus.</span><span class="sxs-lookup"><span data-stu-id="53553-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="53553-127">Soubor cookie je přidružen monitorování, když je vytvořeno pomocí volání [ihostsyncmanager::createmonitorevent –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="53553-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53553-128">Volání k uvolnění událostí základní monitorování mohou blokovat – ale nebude zablokování – Pokud volání této metody je aktuálně umístěna v souboru cookie přidruženého tohoto monitoru.</span><span class="sxs-lookup"><span data-stu-id="53553-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="53553-129">Další úlohy mohou také blokovat, jestliže se pokusí získat toto monitorování.</span><span class="sxs-lookup"><span data-stu-id="53553-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="53553-130">`GetMonitorOwner`vždy vrátí okamžitě a lze volat kdykoli po dokončení volání `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="53553-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="53553-131">Hostitel není nutné Počkejte, dokud úloha čeká na události.</span><span class="sxs-lookup"><span data-stu-id="53553-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53553-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53553-132">Requirements</span></span>  
 <span data-ttu-id="53553-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53553-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53553-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53553-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53553-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53553-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53553-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53553-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53553-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="53553-137">See Also</span></span>  
 [<span data-ttu-id="53553-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53553-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="53553-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53553-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
