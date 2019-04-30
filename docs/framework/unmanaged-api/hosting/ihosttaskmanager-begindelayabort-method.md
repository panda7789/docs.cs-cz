---
title: IHostTaskManager::BeginDelayAbort – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 328462343669b3ea6bed2d86514ea348f6ae2b1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789523"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="82e5f-102">IHostTaskManager::BeginDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="82e5f-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="82e5f-103">Upozorní, že na hostitele, spravovaný kód je zadání období, ve kterém nesmí být aktuální úloha přerušena.</span><span class="sxs-lookup"><span data-stu-id="82e5f-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e5f-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="82e5f-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="82e5f-105">Return Value</span></span>  
  
|<span data-ttu-id="82e5f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82e5f-106">HRESULT</span></span>|<span data-ttu-id="82e5f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="82e5f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82e5f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="82e5f-108">S_OK</span></span>|<span data-ttu-id="82e5f-109">`BeginDelayAbort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="82e5f-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="82e5f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82e5f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82e5f-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="82e5f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82e5f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82e5f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82e5f-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="82e5f-113">The call timed out.</span></span>|  
|<span data-ttu-id="82e5f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82e5f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82e5f-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="82e5f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82e5f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82e5f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82e5f-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="82e5f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82e5f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82e5f-118">E_FAIL</span></span>|<span data-ttu-id="82e5f-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="82e5f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82e5f-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="82e5f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82e5f-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="82e5f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="82e5f-122">E_UNEXPECTED, JE-</span><span class="sxs-lookup"><span data-stu-id="82e5f-122">E_UNEXPECTED</span></span>|<span data-ttu-id="82e5f-123">`BeginDelayAbort` již byla volána, ale odpovídající volání [enddelayabort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) ještě nebylo přijato.</span><span class="sxs-lookup"><span data-stu-id="82e5f-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82e5f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82e5f-124">Remarks</span></span>  
 <span data-ttu-id="82e5f-125">Hostitel nesmí přerušit aktuální úkol až do `EndDelayAbort` je volána.</span><span class="sxs-lookup"><span data-stu-id="82e5f-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="82e5f-126">Pokud jiného volání `BeginDelayAbort` vytvořit bez opětovné volání `EndDelayAbort`, hostitele by měl vrátit e_unexpected, je-z `BeginDelayAbort`a neměla by mít žádné akce.</span><span class="sxs-lookup"><span data-stu-id="82e5f-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e5f-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82e5f-127">Requirements</span></span>  
 <span data-ttu-id="82e5f-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e5f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e5f-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82e5f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82e5f-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82e5f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82e5f-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e5f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e5f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82e5f-132">See also</span></span>

- [<span data-ttu-id="82e5f-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e5f-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="82e5f-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e5f-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="82e5f-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e5f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
