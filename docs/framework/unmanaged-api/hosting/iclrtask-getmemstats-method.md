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
ms.openlocfilehash: 0d2975d6247cd9ecdb07b564d77518151404c7d0
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762454"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="346f3-102">ICLRTask::GetMemStats – metoda</span><span class="sxs-lookup"><span data-stu-id="346f3-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="346f3-103">Získá informace o využití statistické paměti týkající se úkolu, který představuje aktuální instance [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="346f3-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="346f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="346f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="346f3-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="346f3-106">mimo Ukazatel na instanci [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) , která obsahuje podrobnosti o využití paměti úlohy, včetně počtu přidělených bajtů.</span><span class="sxs-lookup"><span data-stu-id="346f3-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="346f3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="346f3-107">Return Value</span></span>  
  
|<span data-ttu-id="346f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="346f3-108">HRESULT</span></span>|<span data-ttu-id="346f3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="346f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="346f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="346f3-110">S_OK</span></span>|<span data-ttu-id="346f3-111">`GetMemStats`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="346f3-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="346f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="346f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="346f3-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="346f3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="346f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="346f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="346f3-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="346f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="346f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="346f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="346f3-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="346f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="346f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="346f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="346f3-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="346f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="346f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="346f3-120">E_FAIL</span></span>|<span data-ttu-id="346f3-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="346f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="346f3-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="346f3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="346f3-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="346f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="346f3-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="346f3-124">Requirements</span></span>  
 <span data-ttu-id="346f3-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="346f3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="346f3-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="346f3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="346f3-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="346f3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="346f3-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="346f3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346f3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="346f3-129">See also</span></span>

- [<span data-ttu-id="346f3-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="346f3-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="346f3-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="346f3-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="346f3-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="346f3-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="346f3-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="346f3-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
