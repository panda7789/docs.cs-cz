---
title: IHostTaskManager::ReverseEnterRuntime – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e5beabb5ac1b5a4b2a34ae8e18b7fad7c86504
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959056"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="66820-102">IHostTaskManager::ReverseEnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="66820-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="66820-103">Upozorňuje hostitele, že je provedeno volání modulu CLR (Common Language Runtime) z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="66820-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66820-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66820-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="66820-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66820-105">Return Value</span></span>  
  
|<span data-ttu-id="66820-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66820-106">HRESULT</span></span>|<span data-ttu-id="66820-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66820-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66820-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="66820-108">S_OK</span></span>|<span data-ttu-id="66820-109">`ReverseEnterRuntime`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="66820-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="66820-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66820-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66820-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="66820-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="66820-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66820-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66820-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="66820-113">The call timed out.</span></span>|  
|<span data-ttu-id="66820-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66820-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66820-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="66820-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66820-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66820-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66820-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="66820-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66820-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="66820-118">E_FAIL</span></span>|<span data-ttu-id="66820-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="66820-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66820-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="66820-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66820-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="66820-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="66820-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="66820-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="66820-123">K dokončení požadovaného přidělení prostředků není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="66820-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66820-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66820-124">Remarks</span></span>  
 <span data-ttu-id="66820-125">Pokud je volání do CLR provedeno z sekvence, která byla vytvořena ve spravovaném kódu, každé volání `ReverseEnterRuntime` odpovídá volání [ReverseLeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="66820-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66820-126">Volání můžou pocházet z nespravovaného kódu bez vnoření.</span><span class="sxs-lookup"><span data-stu-id="66820-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="66820-127">V tomto případě neexistuje žádné volání [EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) `ReverseLeaveRuntime`nebo a počet volání, která `ReverseEnterRuntime` se nerovná počtu volání `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="66820-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66820-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66820-128">Requirements</span></span>  
 <span data-ttu-id="66820-129">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66820-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66820-130">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="66820-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66820-131">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="66820-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66820-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66820-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66820-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66820-133">See also</span></span>

- [<span data-ttu-id="66820-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66820-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="66820-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66820-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="66820-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66820-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="66820-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66820-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
