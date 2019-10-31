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
ms.openlocfilehash: a3af57859c5284ff45681ffc2b5aa3ea3cf8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133061"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="a9353-102">IHostTaskManager::EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="a9353-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="a9353-103">Upozorní hostitele, že volání nespravované metody, jako je například metoda Invoke platformy, vrací řízení provádění modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a9353-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9353-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9353-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a9353-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a9353-105">Return Value</span></span>  
  
|<span data-ttu-id="a9353-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9353-106">HRESULT</span></span>|<span data-ttu-id="a9353-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a9353-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9353-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9353-108">S_OK</span></span>|<span data-ttu-id="a9353-109">`EnterRuntime` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a9353-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="a9353-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9353-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9353-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a9353-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9353-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9353-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9353-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a9353-113">The call timed out.</span></span>|  
|<span data-ttu-id="a9353-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9353-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9353-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="a9353-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9353-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9353-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9353-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="a9353-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9353-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9353-118">E_FAIL</span></span>|<span data-ttu-id="a9353-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="a9353-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9353-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="a9353-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9353-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9353-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9353-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a9353-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a9353-123">K dokončení požadovaného přidělení není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="a9353-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9353-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9353-124">Remarks</span></span>  
 <span data-ttu-id="a9353-125">`EnterRuntime` je volána pro informování hostitele o tom, že došlo k nespravované funkci, pro kterou bylo provedeno předchozí volání metody [LeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) , dokončilo se provádění a vrací řízení provádění do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a9353-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9353-126">[ReverseEnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) je volána pro upozorňování hostitele, že nespravovaná funkce, pro kterou bylo provedeno předchozí volání `LeaveRuntime`, provádí volání spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a9353-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9353-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9353-127">Requirements</span></span>  
 <span data-ttu-id="a9353-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9353-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9353-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a9353-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9353-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9353-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9353-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9353-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9353-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9353-132">See also</span></span>

- [<span data-ttu-id="a9353-133">Pokročilá interoperabilita modelu COM</span><span class="sxs-lookup"><span data-stu-id="a9353-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="a9353-134">Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke</span><span class="sxs-lookup"><span data-stu-id="a9353-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="a9353-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9353-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a9353-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9353-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a9353-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9353-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a9353-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9353-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="a9353-139">LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="a9353-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
