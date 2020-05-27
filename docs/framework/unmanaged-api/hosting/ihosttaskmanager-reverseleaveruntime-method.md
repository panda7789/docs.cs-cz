---
title: IHostTaskManager::ReverseLeaveRuntime – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: d328afcba9761f686dd38bdb2dd651994faaac2a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841851"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="591ba-102">IHostTaskManager::ReverseLeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="591ba-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="591ba-103">Upozorňuje hostitele, že řízení opouští modul CLR (Common Language Runtime) a zadává nespravovanou funkci, která byla zase volána ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="591ba-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="591ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="591ba-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="591ba-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="591ba-105">Return Value</span></span>  
  
|<span data-ttu-id="591ba-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="591ba-106">HRESULT</span></span>|<span data-ttu-id="591ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="591ba-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="591ba-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="591ba-108">S_OK</span></span>|<span data-ttu-id="591ba-109">`ReverseLeaveRuntime`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="591ba-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="591ba-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="591ba-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="591ba-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="591ba-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="591ba-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="591ba-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="591ba-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="591ba-113">The call timed out.</span></span>|  
|<span data-ttu-id="591ba-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="591ba-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="591ba-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="591ba-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="591ba-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="591ba-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="591ba-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="591ba-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="591ba-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="591ba-118">E_FAIL</span></span>|<span data-ttu-id="591ba-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="591ba-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="591ba-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="591ba-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="591ba-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="591ba-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="591ba-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="591ba-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="591ba-123">K dokončení požadovaného přidělení prostředků není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="591ba-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="591ba-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="591ba-124">Remarks</span></span>  
 <span data-ttu-id="591ba-125">Rozhraní CLR `ReverseLeaveRuntime` informuje hostitele o tom, že aktuálně vykonávaná úloha vrací řízení nespravované funkci, která byla volána ze spravovaného kódu prostřednictvím vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="591ba-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="591ba-126">Každé volání `ReverseLeaveRuntime` odpovídá odpovídajícímu volání [ReverseEnterRuntime –](ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="591ba-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="591ba-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="591ba-127">Requirements</span></span>  
 <span data-ttu-id="591ba-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="591ba-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="591ba-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="591ba-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="591ba-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="591ba-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="591ba-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="591ba-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="591ba-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="591ba-132">See also</span></span>

- [<span data-ttu-id="591ba-133">CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="591ba-133">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="591ba-134">EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="591ba-134">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="591ba-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="591ba-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="591ba-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="591ba-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="591ba-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="591ba-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="591ba-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="591ba-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="591ba-139">LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="591ba-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="591ba-140">[Bližší pohled na vyvolání platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="591ba-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
