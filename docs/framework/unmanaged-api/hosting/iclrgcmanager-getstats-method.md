---
title: ICLRGCManager::GetStats – metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 9e8b65c735028029f4fb44c2640df74ef171d9de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141138"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="64ef7-102">ICLRGCManager::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="64ef7-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="64ef7-103">Získá sadu aktuálních statistik o systému uvolňování paměti modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="64ef7-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ef7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64ef7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64ef7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64ef7-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="64ef7-106">[in, out] Instance [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) , která obsahuje požadované statistiky.</span><span class="sxs-lookup"><span data-stu-id="64ef7-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64ef7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="64ef7-107">Return Value</span></span>  
  
|<span data-ttu-id="64ef7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64ef7-108">HRESULT</span></span>|<span data-ttu-id="64ef7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="64ef7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64ef7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="64ef7-110">S_OK</span></span>|<span data-ttu-id="64ef7-111">`GetStats` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="64ef7-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="64ef7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64ef7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64ef7-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="64ef7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64ef7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64ef7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64ef7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="64ef7-115">The call timed out.</span></span>|  
|<span data-ttu-id="64ef7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64ef7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64ef7-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="64ef7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64ef7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64ef7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64ef7-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="64ef7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64ef7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="64ef7-120">E_FAIL</span></span>|<span data-ttu-id="64ef7-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="64ef7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64ef7-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="64ef7-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64ef7-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="64ef7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64ef7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64ef7-124">Remarks</span></span>  
 <span data-ttu-id="64ef7-125">CLR vypočítá a vrátí pouze ty statistiky, které jsou určeny polem `Flags` `pStats`.</span><span class="sxs-lookup"><span data-stu-id="64ef7-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="64ef7-126">Nastavte pole `Flags` na jednu nebo více hodnot výčtu [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) , aby se určilo, které statistiky ve struktuře [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) se mají nastavit.</span><span class="sxs-lookup"><span data-stu-id="64ef7-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="64ef7-127">Příklad použití je následující:</span><span class="sxs-lookup"><span data-stu-id="64ef7-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="64ef7-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64ef7-128">Requirements</span></span>  
 <span data-ttu-id="64ef7-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64ef7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64ef7-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="64ef7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64ef7-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="64ef7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64ef7-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64ef7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ef7-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64ef7-133">See also</span></span>

- [<span data-ttu-id="64ef7-134">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="64ef7-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="64ef7-135">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="64ef7-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="64ef7-136">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="64ef7-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="64ef7-137">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="64ef7-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="64ef7-138">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64ef7-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="64ef7-139">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64ef7-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="64ef7-140">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="64ef7-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="64ef7-141">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="64ef7-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="64ef7-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="64ef7-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
