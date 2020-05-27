---
title: IHostTaskManager::EnterRuntime – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: b255a1d35aa32975c879aac00f7d4edb8ea88d3b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842033"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="6f5de-102">IHostTaskManager::EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="6f5de-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="6f5de-103">Upozorní hostitele, že volání nespravované metody, jako je například metoda Invoke platformy, vrací řízení provádění modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="6f5de-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f5de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f5de-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6f5de-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6f5de-105">Return Value</span></span>  
  
|<span data-ttu-id="6f5de-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f5de-106">HRESULT</span></span>|<span data-ttu-id="6f5de-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6f5de-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f5de-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f5de-108">S_OK</span></span>|<span data-ttu-id="6f5de-109">`EnterRuntime`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6f5de-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="6f5de-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f5de-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f5de-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6f5de-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f5de-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f5de-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f5de-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6f5de-113">The call timed out.</span></span>|  
|<span data-ttu-id="6f5de-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f5de-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f5de-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6f5de-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f5de-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f5de-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f5de-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6f5de-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f5de-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f5de-118">E_FAIL</span></span>|<span data-ttu-id="6f5de-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6f5de-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f5de-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6f5de-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f5de-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f5de-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6f5de-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6f5de-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6f5de-123">K dokončení požadovaného přidělení není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6f5de-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f5de-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f5de-124">Remarks</span></span>  
 <span data-ttu-id="6f5de-125">`EnterRuntime`je volána pro informování hostitele o tom, že došlo k nespravované funkci, pro kterou bylo provedeno předchozí volání metody [LeaveRuntime –](ihosttaskmanager-leaveruntime-method.md) , která byla dokončena a vrací řízení spouštění do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6f5de-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f5de-126">[ReverseEnterRuntime –](ihosttaskmanager-reverseenterruntime-method.md) je volána pro upozorňování hostitele, že nespravovaná funkce, pro kterou `LeaveRuntime` bylo provedeno předchozí volání, provádí volání do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6f5de-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f5de-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f5de-127">Requirements</span></span>  
 <span data-ttu-id="6f5de-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f5de-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f5de-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f5de-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f5de-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6f5de-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f5de-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f5de-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f5de-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f5de-132">See also</span></span>

- <span data-ttu-id="6f5de-133">[Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6f5de-133">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="6f5de-134">Postupy: volání nativních knihoven DLL ze spravovaného kódu pomocí PInvoke</span><span class="sxs-lookup"><span data-stu-id="6f5de-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="6f5de-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f5de-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6f5de-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f5de-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6f5de-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f5de-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6f5de-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f5de-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="6f5de-139">LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="6f5de-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
