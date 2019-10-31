---
title: ICLRTask::GetMemStats – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
ms.openlocfilehash: 0bf8b6f393806e590be8f97dbfe2d01d5746c339
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139700"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="19f30-102">ICLRTask::GetMemStats – metoda</span><span class="sxs-lookup"><span data-stu-id="19f30-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="19f30-103">Získá informace o využití statistické paměti týkající se úkolu, který představuje aktuální instance [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="19f30-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19f30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19f30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19f30-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="19f30-106">mimo Ukazatel na instanci [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) , která obsahuje podrobnosti o využití paměti úlohy, včetně počtu přidělených bajtů.</span><span class="sxs-lookup"><span data-stu-id="19f30-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19f30-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="19f30-107">Return Value</span></span>  
  
|<span data-ttu-id="19f30-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19f30-108">HRESULT</span></span>|<span data-ttu-id="19f30-109">Popis</span><span class="sxs-lookup"><span data-stu-id="19f30-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19f30-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="19f30-110">S_OK</span></span>|<span data-ttu-id="19f30-111">`GetMemStats` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="19f30-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="19f30-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19f30-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19f30-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="19f30-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19f30-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19f30-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19f30-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="19f30-115">The call timed out.</span></span>|  
|<span data-ttu-id="19f30-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19f30-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19f30-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="19f30-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19f30-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19f30-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19f30-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="19f30-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19f30-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19f30-120">E_FAIL</span></span>|<span data-ttu-id="19f30-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="19f30-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19f30-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="19f30-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19f30-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="19f30-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19f30-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19f30-124">Requirements</span></span>  
 <span data-ttu-id="19f30-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19f30-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19f30-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19f30-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19f30-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="19f30-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19f30-128">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19f30-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f30-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19f30-129">See also</span></span>

- [<span data-ttu-id="19f30-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19f30-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="19f30-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19f30-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="19f30-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19f30-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="19f30-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19f30-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
