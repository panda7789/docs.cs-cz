---
title: IHostSyncManager::CreateManualEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ada9a3131ea3063239ab7897d0096f0accbd0f94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137732"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="44ba2-102">IHostSyncManager::CreateManualEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="44ba2-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="44ba2-103">Vytvoří objekt ruční obnovení události.</span><span class="sxs-lookup"><span data-stu-id="44ba2-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44ba2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44ba2-104">Syntax</span></span>  
  
```  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44ba2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44ba2-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="44ba2-106">[in] `true`, pokud je objekt signalizovaného; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="44ba2-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="44ba2-107">[out] Ukazatel na adresu [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instanci, nebo hodnota null, pokud událost se nepovedlo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="44ba2-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44ba2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44ba2-108">Return Value</span></span>  
  
|<span data-ttu-id="44ba2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44ba2-109">HRESULT</span></span>|<span data-ttu-id="44ba2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="44ba2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44ba2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="44ba2-111">S_OK</span></span>|<span data-ttu-id="44ba2-112">`CreateManualEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="44ba2-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="44ba2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44ba2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44ba2-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="44ba2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44ba2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44ba2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44ba2-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="44ba2-116">The call timed out.</span></span>|  
|<span data-ttu-id="44ba2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44ba2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44ba2-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="44ba2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44ba2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44ba2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44ba2-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="44ba2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44ba2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44ba2-121">E_FAIL</span></span>|<span data-ttu-id="44ba2-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="44ba2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44ba2-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="44ba2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44ba2-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44ba2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="44ba2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="44ba2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="44ba2-126">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="44ba2-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44ba2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44ba2-127">Remarks</span></span>  
 <span data-ttu-id="44ba2-128">`CreateManualEvent` vytvoří `IHostManualEvent`, objektu ruční obnovení události, která vyžaduje volání [ihostmanualevent::reset –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) metody nastavte do nesignálového stavu.</span><span class="sxs-lookup"><span data-stu-id="44ba2-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="44ba2-129">`CreateManualEvent` odráží Win32 `CreateEvent` funkci s hodnotou `true` zadaný pro `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="44ba2-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44ba2-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44ba2-130">Requirements</span></span>  
 <span data-ttu-id="44ba2-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44ba2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44ba2-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44ba2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44ba2-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44ba2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44ba2-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44ba2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ba2-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44ba2-135">See also</span></span>

- [<span data-ttu-id="44ba2-136">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44ba2-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="44ba2-137">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44ba2-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="44ba2-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44ba2-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
