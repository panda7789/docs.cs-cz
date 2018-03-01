---
title: "ICLRGCManager::Collect – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e2fdb66008a6bbe315f39a0d3fae293219d6b6c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="6efb1-102">ICLRGCManager::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="6efb1-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="6efb1-103">Vynutí uvolnění paměti pro zadané generaci.</span><span class="sxs-lookup"><span data-stu-id="6efb1-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6efb1-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6efb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6efb1-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="6efb1-106">[v] Generování ke shromažďování.</span><span class="sxs-lookup"><span data-stu-id="6efb1-106">[in] The generation to collect.</span></span> <span data-ttu-id="6efb1-107">Hodnota -1 vynutí kolekci všech generací.</span><span class="sxs-lookup"><span data-stu-id="6efb1-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6efb1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6efb1-108">Return Value</span></span>  
  
|<span data-ttu-id="6efb1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6efb1-109">HRESULT</span></span>|<span data-ttu-id="6efb1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6efb1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6efb1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6efb1-111">S_OK</span></span>|<span data-ttu-id="6efb1-112">`Collect`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6efb1-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="6efb1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6efb1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6efb1-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6efb1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6efb1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6efb1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6efb1-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6efb1-116">The call timed out.</span></span>|  
|<span data-ttu-id="6efb1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6efb1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6efb1-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="6efb1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6efb1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6efb1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6efb1-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="6efb1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6efb1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6efb1-121">E_FAIL</span></span>|<span data-ttu-id="6efb1-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="6efb1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6efb1-123">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6efb1-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6efb1-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6efb1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6efb1-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6efb1-125">Remarks</span></span>  
 <span data-ttu-id="6efb1-126">`Collect` Metoda vynutí CLR pro uvolňování paměti k provedení kolekce bez ohledu na jeho aktuální stav.</span><span class="sxs-lookup"><span data-stu-id="6efb1-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6efb1-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6efb1-127">Requirements</span></span>  
 <span data-ttu-id="6efb1-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6efb1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6efb1-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6efb1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6efb1-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6efb1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6efb1-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6efb1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efb1-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="6efb1-132">See Also</span></span>  
 [<span data-ttu-id="6efb1-133">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="6efb1-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="6efb1-134">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="6efb1-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="6efb1-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6efb1-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="6efb1-136">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6efb1-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="6efb1-137">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6efb1-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="6efb1-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6efb1-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="6efb1-139">Hostování</span><span class="sxs-lookup"><span data-stu-id="6efb1-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
