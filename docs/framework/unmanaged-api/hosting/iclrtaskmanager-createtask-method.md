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
ms.openlocfilehash: 8833daa9cd385a1a76c5b706f15a76bb15139b84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763422"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="73ee7-102">ICLRTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="73ee7-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="73ee7-103">Požádá o explicitně, že modul CLR (CLR) vytvoří nový úkol.</span><span class="sxs-lookup"><span data-stu-id="73ee7-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ee7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73ee7-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73ee7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73ee7-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="73ee7-106">[out] Ukazatel na adresu nově vytvořeného [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), nebo hodnota null, pokud úlohu nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="73ee7-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73ee7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73ee7-107">Return Value</span></span>  
  
|<span data-ttu-id="73ee7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73ee7-108">HRESULT</span></span>|<span data-ttu-id="73ee7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="73ee7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73ee7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="73ee7-110">S_OK</span></span>|<span data-ttu-id="73ee7-111">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="73ee7-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="73ee7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="73ee7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="73ee7-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="73ee7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="73ee7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="73ee7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="73ee7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="73ee7-115">The call timed out.</span></span>|  
|<span data-ttu-id="73ee7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="73ee7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="73ee7-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="73ee7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="73ee7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="73ee7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="73ee7-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="73ee7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="73ee7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73ee7-120">E_FAIL</span></span>|<span data-ttu-id="73ee7-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="73ee7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="73ee7-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="73ee7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="73ee7-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="73ee7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="73ee7-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="73ee7-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="73ee7-125">Nedostatek paměti je možné přidělit požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="73ee7-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73ee7-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73ee7-126">Remarks</span></span>  
 <span data-ttu-id="73ee7-127">Modul CLR vytvoří nový úkol automaticky při inicializaci, když uživatelský kód vytvoří vlákno pomocí typů v <xref:System.Threading> obor názvů, nebo když je vyšší velikost fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="73ee7-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="73ee7-128">Také vytvoří úkoly při nespravovaný kód zavolá spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="73ee7-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="73ee7-129">`CreateTask` umožňuje hostiteli, aby požadavek na explicitní, CLR vytvoří nový úkol.</span><span class="sxs-lookup"><span data-stu-id="73ee7-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="73ee7-130">Například můžete hostitele vyvolat tuto metodu za účelem předem inicializovat datové struktury.</span><span class="sxs-lookup"><span data-stu-id="73ee7-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="73ee7-131">Nová úloha se vrátí v pozastaveném stavu a činnost průvodce zůstává přerušena dokud explicitně volá hostitele [ihosttask::Start –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="73ee7-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73ee7-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73ee7-132">Requirements</span></span>  
 <span data-ttu-id="73ee7-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73ee7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73ee7-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73ee7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73ee7-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73ee7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73ee7-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73ee7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ee7-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73ee7-137">See also</span></span>

- [<span data-ttu-id="73ee7-138">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73ee7-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="73ee7-139">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73ee7-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="73ee7-140">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73ee7-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="73ee7-141">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73ee7-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
