---
title: ICLRSyncManager::GetMonitorOwner – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b14421bbe71b68ca677cf712512a7f10aa30583
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208199"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="f8667-102">ICLRSyncManager::GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="f8667-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="f8667-103">Získá [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která vlastní monitorování identifikovaný zadaného souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="f8667-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8667-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8667-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8667-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8667-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="f8667-106">[in] Soubor cookie, přidružené k monitorování.</span><span class="sxs-lookup"><span data-stu-id="f8667-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="f8667-107">[out] Ukazatel `IHostTask` , který aktuálně vlastní monitorování nebo hodnota null, pokud žádný úkol má vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="f8667-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8667-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8667-108">Return Value</span></span>  
  
|<span data-ttu-id="f8667-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8667-109">HRESULT</span></span>|<span data-ttu-id="f8667-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f8667-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8667-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8667-111">S_OK</span></span>|<span data-ttu-id="f8667-112">`GetMonitorOwner` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f8667-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="f8667-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8667-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8667-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f8667-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8667-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8667-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8667-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f8667-116">The call timed out.</span></span>|  
|<span data-ttu-id="f8667-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8667-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8667-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f8667-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8667-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8667-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8667-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f8667-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8667-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8667-121">E_FAIL</span></span>|<span data-ttu-id="f8667-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f8667-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8667-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f8667-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8667-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f8667-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8667-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8667-125">Remarks</span></span>  
 <span data-ttu-id="f8667-126">Hostitel obvykle volá `GetMonitorOwner` jako součást mechanismus rozpoznávání zablokování.</span><span class="sxs-lookup"><span data-stu-id="f8667-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="f8667-127">Soubor cookie souvisí s monitorováním při jeho vytváření s použitím volání [ihostsyncmanager::createmonitorevent –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8667-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8667-128">Volání k uvolnění základní monitorování události může blokovat – ale nebude zablokování – Pokud volání této metody je aktuálně používána v souboru cookie, přidružené k příslušné monitorování.</span><span class="sxs-lookup"><span data-stu-id="f8667-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="f8667-129">Další úlohy může také blokovat pokusu o získání tohoto monitorování.</span><span class="sxs-lookup"><span data-stu-id="f8667-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="f8667-130">`GetMonitorOwner` vždy vrátí hodnotu okamžitě a může být volána vždy po volání `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="f8667-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="f8667-131">Hostitel není potřeba počkat, dokud úloha čeká na událost.</span><span class="sxs-lookup"><span data-stu-id="f8667-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8667-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8667-132">Requirements</span></span>  
 <span data-ttu-id="f8667-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8667-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8667-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8667-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8667-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8667-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8667-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8667-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8667-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8667-137">See also</span></span>

- [<span data-ttu-id="f8667-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8667-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f8667-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8667-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
