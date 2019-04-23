---
title: ICLRGCManager2::SetGCStartupLimitsEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cba7b4a34835eb2f394aa71be8b907973cb1cd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204715"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="ebf30-102">ICLRGCManager2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ebf30-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="ebf30-103">Nastaví velikost segmentu kolekce uvolnění paměti a maximální velikost systému kolekce uvolnění paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="ebf30-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebf30-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebf30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebf30-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="ebf30-106">[in] Zadaná velikost segmentu kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ebf30-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="ebf30-107">Segment minimální velikost je 4 MB.</span><span class="sxs-lookup"><span data-stu-id="ebf30-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="ebf30-108">Segmenty může být větší nebo vyšší v krocích po 1 MB.</span><span class="sxs-lookup"><span data-stu-id="ebf30-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="ebf30-109">[in] Zadaná maximální velikost 0. generace.</span><span class="sxs-lookup"><span data-stu-id="ebf30-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="ebf30-110">Velikost minimální generace 0 je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="ebf30-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebf30-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ebf30-111">Return Value</span></span>  
  
|<span data-ttu-id="ebf30-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ebf30-112">HRESULT</span></span>|<span data-ttu-id="ebf30-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ebf30-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ebf30-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ebf30-114">S_OK</span></span>|<span data-ttu-id="ebf30-115">`SetGCStartupLimitsEx` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ebf30-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="ebf30-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ebf30-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ebf30-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ebf30-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ebf30-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ebf30-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ebf30-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ebf30-119">The call timed out.</span></span>|  
|<span data-ttu-id="ebf30-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ebf30-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ebf30-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="ebf30-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ebf30-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ebf30-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ebf30-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="ebf30-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ebf30-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ebf30-124">E_FAIL</span></span>|<span data-ttu-id="ebf30-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="ebf30-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ebf30-126">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ebf30-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ebf30-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ebf30-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebf30-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ebf30-128">Remarks</span></span>  
 <span data-ttu-id="ebf30-129">Hodnoty, které `SetGCStartupLimitsEx` sady se dá nastavit pouze před spuštěním hostitele.</span><span class="sxs-lookup"><span data-stu-id="ebf30-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="ebf30-130">Pozdější volání `SetGCStartupLimitsEx` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="ebf30-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="ebf30-131">Pokud chcete nastavit buď parametr bez vlivu jiné, zadejte 0 (nula) pro parametr, který nechcete změnit.</span><span class="sxs-lookup"><span data-stu-id="ebf30-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf30-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebf30-132">Requirements</span></span>  
 <span data-ttu-id="ebf30-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf30-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf30-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebf30-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebf30-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebf30-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebf30-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf30-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf30-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebf30-137">See also</span></span>

- [<span data-ttu-id="ebf30-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="ebf30-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="ebf30-139">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="ebf30-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="ebf30-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebf30-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ebf30-141">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebf30-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
