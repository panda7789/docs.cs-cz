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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9300f67e75d40f041a4fba52f6742741ec9f91de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187324"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="82277-102">ICLRGCManager::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="82277-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="82277-103">Získá sadu aktuální statistické údaje o systému kolekce uvolnění paměti modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="82277-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82277-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82277-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82277-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82277-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="82277-106">[out v] A [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance, která obsahuje požadovaná statistiky.</span><span class="sxs-lookup"><span data-stu-id="82277-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82277-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="82277-107">Return Value</span></span>  
  
|<span data-ttu-id="82277-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82277-108">HRESULT</span></span>|<span data-ttu-id="82277-109">Popis</span><span class="sxs-lookup"><span data-stu-id="82277-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82277-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="82277-110">S_OK</span></span>|<span data-ttu-id="82277-111">`GetStats` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="82277-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="82277-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82277-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82277-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="82277-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82277-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82277-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82277-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="82277-115">The call timed out.</span></span>|  
|<span data-ttu-id="82277-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82277-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82277-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="82277-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82277-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82277-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82277-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="82277-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82277-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82277-120">E_FAIL</span></span>|<span data-ttu-id="82277-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="82277-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82277-122">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="82277-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82277-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="82277-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82277-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82277-124">Remarks</span></span>  
 <span data-ttu-id="82277-125">Modul CLR vypočítá a vrátí pouze statistiky, které jsou určeny `Flags` pole `pStats`.</span><span class="sxs-lookup"><span data-stu-id="82277-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="82277-126">Nastavte `Flags` pole do jednoho nebo více hodnot [cor_gc_stat_types –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) výčet určete, které statistiky v [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury mají být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="82277-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="82277-127">Příklad použití je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="82277-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="82277-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82277-128">Requirements</span></span>  
 <span data-ttu-id="82277-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82277-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82277-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82277-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82277-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82277-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82277-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82277-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82277-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82277-133">See also</span></span>

- [<span data-ttu-id="82277-134">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="82277-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="82277-135">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="82277-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="82277-136">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="82277-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="82277-137">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="82277-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="82277-138">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82277-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="82277-139">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82277-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="82277-140">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="82277-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="82277-141">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="82277-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="82277-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="82277-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
