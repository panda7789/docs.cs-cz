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
ms.openlocfilehash: 3064a5793c6158ead85a9ff6d9b09f077d0bd603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966242"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="6efcd-102">ICLRGCManager::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="6efcd-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="6efcd-103">Vynutí uvolňování paměti pro určenou generaci.</span><span class="sxs-lookup"><span data-stu-id="6efcd-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6efcd-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6efcd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6efcd-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="6efcd-106">pro Generace, která se má shromáždit</span><span class="sxs-lookup"><span data-stu-id="6efcd-106">[in] The generation to collect.</span></span> <span data-ttu-id="6efcd-107">Hodnota-1 vynutí kolekci všech generací.</span><span class="sxs-lookup"><span data-stu-id="6efcd-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6efcd-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6efcd-108">Return Value</span></span>  
  
|<span data-ttu-id="6efcd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6efcd-109">HRESULT</span></span>|<span data-ttu-id="6efcd-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6efcd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6efcd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6efcd-111">S_OK</span></span>|<span data-ttu-id="6efcd-112">`Collect`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6efcd-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="6efcd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6efcd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6efcd-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6efcd-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6efcd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6efcd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6efcd-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6efcd-116">The call timed out.</span></span>|  
|<span data-ttu-id="6efcd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6efcd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6efcd-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6efcd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6efcd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6efcd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6efcd-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6efcd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6efcd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6efcd-121">E_FAIL</span></span>|<span data-ttu-id="6efcd-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6efcd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6efcd-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6efcd-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6efcd-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6efcd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6efcd-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6efcd-125">Remarks</span></span>  
 <span data-ttu-id="6efcd-126">`Collect` Metoda vynutí, aby systém uvolňování paměti CLR prováděl shromažďování bez ohledu na jeho aktuální stav.</span><span class="sxs-lookup"><span data-stu-id="6efcd-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6efcd-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6efcd-127">Requirements</span></span>  
 <span data-ttu-id="6efcd-128">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6efcd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6efcd-129">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6efcd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6efcd-130">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6efcd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6efcd-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6efcd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efcd-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6efcd-132">See also</span></span>

- [<span data-ttu-id="6efcd-133">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="6efcd-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="6efcd-134">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="6efcd-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="6efcd-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6efcd-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6efcd-136">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6efcd-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="6efcd-137">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6efcd-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="6efcd-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6efcd-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6efcd-139">Hostování</span><span class="sxs-lookup"><span data-stu-id="6efcd-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
