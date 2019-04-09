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
ms.openlocfilehash: 12b0e32ab46b3e8ba5120da4b16a10db85f105a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127683"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="0b87c-102">IHostSyncManager::CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="0b87c-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="0b87c-103">Vytvoří objekt monitorovanou událost automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="0b87c-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b87c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b87c-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b87c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b87c-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="0b87c-106">[in] Soubor cookie přidružit k objektu události.</span><span class="sxs-lookup"><span data-stu-id="0b87c-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="0b87c-107">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt události.</span><span class="sxs-lookup"><span data-stu-id="0b87c-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b87c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0b87c-108">Return Value</span></span>  
  
|<span data-ttu-id="0b87c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b87c-109">HRESULT</span></span>|<span data-ttu-id="0b87c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0b87c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b87c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b87c-111">S_OK</span></span>|`CreateMonitorEvent` <span data-ttu-id="0b87c-112">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0b87c-112">returned successfully.</span></span>|  
|<span data-ttu-id="0b87c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b87c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b87c-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0b87c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b87c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b87c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b87c-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0b87c-116">The call timed out.</span></span>|  
|<span data-ttu-id="0b87c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b87c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b87c-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="0b87c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b87c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b87c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b87c-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="0b87c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b87c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b87c-121">E_FAIL</span></span>|<span data-ttu-id="0b87c-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="0b87c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b87c-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0b87c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b87c-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b87c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0b87c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0b87c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0b87c-126">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="0b87c-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b87c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b87c-127">Remarks</span></span>  
 `CreateMonitorEvent` <span data-ttu-id="0b87c-128">Vrátí `IHostAutoEvent` , který používá modul CLR v rámci příslušné implementace spravovaného <xref:System.Threading.Monitor?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="0b87c-128">returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="0b87c-129">Tato metoda zrcadlí Win32 `CreateEvent` funkci s hodnotou `false` zadaný pro `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="0b87c-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="0b87c-130">Hostitele můžete použít soubor cookie k určení, které úloha čeká na monitorování voláním [iclrsyncmanager::getmonitorowner –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0b87c-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b87c-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b87c-131">Requirements</span></span>  
 <span data-ttu-id="0b87c-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b87c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b87c-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b87c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b87c-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b87c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0b87c-135">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0b87c-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0b87c-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b87c-136">See also</span></span>

- [<span data-ttu-id="0b87c-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b87c-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0b87c-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b87c-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="0b87c-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b87c-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
