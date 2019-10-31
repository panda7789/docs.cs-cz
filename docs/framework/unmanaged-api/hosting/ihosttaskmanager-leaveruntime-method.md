---
title: IHostTaskManager::LeaveRuntime – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
ms.openlocfilehash: 8ac1c18d094deca50d461ef9ff0933a4f87176e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132996"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="5b6f7-102">IHostTaskManager::LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="5b6f7-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="5b6f7-103">Upozorňuje hostitele, že aktuálně vykonávaný úkol se chystá opustit modul CLR (Common Language Runtime) a zadat nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b6f7-104">Odpovídající volání [IHostTaskManager:: EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) upozorní hostitele, že aktuálně prováděná úloha předává spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b6f7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b6f7-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b6f7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b6f7-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="5b6f7-107">pro Adresa v mapovaném přenositelném spustitelném souboru nespravované funkce, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b6f7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5b6f7-108">Return Value</span></span>  
  
|<span data-ttu-id="5b6f7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b6f7-109">HRESULT</span></span>|<span data-ttu-id="5b6f7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5b6f7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b6f7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b6f7-111">S_OK</span></span>|<span data-ttu-id="5b6f7-112">`LeaveRuntime` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="5b6f7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b6f7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b6f7-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b6f7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b6f7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b6f7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-116">The call timed out.</span></span>|  
|<span data-ttu-id="5b6f7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b6f7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b6f7-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b6f7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b6f7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b6f7-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b6f7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b6f7-121">E_FAIL</span></span>|<span data-ttu-id="5b6f7-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b6f7-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b6f7-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5b6f7-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5b6f7-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5b6f7-126">K dokončení požadovaného přidělení není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b6f7-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b6f7-127">Remarks</span></span>  
 <span data-ttu-id="5b6f7-128">Sekvence volání do a z nespravovaného kódu mohou být vnořeny.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="5b6f7-129">Například následující seznam popisuje hypotetickou situaci, ve které sekvence volání `LeaveRuntime`, [IHostTaskManager:: ReverseEnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)a `IHostTaskManager::EnterRuntime` umožňuje hostiteli identifikovat vnořené vrstvy.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="5b6f7-130">Akce</span><span class="sxs-lookup"><span data-stu-id="5b6f7-130">Action</span></span>|<span data-ttu-id="5b6f7-131">Odpovídající volání metody</span><span class="sxs-lookup"><span data-stu-id="5b6f7-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="5b6f7-132">Spravovaný spustitelný soubor Visual Basic volá nespravovanou funkci napsanou v jazyce C pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="5b6f7-133">Nespravovaná funkce jazyka C volá metodu ve spravované knihovně DLL napsané v C#.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="5b6f7-134">Spravovaná C# funkce volá jinou nespravovanou funkci napsanou v jazyce C, používá také vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="5b6f7-135">Druhá nespravovaná funkce vrátí provedení do C# funkce.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="5b6f7-136">C# Funkce vrátí provedení první nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="5b6f7-137">První nespravovaná funkce vrátí provedení Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="5b6f7-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="5b6f7-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b6f7-138">Requirements</span></span>  
 <span data-ttu-id="5b6f7-139">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b6f7-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b6f7-140">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5b6f7-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b6f7-141">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b6f7-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b6f7-142">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b6f7-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6f7-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b6f7-143">See also</span></span>

- [<span data-ttu-id="5b6f7-144">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b6f7-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5b6f7-145">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b6f7-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5b6f7-146">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b6f7-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5b6f7-147">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b6f7-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
