---
title: IHostTaskManager::Sleep – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4618f7ea08aa304ff5e77800cf3c0a90dd88fdbd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110914"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="15d63-102">IHostTaskManager::Sleep – metoda</span><span class="sxs-lookup"><span data-stu-id="15d63-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="15d63-103">Upozorňuje hostitele, že aktuální úloha přechází do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="15d63-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15d63-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15d63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15d63-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="15d63-106">[in] Časový interval v milisekundách, která bude v režimu spánku vlákna.</span><span class="sxs-lookup"><span data-stu-id="15d63-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="15d63-107">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnot výčtu označující akci hostitele zabere, pokud tato akce bloky.</span><span class="sxs-lookup"><span data-stu-id="15d63-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15d63-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="15d63-108">Return Value</span></span>  
  
|<span data-ttu-id="15d63-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15d63-109">HRESULT</span></span>|<span data-ttu-id="15d63-110">Popis</span><span class="sxs-lookup"><span data-stu-id="15d63-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15d63-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="15d63-111">S_OK</span></span>|`Sleep` <span data-ttu-id="15d63-112">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="15d63-112">returned successfully.</span></span>|  
|<span data-ttu-id="15d63-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15d63-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15d63-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="15d63-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15d63-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15d63-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15d63-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="15d63-116">The call timed out.</span></span>|  
|<span data-ttu-id="15d63-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15d63-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15d63-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="15d63-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15d63-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15d63-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15d63-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="15d63-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15d63-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15d63-121">E_FAIL</span></span>|<span data-ttu-id="15d63-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="15d63-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15d63-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="15d63-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15d63-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="15d63-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15d63-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15d63-125">Remarks</span></span>  
 <span data-ttu-id="15d63-126">CLR volá obvykle `IHostTaskManager::Sleep` při <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> volání z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="15d63-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d63-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15d63-127">Requirements</span></span>  
 <span data-ttu-id="15d63-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d63-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d63-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15d63-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15d63-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15d63-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="15d63-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="15d63-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="15d63-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15d63-132">See also</span></span>

- [<span data-ttu-id="15d63-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15d63-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="15d63-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15d63-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="15d63-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15d63-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="15d63-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15d63-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
