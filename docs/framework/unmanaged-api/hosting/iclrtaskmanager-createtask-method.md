---
title: "ICLRTaskManager::CreateTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9e78db6e43397709f913f8f79a617221f98db87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="4298c-102">ICLRTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="4298c-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="4298c-103">Explicitně požadavků, že modul CLR (CLR) vytvořit novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="4298c-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4298c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4298c-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4298c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4298c-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="4298c-106">[out] Ukazatel na adresu nově vytvořený [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), nebo hodnota null, pokud úlohy se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="4298c-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4298c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4298c-107">Return Value</span></span>  
  
|<span data-ttu-id="4298c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4298c-108">HRESULT</span></span>|<span data-ttu-id="4298c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4298c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4298c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4298c-110">S_OK</span></span>|<span data-ttu-id="4298c-111">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4298c-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="4298c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4298c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4298c-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4298c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4298c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4298c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4298c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4298c-115">The call timed out.</span></span>|  
|<span data-ttu-id="4298c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4298c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4298c-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="4298c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4298c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4298c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4298c-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="4298c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4298c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4298c-120">E_FAIL</span></span>|<span data-ttu-id="4298c-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="4298c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4298c-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4298c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4298c-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4298c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4298c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4298c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4298c-125">Je k dispozici přidělit požadovaný prostředek není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="4298c-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4298c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4298c-126">Remarks</span></span>  
 <span data-ttu-id="4298c-127">Modul CLR vytvoří novou úlohu automaticky při inicializaci, když uživatelský kód vytvoří vlákno pomocí typy v <xref:System.Threading> obor názvů, nebo když se zvýší velikost fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="4298c-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="4298c-128">Vytváří také úlohy, když nespravovaný kód zavolá spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="4298c-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="4298c-129">`CreateTask`umožňuje hostiteli, aby požadavek explicitní, modul CLR vytvořit novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="4298c-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="4298c-130">Například můžete hostitele vyvolat tuto metodu za účelem preinitialize datové struktury.</span><span class="sxs-lookup"><span data-stu-id="4298c-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4298c-131">Nová úloha je vrácený v pozastaveném stavu a zůstává přerušena, dokud hostitel explicitně volá [ihosttask::Start –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="4298c-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4298c-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4298c-132">Requirements</span></span>  
 <span data-ttu-id="4298c-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4298c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4298c-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4298c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4298c-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4298c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4298c-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4298c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4298c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="4298c-137">See Also</span></span>  
 [<span data-ttu-id="4298c-138">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4298c-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4298c-139">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4298c-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4298c-140">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4298c-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4298c-141">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4298c-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
