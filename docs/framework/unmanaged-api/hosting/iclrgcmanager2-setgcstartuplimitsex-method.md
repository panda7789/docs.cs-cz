---
title: "ICLRGCManager2::SetGCStartupLimitsEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2.SetGCStartupLimitsEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73f5678008354b312964f0cb32d768d36a641fd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="fbcc6-102">ICLRGCManager2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="fbcc6-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="fbcc6-103">Nastaví velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbcc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbcc6-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbcc6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbcc6-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="fbcc6-106">[v] Zadaná velikost paměti segment kolekce.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="fbcc6-107">Velikost minimální segmentu je 4 MB volného místa.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="fbcc6-108">Segmenty může být vyšší v přírůstcích po 1 MB nebo větší.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="fbcc6-109">[v] Zadaná maximální velikost pro generování 0.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="fbcc6-110">Velikost minimální generace 0 je 64 KB.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbcc6-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fbcc6-111">Return Value</span></span>  
  
|<span data-ttu-id="fbcc6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbcc6-112">HRESULT</span></span>|<span data-ttu-id="fbcc6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fbcc6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbcc6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbcc6-114">S_OK</span></span>|<span data-ttu-id="fbcc6-115">`SetGCStartupLimitsEx`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="fbcc6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fbcc6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fbcc6-117">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fbcc6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fbcc6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fbcc6-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-119">The call timed out.</span></span>|  
|<span data-ttu-id="fbcc6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fbcc6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fbcc6-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fbcc6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fbcc6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fbcc6-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fbcc6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbcc6-124">E_FAIL</span></span>|<span data-ttu-id="fbcc6-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fbcc6-126">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fbcc6-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbcc6-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbcc6-128">Remarks</span></span>  
 <span data-ttu-id="fbcc6-129">Hodnoty, `SetGCStartupLimitsEx` sady lze zadat pouze, před zahájením hostitele.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="fbcc6-130">Novější volá, aby se `SetGCStartupLimitsEx` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="fbcc6-131">Nastavit buď parametr bez ovlivnění dalších, zadejte 0 (nula) pro parametr, které nechcete změnit.</span><span class="sxs-lookup"><span data-stu-id="fbcc6-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbcc6-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbcc6-132">Requirements</span></span>  
 <span data-ttu-id="fbcc6-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbcc6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbcc6-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbcc6-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbcc6-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbcc6-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbcc6-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbcc6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcc6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbcc6-137">See Also</span></span>  
 [<span data-ttu-id="fbcc6-138">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="fbcc6-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="fbcc6-139">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="fbcc6-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="fbcc6-140">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbcc6-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="fbcc6-141">Iclrgcmanager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbcc6-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
