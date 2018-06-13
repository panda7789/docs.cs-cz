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
ms.openlocfilehash: 1d7cff23fc0b58d316ce19950a982249e84b79ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441949"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="92367-102">IHostSyncManager::CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="92367-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="92367-103">Vytvoří objekt monitorovanou událost automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="92367-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92367-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92367-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92367-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92367-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="92367-106">[v] Soubor cookie přidružit objekt události.</span><span class="sxs-lookup"><span data-stu-id="92367-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="92367-107">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="92367-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92367-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92367-108">Return Value</span></span>  
  
|<span data-ttu-id="92367-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92367-109">HRESULT</span></span>|<span data-ttu-id="92367-110">Popis</span><span class="sxs-lookup"><span data-stu-id="92367-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92367-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="92367-111">S_OK</span></span>|<span data-ttu-id="92367-112">`CreateMonitorEvent` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="92367-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="92367-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92367-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92367-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="92367-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92367-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92367-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92367-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="92367-116">The call timed out.</span></span>|  
|<span data-ttu-id="92367-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92367-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92367-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="92367-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92367-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92367-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92367-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="92367-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92367-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92367-121">E_FAIL</span></span>|<span data-ttu-id="92367-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="92367-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92367-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="92367-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92367-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92367-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92367-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="92367-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="92367-126">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="92367-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92367-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92367-127">Remarks</span></span>  
 <span data-ttu-id="92367-128">`CreateMonitorEvent` Vrátí `IHostAutoEvent` používající modulu CLR při implementaci spravovaný <xref:System.Threading.Monitor?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="92367-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="92367-129">Tato metoda odpovídá Win32 `CreateEvent` funkce s hodnotou `false` zadaná pro `bManualReset` parametr.</span><span class="sxs-lookup"><span data-stu-id="92367-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="92367-130">Hostitele můžete použít soubor cookie k určení, které úloha čeká na monitoru voláním [iclrsyncmanager::getmonitorowner –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="92367-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92367-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92367-131">Requirements</span></span>  
 <span data-ttu-id="92367-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92367-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92367-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92367-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92367-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92367-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92367-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92367-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92367-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="92367-136">See Also</span></span>  
 [<span data-ttu-id="92367-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92367-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="92367-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92367-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="92367-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92367-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="92367-140">Monitorování</span><span class="sxs-lookup"><span data-stu-id="92367-140">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
