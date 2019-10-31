---
title: IHostManualEvent::Reset – metoda
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 464093291648d7c5c1f2001fbaef85fcd5d592de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136806"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="639b7-102">IHostManualEvent::Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="639b7-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="639b7-103">Obnoví aktuální instanci [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) na stav bez signálu.</span><span class="sxs-lookup"><span data-stu-id="639b7-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="639b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="639b7-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="639b7-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="639b7-105">Return Value</span></span>  
  
|<span data-ttu-id="639b7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="639b7-106">HRESULT</span></span>|<span data-ttu-id="639b7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="639b7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="639b7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="639b7-108">S_OK</span></span>|<span data-ttu-id="639b7-109">`Reset` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="639b7-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="639b7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="639b7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="639b7-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="639b7-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="639b7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="639b7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="639b7-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="639b7-113">The call timed out.</span></span>|  
|<span data-ttu-id="639b7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="639b7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="639b7-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="639b7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="639b7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="639b7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="639b7-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="639b7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="639b7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="639b7-118">E_FAIL</span></span>|<span data-ttu-id="639b7-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="639b7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="639b7-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="639b7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="639b7-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="639b7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="639b7-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="639b7-122">Requirements</span></span>  
 <span data-ttu-id="639b7-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="639b7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="639b7-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="639b7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="639b7-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="639b7-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="639b7-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="639b7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639b7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="639b7-127">See also</span></span>

- [<span data-ttu-id="639b7-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="639b7-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="639b7-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="639b7-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="639b7-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="639b7-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="639b7-131">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="639b7-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="639b7-132">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="639b7-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
