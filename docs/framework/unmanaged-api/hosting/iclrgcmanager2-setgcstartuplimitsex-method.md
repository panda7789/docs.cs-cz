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
ms.openlocfilehash: 0d881c71d4725e1a73d743aa098aecc053182947
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918611"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="96b0e-102">ICLRGCManager2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="96b0e-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="96b0e-103">Nastaví velikost segmentu uvolňování paměti a maximální velikost generace 0 systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="96b0e-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96b0e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96b0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96b0e-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="96b0e-106">pro Zadaná velikost segmentu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="96b0e-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="96b0e-107">Minimální velikost segmentu je 4 MB.</span><span class="sxs-lookup"><span data-stu-id="96b0e-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="96b0e-108">Segmenty lze zvýšit v přírůstcích po 1 MB nebo větší.</span><span class="sxs-lookup"><span data-stu-id="96b0e-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="96b0e-109">pro Zadaná maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="96b0e-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="96b0e-110">Minimální velikost 0. generace je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="96b0e-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96b0e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96b0e-111">Return Value</span></span>  
  
|<span data-ttu-id="96b0e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96b0e-112">HRESULT</span></span>|<span data-ttu-id="96b0e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="96b0e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96b0e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="96b0e-114">S_OK</span></span>|<span data-ttu-id="96b0e-115">`SetGCStartupLimitsEx`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="96b0e-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="96b0e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="96b0e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="96b0e-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="96b0e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="96b0e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="96b0e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="96b0e-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="96b0e-119">The call timed out.</span></span>|  
|<span data-ttu-id="96b0e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="96b0e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="96b0e-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="96b0e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="96b0e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="96b0e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="96b0e-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="96b0e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="96b0e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="96b0e-124">E_FAIL</span></span>|<span data-ttu-id="96b0e-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="96b0e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="96b0e-126">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="96b0e-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="96b0e-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="96b0e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96b0e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96b0e-128">Remarks</span></span>  
 <span data-ttu-id="96b0e-129">Hodnoty, které `SetGCStartupLimitsEx` nastavíte, lze zadat pouze před spuštěním hostitele.</span><span class="sxs-lookup"><span data-stu-id="96b0e-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="96b0e-130">Pozdější volání do `SetGCStartupLimitsEx` jsou ignorována.</span><span class="sxs-lookup"><span data-stu-id="96b0e-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="96b0e-131">Chcete-li nastavit parametr bez vlivu na druhý, zadejte 0 (nula) pro parametr, který nechcete změnit.</span><span class="sxs-lookup"><span data-stu-id="96b0e-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b0e-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96b0e-132">Requirements</span></span>  
 <span data-ttu-id="96b0e-133">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b0e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b0e-134">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="96b0e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96b0e-135">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="96b0e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96b0e-136">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b0e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b0e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96b0e-137">See also</span></span>

- [<span data-ttu-id="96b0e-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="96b0e-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="96b0e-139">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="96b0e-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="96b0e-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96b0e-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="96b0e-141">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96b0e-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
