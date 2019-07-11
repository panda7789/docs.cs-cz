---
title: IHostSyncManager::CreateMonitorEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e5a66a87424c2ff8367aaf9ad4da27595880912
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753424"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="78ae8-102">IHostSyncManager::CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="78ae8-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="78ae8-103">Vytvoří objekt monitorovanou událost automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="78ae8-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ae8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78ae8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78ae8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78ae8-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="78ae8-106">[in] Soubor cookie přidružit k objektu události.</span><span class="sxs-lookup"><span data-stu-id="78ae8-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="78ae8-107">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt události.</span><span class="sxs-lookup"><span data-stu-id="78ae8-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78ae8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78ae8-108">Return Value</span></span>  
  
|<span data-ttu-id="78ae8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78ae8-109">HRESULT</span></span>|<span data-ttu-id="78ae8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="78ae8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78ae8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="78ae8-111">S_OK</span></span>|<span data-ttu-id="78ae8-112">`CreateMonitorEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="78ae8-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="78ae8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78ae8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78ae8-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="78ae8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78ae8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78ae8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78ae8-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="78ae8-116">The call timed out.</span></span>|  
|<span data-ttu-id="78ae8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78ae8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78ae8-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="78ae8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78ae8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78ae8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78ae8-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="78ae8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78ae8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78ae8-121">E_FAIL</span></span>|<span data-ttu-id="78ae8-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="78ae8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78ae8-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="78ae8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78ae8-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="78ae8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78ae8-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="78ae8-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="78ae8-126">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="78ae8-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78ae8-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78ae8-127">Remarks</span></span>  
 <span data-ttu-id="78ae8-128">`CreateMonitorEvent` Vrátí `IHostAutoEvent` , který používá modul CLR v rámci příslušné implementace spravovaného <xref:System.Threading.Monitor?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="78ae8-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="78ae8-129">Tato metoda zrcadlí Win32 `CreateEvent` funkci s hodnotou `false` zadaný pro `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="78ae8-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="78ae8-130">Hostitele můžete použít soubor cookie k určení, které úloha čeká na monitorování voláním [iclrsyncmanager::getmonitorowner –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="78ae8-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78ae8-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78ae8-131">Requirements</span></span>  
 <span data-ttu-id="78ae8-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78ae8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78ae8-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78ae8-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78ae8-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78ae8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78ae8-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78ae8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ae8-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78ae8-136">See also</span></span>

- [<span data-ttu-id="78ae8-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78ae8-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="78ae8-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78ae8-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="78ae8-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78ae8-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
