---
title: IHostAutoEvent::Set – metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: 792b735522580eb7460da703899a00781e525419
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124449"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="63cd3-102">IHostAutoEvent::Set – metoda</span><span class="sxs-lookup"><span data-stu-id="63cd3-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="63cd3-103">Nastaví aktuální instanci [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) na signálový stav.</span><span class="sxs-lookup"><span data-stu-id="63cd3-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63cd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63cd3-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="63cd3-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="63cd3-105">Return Value</span></span>  
  
|<span data-ttu-id="63cd3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63cd3-106">HRESULT</span></span>|<span data-ttu-id="63cd3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="63cd3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63cd3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="63cd3-108">S_OK</span></span>|<span data-ttu-id="63cd3-109">`Set` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="63cd3-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="63cd3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="63cd3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="63cd3-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="63cd3-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="63cd3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="63cd3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="63cd3-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="63cd3-113">The call timed out.</span></span>|  
|<span data-ttu-id="63cd3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="63cd3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="63cd3-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="63cd3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="63cd3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="63cd3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="63cd3-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="63cd3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="63cd3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63cd3-118">E_FAIL</span></span>|<span data-ttu-id="63cd3-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="63cd3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63cd3-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="63cd3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="63cd3-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="63cd3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63cd3-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63cd3-122">Requirements</span></span>  
 <span data-ttu-id="63cd3-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63cd3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63cd3-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63cd3-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63cd3-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63cd3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63cd3-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63cd3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63cd3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63cd3-127">See also</span></span>

- [<span data-ttu-id="63cd3-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63cd3-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="63cd3-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63cd3-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="63cd3-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63cd3-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="63cd3-131">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63cd3-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
