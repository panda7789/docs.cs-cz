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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab388459df88e91093459658ced4d4b4eb023460
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758984"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="ed3f6-102">ICLRTask::GetMemStats – metoda</span><span class="sxs-lookup"><span data-stu-id="ed3f6-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="ed3f6-103">Získá informace o využití paměti statistické souvisejícím s úlohou, která aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed3f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed3f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed3f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed3f6-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="ed3f6-106">[out] Ukazatel [cor_gc_thread_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance, která obsahuje podrobnosti o využití paměti úlohy, včetně počtu bajtů přidělených.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed3f6-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed3f6-107">Return Value</span></span>  
  
|<span data-ttu-id="ed3f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed3f6-108">HRESULT</span></span>|<span data-ttu-id="ed3f6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ed3f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed3f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed3f6-110">S_OK</span></span>|<span data-ttu-id="ed3f6-111">`GetMemStats` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="ed3f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed3f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed3f6-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed3f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed3f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed3f6-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="ed3f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed3f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed3f6-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed3f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed3f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed3f6-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed3f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed3f6-120">E_FAIL</span></span>|<span data-ttu-id="ed3f6-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed3f6-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed3f6-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed3f6-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed3f6-124">Requirements</span></span>  
 <span data-ttu-id="ed3f6-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed3f6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed3f6-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed3f6-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed3f6-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed3f6-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed3f6-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed3f6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3f6-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed3f6-129">See also</span></span>

- [<span data-ttu-id="ed3f6-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed3f6-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ed3f6-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed3f6-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ed3f6-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed3f6-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ed3f6-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed3f6-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
