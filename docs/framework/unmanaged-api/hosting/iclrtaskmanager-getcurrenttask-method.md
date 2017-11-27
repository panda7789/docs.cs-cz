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
ms.openlocfilehash: 1adf2959beb8687dc3d08ceb7a118bb19a5fa68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="90ca5-102">ICLRTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="90ca5-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="90ca5-103">Získá [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instanci, která je aktuálně spuštěna ve vláknu operačního systému, ze kterého pochází volání metody.</span><span class="sxs-lookup"><span data-stu-id="90ca5-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ca5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90ca5-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90ca5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90ca5-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="90ca5-106">[out] Ukazatel na adresu `ICLRTask` instanci, která je aktuálně spuštěných ve vláknu operačního systému, ze kterého pochází volání nebo hodnota null, pokud žádná úloha je aktuálně spuštěné na tento přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="90ca5-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90ca5-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90ca5-107">Return Value</span></span>  
  
|<span data-ttu-id="90ca5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90ca5-108">HRESULT</span></span>|<span data-ttu-id="90ca5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="90ca5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90ca5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="90ca5-110">S_OK</span></span>|<span data-ttu-id="90ca5-111">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="90ca5-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="90ca5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="90ca5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="90ca5-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="90ca5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="90ca5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="90ca5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="90ca5-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="90ca5-115">The call timed out.</span></span>|  
|<span data-ttu-id="90ca5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="90ca5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="90ca5-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="90ca5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="90ca5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="90ca5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="90ca5-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="90ca5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="90ca5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="90ca5-120">E_FAIL</span></span>|<span data-ttu-id="90ca5-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="90ca5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="90ca5-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="90ca5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="90ca5-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="90ca5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90ca5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90ca5-124">Remarks</span></span>  
 <span data-ttu-id="90ca5-125">`ICLRTask` Instanci `ppTask` parametr odkazuje na představuje aktuálně prováděné úlohy pro modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="90ca5-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="90ca5-126">`ICLRTask` Instance souvisí s odpovídající [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která představuje úlohu pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="90ca5-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ca5-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90ca5-127">Requirements</span></span>  
 <span data-ttu-id="90ca5-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ca5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ca5-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90ca5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90ca5-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90ca5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90ca5-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ca5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ca5-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="90ca5-132">See Also</span></span>  
 [<span data-ttu-id="90ca5-133">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ca5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="90ca5-134">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ca5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="90ca5-135">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ca5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="90ca5-136">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ca5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
