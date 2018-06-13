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
ms.openlocfilehash: 96673049d37034781dff9f206db86a1d5d953d52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436397"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="c1073-102">ICLRGCManager::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="c1073-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="c1073-103">Získá sadu aktuální statistické údaje o systém kolekce paměti modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c1073-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1073-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1073-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1073-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1073-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="c1073-106">[ve out] A [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance, která obsahuje požadovanou statistiku.</span><span class="sxs-lookup"><span data-stu-id="c1073-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1073-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1073-107">Return Value</span></span>  
  
|<span data-ttu-id="c1073-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1073-108">HRESULT</span></span>|<span data-ttu-id="c1073-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c1073-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1073-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1073-110">S_OK</span></span>|<span data-ttu-id="c1073-111">`GetStats` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c1073-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="c1073-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1073-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1073-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c1073-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1073-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1073-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1073-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c1073-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1073-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1073-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1073-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c1073-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1073-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1073-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1073-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c1073-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1073-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1073-120">E_FAIL</span></span>|<span data-ttu-id="c1073-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c1073-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1073-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c1073-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1073-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c1073-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1073-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1073-124">Remarks</span></span>  
 <span data-ttu-id="c1073-125">Modul CLR vypočítá a vrátí pouze statistiky, které jsou určené `Flags` pole z `pStats`.</span><span class="sxs-lookup"><span data-stu-id="c1073-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="c1073-126">Nastavit `Flags` pole na jeden nebo více hodnot [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) výčtu k určete, které statistiky v [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura mají být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="c1073-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="c1073-127">Příklad použití je následující:</span><span class="sxs-lookup"><span data-stu-id="c1073-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c1073-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1073-128">Requirements</span></span>  
 <span data-ttu-id="c1073-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1073-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1073-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1073-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1073-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1073-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1073-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1073-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1073-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1073-133">See Also</span></span>  
 [<span data-ttu-id="c1073-134">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="c1073-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="c1073-135">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="c1073-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="c1073-136">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="c1073-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="c1073-137">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="c1073-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="c1073-138">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1073-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c1073-139">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1073-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="c1073-140">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="c1073-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="c1073-141">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c1073-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c1073-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="c1073-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
