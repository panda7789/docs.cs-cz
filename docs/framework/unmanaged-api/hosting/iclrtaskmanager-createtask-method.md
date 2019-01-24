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
ms.openlocfilehash: 3556c9c73d354f096316cf67741a055e9f46adfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600271"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="64067-102">ICLRTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="64067-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="64067-103">Požádá o explicitně, že modul CLR (CLR) vytvoří nový úkol.</span><span class="sxs-lookup"><span data-stu-id="64067-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64067-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64067-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64067-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64067-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="64067-106">[out] Ukazatel na adresu nově vytvořeného [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), nebo hodnota null, pokud úlohu nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="64067-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64067-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="64067-107">Return Value</span></span>  
  
|<span data-ttu-id="64067-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64067-108">HRESULT</span></span>|<span data-ttu-id="64067-109">Popis</span><span class="sxs-lookup"><span data-stu-id="64067-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64067-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="64067-110">S_OK</span></span>|<span data-ttu-id="64067-111">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="64067-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="64067-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64067-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64067-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="64067-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64067-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64067-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64067-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="64067-115">The call timed out.</span></span>|  
|<span data-ttu-id="64067-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64067-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64067-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="64067-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64067-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64067-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64067-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="64067-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64067-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="64067-120">E_FAIL</span></span>|<span data-ttu-id="64067-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="64067-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64067-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="64067-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64067-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="64067-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="64067-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="64067-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="64067-125">Nedostatek paměti je možné přidělit požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="64067-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64067-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64067-126">Remarks</span></span>  
 <span data-ttu-id="64067-127">Modul CLR vytvoří nový úkol automaticky při inicializaci, když uživatelský kód vytvoří vlákno pomocí typů v <xref:System.Threading> obor názvů, nebo když je vyšší velikost fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="64067-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="64067-128">Také vytvoří úkoly při nespravovaný kód zavolá spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="64067-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="64067-129">`CreateTask` umožňuje hostiteli, aby požadavek na explicitní, CLR vytvoří nový úkol.</span><span class="sxs-lookup"><span data-stu-id="64067-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="64067-130">Například můžete hostitele vyvolat tuto metodu za účelem předem inicializovat datové struktury.</span><span class="sxs-lookup"><span data-stu-id="64067-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64067-131">Nová úloha se vrátí v pozastaveném stavu a činnost průvodce zůstává přerušena dokud explicitně volá hostitele [ihosttask::Start –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="64067-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64067-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64067-132">Requirements</span></span>  
 <span data-ttu-id="64067-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64067-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64067-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64067-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64067-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64067-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64067-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64067-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64067-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64067-137">See also</span></span>
- [<span data-ttu-id="64067-138">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64067-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="64067-139">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64067-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="64067-140">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64067-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="64067-141">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64067-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
