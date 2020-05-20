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
ms.openlocfilehash: 1e881b4a55a99bac3f9ca0e8db1556807b888f13
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616959"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="408e2-102">ICLRGCManager::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="408e2-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="408e2-103">Získá sadu aktuálních statistik o systému uvolňování paměti modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="408e2-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="408e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="408e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="408e2-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="408e2-106">[in, out] Instance [COR_GC_STATS](cor-gc-stats-structure.md) , která obsahuje požadované statistiky.</span><span class="sxs-lookup"><span data-stu-id="408e2-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="408e2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="408e2-107">Return Value</span></span>  
  
|<span data-ttu-id="408e2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="408e2-108">HRESULT</span></span>|<span data-ttu-id="408e2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="408e2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="408e2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="408e2-110">S_OK</span></span>|<span data-ttu-id="408e2-111">`GetStats`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="408e2-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="408e2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="408e2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="408e2-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="408e2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="408e2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="408e2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="408e2-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="408e2-115">The call timed out.</span></span>|  
|<span data-ttu-id="408e2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="408e2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="408e2-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="408e2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="408e2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="408e2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="408e2-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="408e2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="408e2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="408e2-120">E_FAIL</span></span>|<span data-ttu-id="408e2-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="408e2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="408e2-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="408e2-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="408e2-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="408e2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="408e2-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="408e2-124">Remarks</span></span>  
 <span data-ttu-id="408e2-125">CLR vypočítá a vrátí pouze ty statistiky, které jsou určeny `Flags` polem `pStats` .</span><span class="sxs-lookup"><span data-stu-id="408e2-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="408e2-126">Nastavte `Flags` pole na jednu nebo více hodnot výčtu [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) , aby se určilo, které statistiky ve [COR_GC_STATS](cor-gc-stats-structure.md) struktuře mají být nastavené.</span><span class="sxs-lookup"><span data-stu-id="408e2-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="408e2-127">Příklad použití je následující:</span><span class="sxs-lookup"><span data-stu-id="408e2-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="408e2-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="408e2-128">Requirements</span></span>  
 <span data-ttu-id="408e2-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="408e2-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408e2-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="408e2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="408e2-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="408e2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="408e2-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408e2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408e2-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="408e2-133">See also</span></span>

- [<span data-ttu-id="408e2-134">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="408e2-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="408e2-135">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="408e2-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="408e2-136">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="408e2-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="408e2-137">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="408e2-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="408e2-138">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="408e2-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="408e2-139">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="408e2-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="408e2-140">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="408e2-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="408e2-141">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="408e2-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="408e2-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="408e2-142">Hosting</span></span>](index.md)
