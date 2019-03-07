---
title: ICLRGCManager::SetGCStartupLimits – metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3292fae0ca78615faee4cb5208aa711fea9a0a24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490005"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="cc687-102">ICLRGCManager::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="cc687-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="cc687-103">Nastaví velikost segmentu kolekce uvolnění paměti a maximální velikost systému kolekce uvolnění paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="cc687-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc687-104">Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete nastavit velikost segmentu a hodnoty větší než maximální generace 0 velikost `DWORD` pomocí [iclrgcmanager2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="cc687-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc687-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc687-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc687-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc687-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="cc687-107">[in] Zadaná velikost segmentu kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="cc687-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="cc687-108">Segment minimální velikost je 4 MB.</span><span class="sxs-lookup"><span data-stu-id="cc687-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="cc687-109">Segmenty může být větší nebo vyšší v krocích po 1 MB.</span><span class="sxs-lookup"><span data-stu-id="cc687-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="cc687-110">[in] Zadaná maximální velikost 0. generace.</span><span class="sxs-lookup"><span data-stu-id="cc687-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="cc687-111">Velikost minimální generace 0 je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="cc687-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc687-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc687-112">Return Value</span></span>  
  
|<span data-ttu-id="cc687-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc687-113">HRESULT</span></span>|<span data-ttu-id="cc687-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cc687-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc687-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc687-115">S_OK</span></span>|<span data-ttu-id="cc687-116">`SetGCStartupLimits` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="cc687-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="cc687-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc687-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc687-118">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cc687-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc687-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc687-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc687-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="cc687-120">The call timed out.</span></span>|  
|<span data-ttu-id="cc687-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc687-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc687-122">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="cc687-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc687-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc687-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc687-124">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="cc687-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc687-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc687-125">E_FAIL</span></span>|<span data-ttu-id="cc687-126">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="cc687-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc687-127">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="cc687-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc687-128">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc687-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc687-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc687-129">Remarks</span></span>  
 <span data-ttu-id="cc687-130">Hodnoty, které `SetGCStartupLimits` sady lze zadat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="cc687-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="cc687-131">Pozdější volání `SetGCStartupLimits` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="cc687-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc687-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc687-132">Requirements</span></span>  
 <span data-ttu-id="cc687-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc687-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc687-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc687-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc687-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc687-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc687-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc687-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc687-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc687-137">See also</span></span>
- [<span data-ttu-id="cc687-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="cc687-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="cc687-139">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="cc687-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="cc687-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc687-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="cc687-141">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc687-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
