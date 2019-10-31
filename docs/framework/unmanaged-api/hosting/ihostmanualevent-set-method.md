---
title: IHostManualEvent::Set – metoda
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: 1114fc744ac1811585f2c5a94858b75eda00815c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136762"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="9cef9-102">IHostManualEvent::Set – metoda</span><span class="sxs-lookup"><span data-stu-id="9cef9-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="9cef9-103">Nastaví aktuální instanci [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) na signálový stav.</span><span class="sxs-lookup"><span data-stu-id="9cef9-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cef9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cef9-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9cef9-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9cef9-105">Return Value</span></span>  
  
|<span data-ttu-id="9cef9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cef9-106">HRESULT</span></span>|<span data-ttu-id="9cef9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9cef9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cef9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cef9-108">S_OK</span></span>|<span data-ttu-id="9cef9-109">`Set` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9cef9-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="9cef9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9cef9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9cef9-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9cef9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9cef9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9cef9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9cef9-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9cef9-113">The call timed out.</span></span>|  
|<span data-ttu-id="9cef9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9cef9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9cef9-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="9cef9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9cef9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9cef9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9cef9-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="9cef9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9cef9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9cef9-118">E_FAIL</span></span>|<span data-ttu-id="9cef9-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="9cef9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9cef9-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="9cef9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9cef9-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9cef9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cef9-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cef9-122">Requirements</span></span>  
 <span data-ttu-id="9cef9-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cef9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cef9-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9cef9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cef9-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9cef9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cef9-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cef9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cef9-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cef9-127">See also</span></span>

- [<span data-ttu-id="9cef9-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cef9-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9cef9-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cef9-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="9cef9-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cef9-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="9cef9-131">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cef9-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="9cef9-132">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cef9-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
