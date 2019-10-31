---
title: ICLRTaskManager::CreateTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: fcb78dd5374ff97f23d7dfea63fe33fa96836958
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124534"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="21e8d-102">ICLRTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="21e8d-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="21e8d-103">Požadavky explicitně, aby modul CLR (Common Language Runtime) vytvořil nový úkol.</span><span class="sxs-lookup"><span data-stu-id="21e8d-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21e8d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21e8d-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="21e8d-106">mimo Ukazatel na adresu nově vytvořeného [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)nebo hodnotu null, pokud úlohu nebylo možné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="21e8d-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21e8d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="21e8d-107">Return Value</span></span>  
  
|<span data-ttu-id="21e8d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21e8d-108">HRESULT</span></span>|<span data-ttu-id="21e8d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="21e8d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21e8d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="21e8d-110">S_OK</span></span>|<span data-ttu-id="21e8d-111">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="21e8d-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="21e8d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21e8d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21e8d-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="21e8d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21e8d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21e8d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21e8d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="21e8d-115">The call timed out.</span></span>|  
|<span data-ttu-id="21e8d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21e8d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21e8d-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="21e8d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21e8d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21e8d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21e8d-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="21e8d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21e8d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21e8d-120">E_FAIL</span></span>|<span data-ttu-id="21e8d-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="21e8d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21e8d-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="21e8d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21e8d-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="21e8d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21e8d-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="21e8d-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="21e8d-125">K přidělení požadovaného prostředku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="21e8d-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21e8d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21e8d-126">Remarks</span></span>  
 <span data-ttu-id="21e8d-127">Modul CLR vytvoří automaticky nový úkol po inicializaci, když uživatelský kód vytvoří vlákno pomocí typů v oboru názvů <xref:System.Threading> nebo při zvýšení velikosti fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="21e8d-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="21e8d-128">Také vytvoří úlohy, pokud nespravovaný kód provede volání spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="21e8d-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="21e8d-129">`CreateTask` umožňuje hostiteli vytvořit explicitní požadavek, který vytvoří nový úkol CLR.</span><span class="sxs-lookup"><span data-stu-id="21e8d-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="21e8d-130">Například hostitel může vyvolat tuto metodu pro předinicializaci datových struktur.</span><span class="sxs-lookup"><span data-stu-id="21e8d-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="21e8d-131">Nový úkol se vrátí v pozastaveném stavu a zůstane pozastaven, dokud hostitel explicitně nevolá [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="21e8d-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e8d-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21e8d-132">Requirements</span></span>  
 <span data-ttu-id="21e8d-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e8d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e8d-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21e8d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21e8d-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="21e8d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21e8d-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e8d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e8d-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21e8d-137">See also</span></span>

- [<span data-ttu-id="21e8d-138">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e8d-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="21e8d-139">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e8d-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="21e8d-140">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e8d-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="21e8d-141">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e8d-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
