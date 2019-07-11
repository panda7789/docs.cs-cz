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
ms.openlocfilehash: 0e25f2e49ab25d2df827fdd59526b13976d21219
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756564"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="5c5a7-102">IHostTaskManager::Sleep – metoda</span><span class="sxs-lookup"><span data-stu-id="5c5a7-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="5c5a7-103">Upozorňuje hostitele, že aktuální úloha přechází do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c5a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c5a7-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c5a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c5a7-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="5c5a7-106">[in] Časový interval v milisekundách, která bude v režimu spánku vlákna.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="5c5a7-107">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnot výčtu označující akci hostitele zabere, pokud tato akce bloky.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c5a7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c5a7-108">Return Value</span></span>  
  
|<span data-ttu-id="5c5a7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c5a7-109">HRESULT</span></span>|<span data-ttu-id="5c5a7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5c5a7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c5a7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c5a7-111">S_OK</span></span>|<span data-ttu-id="5c5a7-112">`Sleep` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="5c5a7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c5a7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c5a7-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c5a7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c5a7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c5a7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c5a7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c5a7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c5a7-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c5a7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c5a7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c5a7-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c5a7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c5a7-121">E_FAIL</span></span>|<span data-ttu-id="5c5a7-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c5a7-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c5a7-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c5a7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c5a7-125">Remarks</span></span>  
 <span data-ttu-id="5c5a7-126">CLR volá obvykle `IHostTaskManager::Sleep` při <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> volání z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="5c5a7-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c5a7-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c5a7-127">Requirements</span></span>  
 <span data-ttu-id="5c5a7-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c5a7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c5a7-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c5a7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c5a7-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c5a7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c5a7-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c5a7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5a7-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c5a7-132">See also</span></span>

- [<span data-ttu-id="5c5a7-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c5a7-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5c5a7-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c5a7-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5c5a7-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c5a7-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5c5a7-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c5a7-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
