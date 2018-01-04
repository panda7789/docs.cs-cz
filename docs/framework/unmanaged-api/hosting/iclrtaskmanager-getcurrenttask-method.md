---
title: "ICLRTaskManager::GetCurrentTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04d12e3ff17cc422121e62f08a77f0271ed78346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="cb578-102">ICLRTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="cb578-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="cb578-103">Získá [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instanci, která je aktuálně spuštěna ve vláknu operačního systému, ze kterého pochází volání metody.</span><span class="sxs-lookup"><span data-stu-id="cb578-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb578-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb578-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb578-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb578-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="cb578-106">[out] Ukazatel na adresu `ICLRTask` instanci, která je aktuálně spuštěných ve vláknu operačního systému, ze kterého pochází volání nebo hodnota null, pokud žádná úloha je aktuálně spuštěné na tento přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="cb578-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb578-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cb578-107">Return Value</span></span>  
  
|<span data-ttu-id="cb578-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb578-108">HRESULT</span></span>|<span data-ttu-id="cb578-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cb578-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb578-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb578-110">S_OK</span></span>|<span data-ttu-id="cb578-111">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="cb578-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="cb578-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb578-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb578-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cb578-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb578-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb578-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb578-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="cb578-115">The call timed out.</span></span>|  
|<span data-ttu-id="cb578-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb578-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb578-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="cb578-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb578-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb578-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb578-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="cb578-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb578-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb578-120">E_FAIL</span></span>|<span data-ttu-id="cb578-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="cb578-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb578-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="cb578-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb578-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cb578-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb578-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb578-124">Remarks</span></span>  
 <span data-ttu-id="cb578-125">`ICLRTask` Instanci `ppTask` parametr odkazuje na představuje aktuálně prováděné úlohy pro modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cb578-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="cb578-126">`ICLRTask` Instance souvisí s odpovídající [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která představuje úlohu pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="cb578-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb578-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb578-127">Requirements</span></span>  
 <span data-ttu-id="cb578-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb578-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb578-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb578-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb578-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb578-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb578-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb578-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb578-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb578-132">See Also</span></span>  
 [<span data-ttu-id="cb578-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb578-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cb578-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb578-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cb578-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb578-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="cb578-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb578-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
