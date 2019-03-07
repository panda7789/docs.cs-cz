---
title: IHostSyncManager::CreateRWLockReaderEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5aef90fa14dac58a0b38316cd5f64b4ac8c9aa1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495647"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="fd057-102">IHostSyncManager::CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="fd057-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="fd057-103">Vytvoří objekt ruční obnovení události pro implementaci zámku čtecího modulu.</span><span class="sxs-lookup"><span data-stu-id="fd057-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd057-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd057-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd057-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd057-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="fd057-106">[in] `true`, pokud `ppEvent` by měl být signalizovaného; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="fd057-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="fd057-107">[in] Soubor cookie přidružit zámku čtecího modulu.</span><span class="sxs-lookup"><span data-stu-id="fd057-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="fd057-108">[out] Ukazatel na adresu [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt události.</span><span class="sxs-lookup"><span data-stu-id="fd057-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd057-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fd057-109">Return Value</span></span>  
  
|<span data-ttu-id="fd057-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd057-110">HRESULT</span></span>|<span data-ttu-id="fd057-111">Popis</span><span class="sxs-lookup"><span data-stu-id="fd057-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd057-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd057-112">S_OK</span></span>|<span data-ttu-id="fd057-113">`CreateRWLockReaderEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="fd057-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="fd057-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd057-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd057-115">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fd057-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd057-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd057-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd057-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fd057-117">The call timed out.</span></span>|  
|<span data-ttu-id="fd057-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd057-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd057-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="fd057-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd057-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd057-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd057-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="fd057-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd057-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd057-122">E_FAIL</span></span>|<span data-ttu-id="fd057-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="fd057-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd057-124">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fd057-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd057-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fd057-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fd057-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fd057-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fd057-127">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="fd057-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd057-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd057-128">Remarks</span></span>  
 <span data-ttu-id="fd057-129">Volání CLR `CreateRWLockReaderEvent` k získání odkazu na `IHostManualEvent` instance pro použití v jeho provádění zámku čtecího modulu.</span><span class="sxs-lookup"><span data-stu-id="fd057-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="fd057-130">Hostitele můžete použít soubor cookie k určení, úlohy, které čekají na zámek pro čtení pomocí dotazu [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fd057-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd057-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd057-131">Requirements</span></span>  
 <span data-ttu-id="fd057-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd057-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd057-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd057-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd057-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd057-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd057-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd057-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd057-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd057-136">See also</span></span>
- [<span data-ttu-id="fd057-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd057-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="fd057-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd057-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="fd057-139">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd057-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="fd057-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd057-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
