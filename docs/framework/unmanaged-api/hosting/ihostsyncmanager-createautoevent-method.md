---
title: IHostSyncManager::CreateAutoEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60d0d8480dcbe697b9ae76abd210120fc6b6955
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485509"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="b12ff-102">IHostSyncManager::CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="b12ff-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="b12ff-103">Vytvoří objekt události automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="b12ff-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b12ff-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b12ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b12ff-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="b12ff-106">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci implementovaného tímto hostitelem, nebo hodnotu null, pokud nelze vytvořit objekt události.</span><span class="sxs-lookup"><span data-stu-id="b12ff-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b12ff-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b12ff-107">Return Value</span></span>  
  
|<span data-ttu-id="b12ff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b12ff-108">HRESULT</span></span>|<span data-ttu-id="b12ff-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b12ff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b12ff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b12ff-110">S_OK</span></span>|<span data-ttu-id="b12ff-111">`CreateAutoEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b12ff-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="b12ff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b12ff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b12ff-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b12ff-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b12ff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b12ff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b12ff-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b12ff-115">The call timed out.</span></span>|  
|<span data-ttu-id="b12ff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b12ff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b12ff-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="b12ff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b12ff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b12ff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b12ff-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="b12ff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b12ff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b12ff-120">E_FAIL</span></span>|<span data-ttu-id="b12ff-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="b12ff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b12ff-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="b12ff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b12ff-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b12ff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b12ff-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b12ff-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b12ff-125">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="b12ff-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b12ff-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b12ff-126">Remarks</span></span>  
 <span data-ttu-id="b12ff-127">`CreateAutoEvent` Vytvoří objekt automatické událostí jehož stav se automaticky změní na nesignálového po vydala vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="b12ff-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="b12ff-128">Tato metoda zrcadlí Win32 `CreateEvent` funkci s hodnotou `false` zadaný pro `bManualReset` parametr</span><span class="sxs-lookup"><span data-stu-id="b12ff-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b12ff-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b12ff-129">Requirements</span></span>  
 <span data-ttu-id="b12ff-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12ff-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12ff-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b12ff-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b12ff-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b12ff-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b12ff-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12ff-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12ff-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b12ff-134">See also</span></span>
- [<span data-ttu-id="b12ff-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b12ff-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b12ff-136">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b12ff-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="b12ff-137">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b12ff-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="b12ff-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b12ff-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
