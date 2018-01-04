---
title: "ICLRGCManager::SetGCStartupLimits – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fd5a1135866b75ea1d11fc5a14289104edfeac4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="90825-102">ICLRGCManager::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="90825-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="90825-103">Nastaví velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="90825-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90825-104">Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete nastavit velikost segmentu a hodnoty větší než maximální generace 0 velikost tak, aby `DWORD` pomocí [iclrgcmanager2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="90825-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90825-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90825-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90825-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="90825-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="90825-107">[v] Zadaná velikost paměti segment kolekce.</span><span class="sxs-lookup"><span data-stu-id="90825-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="90825-108">Velikost minimální segmentu je 4 MB volného místa.</span><span class="sxs-lookup"><span data-stu-id="90825-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="90825-109">Segmenty může být vyšší v přírůstcích po 1 MB nebo větší.</span><span class="sxs-lookup"><span data-stu-id="90825-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="90825-110">[v] Zadaná maximální velikost pro generování 0.</span><span class="sxs-lookup"><span data-stu-id="90825-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="90825-111">Velikost minimální generace 0 je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="90825-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90825-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90825-112">Return Value</span></span>  
  
|<span data-ttu-id="90825-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90825-113">HRESULT</span></span>|<span data-ttu-id="90825-114">Popis</span><span class="sxs-lookup"><span data-stu-id="90825-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90825-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="90825-115">S_OK</span></span>|<span data-ttu-id="90825-116">`SetGCStartupLimits`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="90825-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="90825-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="90825-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="90825-118">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="90825-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="90825-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="90825-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="90825-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="90825-120">The call timed out.</span></span>|  
|<span data-ttu-id="90825-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="90825-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="90825-122">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="90825-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="90825-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="90825-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="90825-124">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="90825-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="90825-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="90825-125">E_FAIL</span></span>|<span data-ttu-id="90825-126">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="90825-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="90825-127">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="90825-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="90825-128">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="90825-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90825-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90825-129">Remarks</span></span>  
 <span data-ttu-id="90825-130">Hodnoty, `SetGCStartupLimits` sady lze zadat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="90825-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="90825-131">Novější volá, aby se `SetGCStartupLimits` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="90825-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90825-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90825-132">Requirements</span></span>  
 <span data-ttu-id="90825-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90825-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90825-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90825-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90825-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90825-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90825-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90825-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90825-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="90825-137">See Also</span></span>  
 [<span data-ttu-id="90825-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="90825-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="90825-139">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="90825-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="90825-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90825-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="90825-141">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90825-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
