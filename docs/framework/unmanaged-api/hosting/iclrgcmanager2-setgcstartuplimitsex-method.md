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
ms.openlocfilehash: 77de550cd3fb614e03f8028707c3cbf914734910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141085"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="3d9bd-102">ICLRGCManager2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="3d9bd-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="3d9bd-103">Nastaví velikost segmentu uvolňování paměti a maximální velikost generace 0 systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d9bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d9bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d9bd-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="3d9bd-106">pro Zadaná velikost segmentu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="3d9bd-107">Minimální velikost segmentu je 4 MB.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="3d9bd-108">Segmenty lze zvýšit v přírůstcích po 1 MB nebo větší.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="3d9bd-109">pro Zadaná maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="3d9bd-110">Minimální velikost 0. generace je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d9bd-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3d9bd-111">Return Value</span></span>  
  
|<span data-ttu-id="3d9bd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d9bd-112">HRESULT</span></span>|<span data-ttu-id="3d9bd-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3d9bd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d9bd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d9bd-114">S_OK</span></span>|<span data-ttu-id="3d9bd-115">`SetGCStartupLimitsEx` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="3d9bd-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d9bd-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d9bd-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d9bd-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d9bd-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d9bd-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-119">The call timed out.</span></span>|  
|<span data-ttu-id="3d9bd-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d9bd-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d9bd-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d9bd-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d9bd-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d9bd-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d9bd-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d9bd-124">E_FAIL</span></span>|<span data-ttu-id="3d9bd-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d9bd-126">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d9bd-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d9bd-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d9bd-128">Remarks</span></span>  
 <span data-ttu-id="3d9bd-129">Hodnoty, které `SetGCStartupLimitsEx` sady lze zadat pouze před spuštěním hostitele.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="3d9bd-130">Pozdější volání `SetGCStartupLimitsEx` jsou ignorována.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="3d9bd-131">Chcete-li nastavit parametr bez vlivu na druhý, zadejte 0 (nula) pro parametr, který nechcete změnit.</span><span class="sxs-lookup"><span data-stu-id="3d9bd-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d9bd-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d9bd-132">Requirements</span></span>  
 <span data-ttu-id="3d9bd-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d9bd-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d9bd-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3d9bd-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d9bd-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3d9bd-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d9bd-136">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d9bd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9bd-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d9bd-137">See also</span></span>

- [<span data-ttu-id="3d9bd-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="3d9bd-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="3d9bd-139">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="3d9bd-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="3d9bd-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d9bd-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3d9bd-141">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d9bd-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
