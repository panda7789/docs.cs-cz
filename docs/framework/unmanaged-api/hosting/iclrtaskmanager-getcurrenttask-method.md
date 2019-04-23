---
title: ICLRTaskManager::GetCurrentTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db333cd97963ca8ef26673c0ba5cbf352fa331b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165305"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="e019b-102">ICLRTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="e019b-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="e019b-103">Získá [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instanci, která je aktuálně spuštěna ve vlákně operačního systému, ze kterého pochází volání metody.</span><span class="sxs-lookup"><span data-stu-id="e019b-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e019b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e019b-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e019b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e019b-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="e019b-106">[out] Ukazatel na adresu `ICLRTask` instanci, která se právě spouští ve vlákně operačního systému, ze kterého bylo volání provedeno, nebo hodnota null, pokud žádná úloha právě probíhá v tomto vlákně.</span><span class="sxs-lookup"><span data-stu-id="e019b-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e019b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e019b-107">Return Value</span></span>  
  
|<span data-ttu-id="e019b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e019b-108">HRESULT</span></span>|<span data-ttu-id="e019b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e019b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e019b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e019b-110">S_OK</span></span>|<span data-ttu-id="e019b-111">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="e019b-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="e019b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e019b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e019b-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e019b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e019b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e019b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e019b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e019b-115">The call timed out.</span></span>|  
|<span data-ttu-id="e019b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e019b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e019b-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="e019b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e019b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e019b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e019b-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="e019b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e019b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e019b-120">E_FAIL</span></span>|<span data-ttu-id="e019b-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="e019b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e019b-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e019b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e019b-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e019b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e019b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e019b-124">Remarks</span></span>  
 <span data-ttu-id="e019b-125">`ICLRTask` Instanci, která `ppTask` parametr odkazuje na představuje aktuálně prováděný úkol pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="e019b-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="e019b-126">`ICLRTask` Instance je spojen s odpovídající [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která představuje úkol pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="e019b-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e019b-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e019b-127">Requirements</span></span>  
 <span data-ttu-id="e019b-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e019b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e019b-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e019b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e019b-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e019b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e019b-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e019b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e019b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e019b-132">See also</span></span>

- [<span data-ttu-id="e019b-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e019b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e019b-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e019b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e019b-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e019b-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e019b-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e019b-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
