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
ms.openlocfilehash: f9d6c4f01b01944c885190f90e2195c3a308490a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141202"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="70cf9-102">ICLRGCManager::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="70cf9-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="70cf9-103">Nastaví velikost segmentu uvolňování paměti a maximální velikost generace 0 systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="70cf9-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="70cf9-104">Počínaje .NET Framework 4,5 můžete nastavit velikost segmentu a maximální velikost generace 0 na hodnoty větší než `DWORD` pomocí metody [ICLRGCManager2 –:: SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="70cf9-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cf9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70cf9-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70cf9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="70cf9-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="70cf9-107">pro Zadaná velikost segmentu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="70cf9-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="70cf9-108">Minimální velikost segmentu je 4 MB.</span><span class="sxs-lookup"><span data-stu-id="70cf9-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="70cf9-109">Segmenty lze zvýšit v přírůstcích po 1 MB nebo větší.</span><span class="sxs-lookup"><span data-stu-id="70cf9-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="70cf9-110">pro Zadaná maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="70cf9-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="70cf9-111">Minimální velikost 0. generace je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="70cf9-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70cf9-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70cf9-112">Return Value</span></span>  
  
|<span data-ttu-id="70cf9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70cf9-113">HRESULT</span></span>|<span data-ttu-id="70cf9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="70cf9-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70cf9-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="70cf9-115">S_OK</span></span>|<span data-ttu-id="70cf9-116">`SetGCStartupLimits` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="70cf9-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="70cf9-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70cf9-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70cf9-118">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="70cf9-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="70cf9-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70cf9-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70cf9-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="70cf9-120">The call timed out.</span></span>|  
|<span data-ttu-id="70cf9-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70cf9-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70cf9-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="70cf9-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70cf9-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70cf9-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70cf9-124">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="70cf9-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70cf9-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70cf9-125">E_FAIL</span></span>|<span data-ttu-id="70cf9-126">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="70cf9-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70cf9-127">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="70cf9-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70cf9-128">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="70cf9-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70cf9-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70cf9-129">Remarks</span></span>  
 <span data-ttu-id="70cf9-130">Hodnoty, které `SetGCStartupLimits` sady, lze zadat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="70cf9-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="70cf9-131">Pozdější volání `SetGCStartupLimits` jsou ignorována.</span><span class="sxs-lookup"><span data-stu-id="70cf9-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70cf9-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70cf9-132">Requirements</span></span>  
 <span data-ttu-id="70cf9-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70cf9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cf9-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="70cf9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70cf9-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="70cf9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70cf9-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70cf9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cf9-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70cf9-137">See also</span></span>

- [<span data-ttu-id="70cf9-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="70cf9-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="70cf9-139">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="70cf9-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="70cf9-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70cf9-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="70cf9-141">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70cf9-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
