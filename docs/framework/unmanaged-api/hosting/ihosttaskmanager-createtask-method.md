---
title: "IHostTaskManager::CreateTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.CreateTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ba71fcd35b16654ab67db3f657f7821c23b702
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="bfd34-102">IHostTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="bfd34-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="bfd34-103">Požadavky, že hostitel vytvořit novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="bfd34-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfd34-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfd34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfd34-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="bfd34-106">[v] Požadovaná velikost v bajtech požadovaný zásobník nebo 0 (nula) pro výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="bfd34-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="bfd34-107">[v] Ukazatel na funkci úloha se má spustit.</span><span class="sxs-lookup"><span data-stu-id="bfd34-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="bfd34-108">[v] Ukazatel na data uživatele předávané do funkce, nebo hodnota null, pokud funkci nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="bfd34-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="bfd34-109">[out] Ukazatel na adresu [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance vytvořené hostitele, nebo hodnota null, pokud nelze vytvořit úlohu.</span><span class="sxs-lookup"><span data-stu-id="bfd34-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="bfd34-110">Úkol zůstane v pozastaveném stavu, dokud se explicitně spustí volání [ihosttask::Start –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="bfd34-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfd34-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bfd34-111">Return Value</span></span>  
  
|<span data-ttu-id="bfd34-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bfd34-112">HRESULT</span></span>|<span data-ttu-id="bfd34-113">Popis</span><span class="sxs-lookup"><span data-stu-id="bfd34-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bfd34-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bfd34-114">S_OK</span></span>|<span data-ttu-id="bfd34-115">`CreateTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="bfd34-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="bfd34-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bfd34-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bfd34-117">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="bfd34-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bfd34-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfd34-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bfd34-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="bfd34-119">The call timed out.</span></span>|  
|<span data-ttu-id="bfd34-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bfd34-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bfd34-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="bfd34-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bfd34-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bfd34-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bfd34-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="bfd34-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bfd34-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bfd34-124">E_FAIL</span></span>|<span data-ttu-id="bfd34-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="bfd34-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bfd34-126">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="bfd34-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bfd34-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bfd34-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bfd34-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bfd34-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bfd34-129">Nedostatek paměti nebylo k dispozici k vytvoření požadované úlohy.</span><span class="sxs-lookup"><span data-stu-id="bfd34-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfd34-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bfd34-130">Remarks</span></span>  
 <span data-ttu-id="bfd34-131">Volání CLR `CreateTask` k vyžádání, že hostitel vytvořit novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="bfd34-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="bfd34-132">Vrátí ukazatele rozhraní na hostiteli `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="bfd34-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="bfd34-133">Vrácený úloh musí pozastaveny, dokud se explicitně spustí volání `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="bfd34-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfd34-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bfd34-134">Requirements</span></span>  
 <span data-ttu-id="bfd34-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfd34-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfd34-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bfd34-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfd34-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bfd34-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfd34-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfd34-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd34-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfd34-139">See Also</span></span>  
 [<span data-ttu-id="bfd34-140">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfd34-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="bfd34-141">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfd34-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="bfd34-142">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfd34-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="bfd34-143">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfd34-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
