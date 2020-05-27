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
ms.openlocfilehash: 41955bd2f64d53e3620dede6b6da4cef2aab45f4
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842293"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="66128-102">IHostTaskManager::ReverseEnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="66128-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="66128-103">Upozorňuje hostitele, že je provedeno volání modulu CLR (Common Language Runtime) z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="66128-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66128-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66128-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="66128-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66128-105">Return Value</span></span>  
  
|<span data-ttu-id="66128-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66128-106">HRESULT</span></span>|<span data-ttu-id="66128-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66128-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66128-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="66128-108">S_OK</span></span>|<span data-ttu-id="66128-109">`ReverseEnterRuntime`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="66128-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="66128-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66128-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66128-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="66128-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="66128-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66128-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66128-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="66128-113">The call timed out.</span></span>|  
|<span data-ttu-id="66128-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66128-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66128-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="66128-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66128-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66128-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66128-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="66128-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66128-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="66128-118">E_FAIL</span></span>|<span data-ttu-id="66128-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="66128-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66128-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="66128-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66128-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="66128-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="66128-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="66128-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="66128-123">K dokončení požadovaného přidělení prostředků není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="66128-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66128-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66128-124">Remarks</span></span>  
 <span data-ttu-id="66128-125">Pokud je volání do CLR provedeno z sekvence, která byla vytvořena ve spravovaném kódu, každé volání `ReverseEnterRuntime` odpovídá volání [ReverseLeaveRuntime –](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="66128-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66128-126">Volání můžou pocházet z nespravovaného kódu bez vnoření.</span><span class="sxs-lookup"><span data-stu-id="66128-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="66128-127">V tomto případě neexistuje žádné volání [EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime –](ihosttaskmanager-leaveruntime-method.md)nebo `ReverseLeaveRuntime` a počet volání, která se `ReverseEnterRuntime` nerovná počtu volání `ReverseLeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="66128-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66128-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66128-128">Requirements</span></span>  
 <span data-ttu-id="66128-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66128-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66128-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="66128-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66128-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="66128-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66128-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66128-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66128-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="66128-133">See also</span></span>

- [<span data-ttu-id="66128-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66128-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="66128-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66128-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="66128-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66128-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="66128-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66128-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
