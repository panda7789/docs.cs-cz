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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796658"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="4c01b-102">IHostTaskManager::Sleep – metoda</span><span class="sxs-lookup"><span data-stu-id="4c01b-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="4c01b-103">Upozorňuje hostitele, že aktuální úloha přechází do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="4c01b-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c01b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c01b-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c01b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c01b-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="4c01b-106">[in] Časový interval v milisekundách, která bude v režimu spánku vlákna.</span><span class="sxs-lookup"><span data-stu-id="4c01b-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="4c01b-107">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnot výčtu označující akci hostitele zabere, pokud tato akce bloky.</span><span class="sxs-lookup"><span data-stu-id="4c01b-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c01b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4c01b-108">Return Value</span></span>  
  
|<span data-ttu-id="4c01b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c01b-109">HRESULT</span></span>|<span data-ttu-id="4c01b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4c01b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c01b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c01b-111">S_OK</span></span>|<span data-ttu-id="4c01b-112">`Sleep` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4c01b-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="4c01b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c01b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c01b-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4c01b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c01b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c01b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c01b-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4c01b-116">The call timed out.</span></span>|  
|<span data-ttu-id="4c01b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c01b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c01b-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="4c01b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c01b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c01b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c01b-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="4c01b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c01b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c01b-121">E_FAIL</span></span>|<span data-ttu-id="4c01b-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="4c01b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c01b-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4c01b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c01b-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c01b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c01b-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c01b-125">Remarks</span></span>  
 <span data-ttu-id="4c01b-126">CLR volá obvykle `IHostTaskManager::Sleep` při <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> volání z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="4c01b-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c01b-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c01b-127">Requirements</span></span>  
 <span data-ttu-id="4c01b-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c01b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c01b-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c01b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c01b-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c01b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c01b-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c01b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c01b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c01b-132">See also</span></span>

- [<span data-ttu-id="4c01b-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c01b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4c01b-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c01b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4c01b-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c01b-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4c01b-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c01b-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
