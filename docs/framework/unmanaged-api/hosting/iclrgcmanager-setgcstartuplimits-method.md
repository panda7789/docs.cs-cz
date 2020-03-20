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
ms.openlocfilehash: 645b64c8b536029663c350bdcde9a716a715aab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178086"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="438b6-102">ICLRGCManager::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="438b6-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="438b6-103">Nastaví velikost segmentu uvolňování paměti a maximální velikost generování systému uvolňování paměti 0.</span><span class="sxs-lookup"><span data-stu-id="438b6-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="438b6-104">Počínaje rozhraním .NET Framework 4.5 můžete nastavit velikost segmentu a `DWORD` maximální velikost generace 0 na hodnoty větší než pomocí metody [ICLRGCManager2::SetGCStartupLimitsEx.](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)</span><span class="sxs-lookup"><span data-stu-id="438b6-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438b6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="438b6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="438b6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="438b6-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="438b6-107">[v] Zadaná velikost segmentu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="438b6-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="438b6-108">Minimální velikost segmentu je 4 MB.</span><span class="sxs-lookup"><span data-stu-id="438b6-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="438b6-109">Segmenty lze zvýšit v krocích po 1 MB nebo větší.</span><span class="sxs-lookup"><span data-stu-id="438b6-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="438b6-110">[v] Zadaná maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="438b6-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="438b6-111">Minimální velikost generace 0 je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="438b6-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="438b6-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="438b6-112">Return Value</span></span>  
  
|<span data-ttu-id="438b6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="438b6-113">HRESULT</span></span>|<span data-ttu-id="438b6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="438b6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="438b6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="438b6-115">S_OK</span></span>|<span data-ttu-id="438b6-116">`SetGCStartupLimits`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="438b6-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="438b6-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="438b6-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="438b6-118">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="438b6-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="438b6-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="438b6-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="438b6-120">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="438b6-120">The call timed out.</span></span>|  
|<span data-ttu-id="438b6-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="438b6-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="438b6-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="438b6-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="438b6-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="438b6-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="438b6-124">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="438b6-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="438b6-125">E_fail</span><span class="sxs-lookup"><span data-stu-id="438b6-125">E_FAIL</span></span>|<span data-ttu-id="438b6-126">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="438b6-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="438b6-127">Po metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="438b6-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="438b6-128">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="438b6-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="438b6-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="438b6-129">Remarks</span></span>  
 <span data-ttu-id="438b6-130">Hodnoty, `SetGCStartupLimits` které nastaví lze zadat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="438b6-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="438b6-131">Pozdější volání `SetGCStartupLimits` do jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="438b6-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="438b6-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="438b6-132">Requirements</span></span>  
 <span data-ttu-id="438b6-133">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="438b6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="438b6-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="438b6-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="438b6-135">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="438b6-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="438b6-136">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="438b6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438b6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="438b6-137">See also</span></span>

- [<span data-ttu-id="438b6-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="438b6-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="438b6-139">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="438b6-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="438b6-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="438b6-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="438b6-141">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="438b6-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
