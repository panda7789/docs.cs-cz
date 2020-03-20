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
ms.openlocfilehash: 9885149a71147db6eef13958b8ef825caa1d6ec6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176380"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="034a9-102">ICLRGCManager2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="034a9-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="034a9-103">Nastaví velikost segmentu uvolňování paměti a maximální velikost generování systému uvolňování paměti 0.</span><span class="sxs-lookup"><span data-stu-id="034a9-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="034a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="034a9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="034a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="034a9-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="034a9-106">[v] Zadaná velikost segmentu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="034a9-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="034a9-107">Minimální velikost segmentu je 4 MB.</span><span class="sxs-lookup"><span data-stu-id="034a9-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="034a9-108">Segmenty lze zvýšit v krocích po 1 MB nebo větší.</span><span class="sxs-lookup"><span data-stu-id="034a9-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="034a9-109">[v] Zadaná maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="034a9-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="034a9-110">Minimální velikost generace 0 je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="034a9-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="034a9-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="034a9-111">Return Value</span></span>  
  
|<span data-ttu-id="034a9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="034a9-112">HRESULT</span></span>|<span data-ttu-id="034a9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="034a9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="034a9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="034a9-114">S_OK</span></span>|<span data-ttu-id="034a9-115">`SetGCStartupLimitsEx`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="034a9-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="034a9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="034a9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="034a9-117">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="034a9-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="034a9-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="034a9-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="034a9-119">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="034a9-119">The call timed out.</span></span>|  
|<span data-ttu-id="034a9-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="034a9-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="034a9-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="034a9-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="034a9-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="034a9-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="034a9-123">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="034a9-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="034a9-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="034a9-124">E_FAIL</span></span>|<span data-ttu-id="034a9-125">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="034a9-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="034a9-126">Po metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="034a9-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="034a9-127">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="034a9-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="034a9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="034a9-128">Remarks</span></span>  
 <span data-ttu-id="034a9-129">Hodnoty, `SetGCStartupLimitsEx` které nastaví lze zadat pouze před spuštěním hostitele.</span><span class="sxs-lookup"><span data-stu-id="034a9-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="034a9-130">Pozdější volání `SetGCStartupLimitsEx` do jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="034a9-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="034a9-131">Chcete-li nastavit buď parametr bez ovlivnění druhého, zadejte 0 (nula) pro parametr, který nechcete změnit.</span><span class="sxs-lookup"><span data-stu-id="034a9-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="034a9-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="034a9-132">Requirements</span></span>  
 <span data-ttu-id="034a9-133">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="034a9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="034a9-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="034a9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="034a9-135">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="034a9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="034a9-136">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="034a9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="034a9-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="034a9-137">See also</span></span>

- [<span data-ttu-id="034a9-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="034a9-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="034a9-139">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="034a9-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="034a9-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="034a9-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="034a9-141">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="034a9-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
