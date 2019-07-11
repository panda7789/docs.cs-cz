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
ms.openlocfilehash: e1c986de068cd79ae3662c82ed24906d42bf2780
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759033"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="8cd65-102">ICLRSyncManager::GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="8cd65-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="8cd65-103">Získá [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která vlastní monitorování identifikovaný zadaného souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="8cd65-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cd65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cd65-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cd65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cd65-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="8cd65-106">[in] Soubor cookie, přidružené k monitorování.</span><span class="sxs-lookup"><span data-stu-id="8cd65-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="8cd65-107">[out] Ukazatel `IHostTask` , který aktuálně vlastní monitorování nebo hodnota null, pokud žádný úkol má vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="8cd65-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cd65-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8cd65-108">Return Value</span></span>  
  
|<span data-ttu-id="8cd65-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cd65-109">HRESULT</span></span>|<span data-ttu-id="8cd65-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8cd65-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cd65-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cd65-111">S_OK</span></span>|<span data-ttu-id="8cd65-112">`GetMonitorOwner` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8cd65-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="8cd65-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8cd65-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8cd65-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8cd65-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8cd65-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8cd65-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8cd65-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8cd65-116">The call timed out.</span></span>|  
|<span data-ttu-id="8cd65-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8cd65-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8cd65-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8cd65-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8cd65-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8cd65-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8cd65-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8cd65-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8cd65-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8cd65-121">E_FAIL</span></span>|<span data-ttu-id="8cd65-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8cd65-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8cd65-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8cd65-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8cd65-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8cd65-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cd65-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8cd65-125">Remarks</span></span>  
 <span data-ttu-id="8cd65-126">Hostitel obvykle volá `GetMonitorOwner` jako součást mechanismus rozpoznávání zablokování.</span><span class="sxs-lookup"><span data-stu-id="8cd65-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="8cd65-127">Soubor cookie souvisí s monitorováním při jeho vytváření s použitím volání [ihostsyncmanager::createmonitorevent –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="8cd65-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cd65-128">Volání k uvolnění základní monitorování události může blokovat – ale nebude zablokování – Pokud volání této metody je aktuálně používána v souboru cookie, přidružené k příslušné monitorování.</span><span class="sxs-lookup"><span data-stu-id="8cd65-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="8cd65-129">Další úlohy může také blokovat pokusu o získání tohoto monitorování.</span><span class="sxs-lookup"><span data-stu-id="8cd65-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="8cd65-130">`GetMonitorOwner` vždy vrátí hodnotu okamžitě a může být volána vždy po volání `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="8cd65-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="8cd65-131">Hostitel není potřeba počkat, dokud úloha čeká na událost.</span><span class="sxs-lookup"><span data-stu-id="8cd65-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cd65-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8cd65-132">Requirements</span></span>  
 <span data-ttu-id="8cd65-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cd65-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cd65-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8cd65-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cd65-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8cd65-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cd65-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cd65-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd65-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cd65-137">See also</span></span>

- [<span data-ttu-id="8cd65-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8cd65-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8cd65-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8cd65-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
