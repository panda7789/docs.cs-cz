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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a89ea76d78431ae8833602588379d5150e473710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938307"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="9cfdf-102">ICLRTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="9cfdf-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="9cfdf-103">Požadavky explicitně, aby modul CLR (Common Language Runtime) vytvořil nový úkol.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cfdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cfdf-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cfdf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cfdf-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="9cfdf-106">mimo Ukazatel na adresu nově vytvořeného [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)nebo hodnotu null, pokud úlohu nebylo možné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cfdf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9cfdf-107">Return Value</span></span>  
  
|<span data-ttu-id="9cfdf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cfdf-108">HRESULT</span></span>|<span data-ttu-id="9cfdf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9cfdf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cfdf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cfdf-110">S_OK</span></span>|<span data-ttu-id="9cfdf-111">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="9cfdf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9cfdf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9cfdf-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9cfdf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9cfdf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9cfdf-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-115">The call timed out.</span></span>|  
|<span data-ttu-id="9cfdf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9cfdf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9cfdf-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9cfdf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9cfdf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9cfdf-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9cfdf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9cfdf-120">E_FAIL</span></span>|<span data-ttu-id="9cfdf-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9cfdf-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9cfdf-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9cfdf-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9cfdf-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9cfdf-125">K přidělení požadovaného prostředku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cfdf-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cfdf-126">Remarks</span></span>  
 <span data-ttu-id="9cfdf-127">Modul CLR vytvoří automaticky nový úkol po inicializaci, když uživatelský kód vytvoří vlákno pomocí typů v <xref:System.Threading> oboru názvů nebo při zvýšení velikosti fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="9cfdf-128">Také vytvoří úlohy, pokud nespravovaný kód provede volání spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="9cfdf-129">`CreateTask`umožňuje hostiteli vytvořit explicitní požadavek, který vytvoří nový úkol CLR.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="9cfdf-130">Například hostitel může vyvolat tuto metodu pro předinicializaci datových struktur.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9cfdf-131">Nový úkol se vrátí v pozastaveném stavu a zůstane pozastaven, dokud hostitel explicitně nevolá [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="9cfdf-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cfdf-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cfdf-132">Requirements</span></span>  
 <span data-ttu-id="9cfdf-133">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cfdf-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cfdf-134">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9cfdf-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cfdf-135">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9cfdf-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cfdf-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cfdf-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfdf-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cfdf-137">See also</span></span>

- [<span data-ttu-id="9cfdf-138">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cfdf-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9cfdf-139">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cfdf-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9cfdf-140">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cfdf-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9cfdf-141">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cfdf-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
