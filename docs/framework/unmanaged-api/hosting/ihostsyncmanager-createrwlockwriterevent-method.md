---
title: IHostSyncManager::CreateRWLockWriterEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1deff93744d1dec0ff7d6cab5bb6580f3a8fbad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490044"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="82e6a-102">IHostSyncManager::CreateRWLockWriterEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="82e6a-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="82e6a-103">Vytvoří objekt automatického resetu pro provádění zapisovací zámek.</span><span class="sxs-lookup"><span data-stu-id="82e6a-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e6a-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82e6a-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="82e6a-106">[in] Soubor cookie přidružit k události automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="82e6a-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="82e6a-107">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt události.</span><span class="sxs-lookup"><span data-stu-id="82e6a-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82e6a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="82e6a-108">Return Value</span></span>  
  
|<span data-ttu-id="82e6a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82e6a-109">HRESULT</span></span>|<span data-ttu-id="82e6a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="82e6a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82e6a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="82e6a-111">S_OK</span></span>|<span data-ttu-id="82e6a-112">`CreateRWLockWriterEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="82e6a-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="82e6a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82e6a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82e6a-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="82e6a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82e6a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82e6a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82e6a-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="82e6a-116">The call timed out.</span></span>|  
|<span data-ttu-id="82e6a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82e6a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82e6a-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="82e6a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82e6a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82e6a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82e6a-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="82e6a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82e6a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82e6a-121">E_FAIL</span></span>|<span data-ttu-id="82e6a-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="82e6a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82e6a-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="82e6a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82e6a-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="82e6a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="82e6a-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="82e6a-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="82e6a-126">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="82e6a-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82e6a-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82e6a-127">Remarks</span></span>  
 <span data-ttu-id="82e6a-128">Volání CLR `CreateRWLockWriterEvent` metodu k získání odkazu na `IHostAutoEvent` instance pro použití v jeho provádění zapisovací zámek.</span><span class="sxs-lookup"><span data-stu-id="82e6a-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="82e6a-129">Hostitele můžete použít zadaný soubor cookie k určení, úlohy, které čekají na zámek voláním metod iterace [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="82e6a-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e6a-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82e6a-130">Requirements</span></span>  
 <span data-ttu-id="82e6a-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e6a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e6a-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82e6a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82e6a-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82e6a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82e6a-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e6a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e6a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82e6a-135">See also</span></span>
- [<span data-ttu-id="82e6a-136">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e6a-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="82e6a-137">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e6a-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="82e6a-138">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e6a-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="82e6a-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e6a-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
