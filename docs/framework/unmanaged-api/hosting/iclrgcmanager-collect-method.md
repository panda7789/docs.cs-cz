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
ms.openlocfilehash: a7dae98d1f2dc2448bd3a5df2d6143b7be0bb734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129262"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="bb4c9-102">ICLRGCManager::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="bb4c9-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="bb4c9-103">Vynutí uvolňování paměti pro určenou generaci.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb4c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb4c9-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb4c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb4c9-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="bb4c9-106">pro Generace, která se má shromáždit</span><span class="sxs-lookup"><span data-stu-id="bb4c9-106">[in] The generation to collect.</span></span> <span data-ttu-id="bb4c9-107">Hodnota-1 vynutí kolekci všech generací.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb4c9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bb4c9-108">Return Value</span></span>  
  
|<span data-ttu-id="bb4c9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb4c9-109">HRESULT</span></span>|<span data-ttu-id="bb4c9-110">Popis</span><span class="sxs-lookup"><span data-stu-id="bb4c9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb4c9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb4c9-111">S_OK</span></span>|<span data-ttu-id="bb4c9-112">`Collect` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="bb4c9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb4c9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb4c9-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb4c9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb4c9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb4c9-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-116">The call timed out.</span></span>|  
|<span data-ttu-id="bb4c9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb4c9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb4c9-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb4c9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb4c9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb4c9-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb4c9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb4c9-121">E_FAIL</span></span>|<span data-ttu-id="bb4c9-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb4c9-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb4c9-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb4c9-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb4c9-125">Remarks</span></span>  
 <span data-ttu-id="bb4c9-126">Metoda `Collect` vynutí, aby systém uvolňování paměti CLR prováděl shromažďování bez ohledu na jeho aktuální stav.</span><span class="sxs-lookup"><span data-stu-id="bb4c9-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb4c9-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb4c9-127">Requirements</span></span>  
 <span data-ttu-id="bb4c9-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb4c9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb4c9-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bb4c9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb4c9-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bb4c9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb4c9-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb4c9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb4c9-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb4c9-132">See also</span></span>

- [<span data-ttu-id="bb4c9-133">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="bb4c9-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="bb4c9-134">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="bb4c9-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="bb4c9-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb4c9-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="bb4c9-136">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb4c9-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="bb4c9-137">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="bb4c9-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="bb4c9-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="bb4c9-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="bb4c9-139">Hostování</span><span class="sxs-lookup"><span data-stu-id="bb4c9-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
