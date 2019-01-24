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
ms.openlocfilehash: 9166d7934c56a897ef766bc3a4962041e6d19f5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658634"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="522ca-102">IHostSyncManager::CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="522ca-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="522ca-103">Vytvoří objekt události automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="522ca-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="522ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="522ca-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="522ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="522ca-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="522ca-106">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci implementovaného tímto hostitelem, nebo hodnotu null, pokud nelze vytvořit objekt události.</span><span class="sxs-lookup"><span data-stu-id="522ca-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="522ca-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="522ca-107">Return Value</span></span>  
  
|<span data-ttu-id="522ca-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="522ca-108">HRESULT</span></span>|<span data-ttu-id="522ca-109">Popis</span><span class="sxs-lookup"><span data-stu-id="522ca-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="522ca-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="522ca-110">S_OK</span></span>|<span data-ttu-id="522ca-111">`CreateAutoEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="522ca-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="522ca-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="522ca-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="522ca-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="522ca-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="522ca-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="522ca-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="522ca-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="522ca-115">The call timed out.</span></span>|  
|<span data-ttu-id="522ca-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="522ca-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="522ca-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="522ca-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="522ca-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="522ca-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="522ca-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="522ca-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="522ca-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="522ca-120">E_FAIL</span></span>|<span data-ttu-id="522ca-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="522ca-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="522ca-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="522ca-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="522ca-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="522ca-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="522ca-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="522ca-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="522ca-125">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="522ca-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="522ca-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="522ca-126">Remarks</span></span>  
 <span data-ttu-id="522ca-127">`CreateAutoEvent` Vytvoří objekt automatické událostí jehož stav se automaticky změní na nesignálového po vydala vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="522ca-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="522ca-128">Tato metoda zrcadlí Win32 `CreateEvent` funkci s hodnotou `false` zadaný pro `bManualReset` parametr</span><span class="sxs-lookup"><span data-stu-id="522ca-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="522ca-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="522ca-129">Requirements</span></span>  
 <span data-ttu-id="522ca-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="522ca-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="522ca-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="522ca-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="522ca-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="522ca-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="522ca-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="522ca-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522ca-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="522ca-134">See also</span></span>
- [<span data-ttu-id="522ca-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="522ca-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="522ca-136">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="522ca-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="522ca-137">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="522ca-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="522ca-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="522ca-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
