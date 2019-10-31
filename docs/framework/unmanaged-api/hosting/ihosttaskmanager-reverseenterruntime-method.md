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
ms.openlocfilehash: 390a29760c0f3680ca082561607ab678e8bd1e8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133012"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="0aa4e-102">IHostTaskManager::ReverseEnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="0aa4e-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="0aa4e-103">Upozorňuje hostitele, že je provedeno volání modulu CLR (Common Language Runtime) z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0aa4e-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0aa4e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0aa4e-105">Return Value</span></span>  
  
|<span data-ttu-id="0aa4e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0aa4e-106">HRESULT</span></span>|<span data-ttu-id="0aa4e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0aa4e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0aa4e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0aa4e-108">S_OK</span></span>|<span data-ttu-id="0aa4e-109">`ReverseEnterRuntime` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="0aa4e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0aa4e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0aa4e-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0aa4e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0aa4e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0aa4e-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-113">The call timed out.</span></span>|  
|<span data-ttu-id="0aa4e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0aa4e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0aa4e-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0aa4e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0aa4e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0aa4e-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0aa4e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0aa4e-118">E_FAIL</span></span>|<span data-ttu-id="0aa4e-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0aa4e-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0aa4e-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0aa4e-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0aa4e-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0aa4e-123">K dokončení požadovaného přidělení prostředků není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aa4e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0aa4e-124">Remarks</span></span>  
 <span data-ttu-id="0aa4e-125">Pokud je volání CLR provedeno z sekvence, která byla vytvořena ve spravovaném kódu, každé volání `ReverseEnterRuntime` odpovídá volání [ReverseLeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="0aa4e-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0aa4e-126">Volání můžou pocházet z nespravovaného kódu bez vnoření.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="0aa4e-127">V tomto případě není žádné volání [EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)nebo `ReverseLeaveRuntime`a počet volání `ReverseEnterRuntime` se nerovná počtu volání `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="0aa4e-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa4e-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0aa4e-128">Requirements</span></span>  
 <span data-ttu-id="0aa4e-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa4e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa4e-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0aa4e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0aa4e-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0aa4e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0aa4e-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa4e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa4e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aa4e-133">See also</span></span>

- [<span data-ttu-id="0aa4e-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aa4e-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0aa4e-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aa4e-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0aa4e-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aa4e-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0aa4e-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aa4e-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
