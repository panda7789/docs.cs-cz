---
title: IHostTaskManager::CreateTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33cffb086609432f5207310fc565bd34cccd7642
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698645"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="a3c28-102">IHostTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="a3c28-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="a3c28-103">Požadavky, že hostitel vytvoří nový úkol.</span><span class="sxs-lookup"><span data-stu-id="a3c28-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3c28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3c28-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3c28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3c28-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="a3c28-106">[in] Požadovaná velikost v bajtech, požadovaná zásobníku nebo 0 (nula) pro výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="a3c28-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="a3c28-107">[in] Ukazatel na funkci úkolu se má provést.</span><span class="sxs-lookup"><span data-stu-id="a3c28-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="a3c28-108">[in] Ukazatel na data uživatelů mají být předány funkce nebo hodnota null, pokud funkce nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="a3c28-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="a3c28-109">[out] Ukazatel na adresu [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance vytvořené hostitele, nebo hodnota null, pokud úlohu nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="a3c28-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="a3c28-110">Úkol zůstane v pozastaveném stavu, dokud se explicitně spustí volání [ihosttask::Start –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="a3c28-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3c28-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a3c28-111">Return Value</span></span>  
  
|<span data-ttu-id="a3c28-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3c28-112">HRESULT</span></span>|<span data-ttu-id="a3c28-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a3c28-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3c28-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3c28-114">S_OK</span></span>|<span data-ttu-id="a3c28-115">`CreateTask` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a3c28-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="a3c28-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3c28-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3c28-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a3c28-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a3c28-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a3c28-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a3c28-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a3c28-119">The call timed out.</span></span>|  
|<span data-ttu-id="a3c28-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a3c28-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a3c28-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a3c28-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a3c28-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a3c28-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a3c28-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a3c28-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a3c28-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3c28-124">E_FAIL</span></span>|<span data-ttu-id="a3c28-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a3c28-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a3c28-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a3c28-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a3c28-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a3c28-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a3c28-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a3c28-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a3c28-129">Není dostatek paměti bylo možné vytvořit požadovanou úlohu.</span><span class="sxs-lookup"><span data-stu-id="a3c28-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3c28-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3c28-130">Remarks</span></span>  
 <span data-ttu-id="a3c28-131">Volání CLR `CreateTask` požádat, aby hostitel vytvoří nový úkol.</span><span class="sxs-lookup"><span data-stu-id="a3c28-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="a3c28-132">Vrátí ukazatel rozhraní k hostiteli `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="a3c28-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="a3c28-133">Vrácená úloha musí pozastaveny, dokud se explicitně spustí volání `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="a3c28-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3c28-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3c28-134">Requirements</span></span>  
 <span data-ttu-id="a3c28-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3c28-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3c28-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3c28-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3c28-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3c28-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3c28-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3c28-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c28-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3c28-139">See also</span></span>
- [<span data-ttu-id="a3c28-140">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3c28-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a3c28-141">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3c28-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a3c28-142">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3c28-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a3c28-143">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3c28-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
