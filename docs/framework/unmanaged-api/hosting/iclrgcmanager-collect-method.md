---
title: ICLRGCManager::Collect – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b448892a58dd120fd0f30f2b61be59e579b629a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651406"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="660c7-102">ICLRGCManager::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="660c7-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="660c7-103">Vynutí uvolnění pro zadané generace.</span><span class="sxs-lookup"><span data-stu-id="660c7-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="660c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="660c7-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="660c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="660c7-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="660c7-106">[in] Generování, shromažďování.</span><span class="sxs-lookup"><span data-stu-id="660c7-106">[in] The generation to collect.</span></span> <span data-ttu-id="660c7-107">Hodnota -1 vynutí kolekce všech generací.</span><span class="sxs-lookup"><span data-stu-id="660c7-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="660c7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="660c7-108">Return Value</span></span>  
  
|<span data-ttu-id="660c7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="660c7-109">HRESULT</span></span>|<span data-ttu-id="660c7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="660c7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="660c7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="660c7-111">S_OK</span></span>|<span data-ttu-id="660c7-112">`Collect` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="660c7-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="660c7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="660c7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="660c7-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="660c7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="660c7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="660c7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="660c7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="660c7-116">The call timed out.</span></span>|  
|<span data-ttu-id="660c7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="660c7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="660c7-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="660c7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="660c7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="660c7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="660c7-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="660c7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="660c7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="660c7-121">E_FAIL</span></span>|<span data-ttu-id="660c7-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="660c7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="660c7-123">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="660c7-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="660c7-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="660c7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="660c7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="660c7-125">Remarks</span></span>  
 <span data-ttu-id="660c7-126">`Collect` Metoda donutí modulu CLR systému uvolňování paměti k provedení uvolnění bez ohledu na její aktuální stav.</span><span class="sxs-lookup"><span data-stu-id="660c7-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="660c7-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="660c7-127">Requirements</span></span>  
 <span data-ttu-id="660c7-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="660c7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="660c7-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="660c7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="660c7-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="660c7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="660c7-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="660c7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="660c7-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="660c7-132">See also</span></span>
- [<span data-ttu-id="660c7-133">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="660c7-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="660c7-134">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="660c7-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="660c7-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="660c7-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="660c7-136">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="660c7-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="660c7-137">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="660c7-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="660c7-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="660c7-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="660c7-139">Hostování</span><span class="sxs-lookup"><span data-stu-id="660c7-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
