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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2059657a6f4543ee29d795ecae7b93b72876fdf4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474628"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="ba517-102">IHostTaskManager::LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="ba517-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="ba517-103">Upozorňuje hostitele, že právě prováděnou úlohu se chystá nechte common language runtime (CLR) a zadejte nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ba517-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba517-104">Odpovídající volání [ihosttaskmanager::enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) upozorňuje hostitele, že je právě prováděnou úlohu pokuste spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ba517-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba517-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba517-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba517-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba517-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="ba517-107">[in] Adresa v mapovaných přenosný spustitelný soubor nespravovanou funkci, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="ba517-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba517-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba517-108">Return Value</span></span>  
  
|<span data-ttu-id="ba517-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba517-109">HRESULT</span></span>|<span data-ttu-id="ba517-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ba517-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba517-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba517-111">S_OK</span></span>|<span data-ttu-id="ba517-112">`LeaveRuntime` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ba517-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="ba517-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ba517-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ba517-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ba517-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ba517-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ba517-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ba517-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ba517-116">The call timed out.</span></span>|  
|<span data-ttu-id="ba517-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ba517-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ba517-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="ba517-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ba517-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ba517-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ba517-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="ba517-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ba517-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ba517-121">E_FAIL</span></span>|<span data-ttu-id="ba517-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="ba517-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ba517-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ba517-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ba517-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ba517-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ba517-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ba517-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ba517-126">Nedostatek paměti je k dispozici k dokončení požadované přidělení.</span><span class="sxs-lookup"><span data-stu-id="ba517-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba517-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba517-127">Remarks</span></span>  
 <span data-ttu-id="ba517-128">Mohou být vnořené sekvence volání do a z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ba517-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="ba517-129">Například následující seznam popisuje hypotetické situace, ve kterém pořadí volání `LeaveRuntime`, [ihosttaskmanager::reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [ihosttaskmanager::reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), a `IHostTaskManager::EnterRuntime` umožňuje tak hostitele kvůli identifikaci vnořených vrstev.</span><span class="sxs-lookup"><span data-stu-id="ba517-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="ba517-130">Akce</span><span class="sxs-lookup"><span data-stu-id="ba517-130">Action</span></span>|<span data-ttu-id="ba517-131">Odpovídající volání metody</span><span class="sxs-lookup"><span data-stu-id="ba517-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="ba517-132">Spravované spustitelný soubor volá jazyka Visual Basic vyvolat nespravovanou funkci napsané v jazyce C s použitím platformy.</span><span class="sxs-lookup"><span data-stu-id="ba517-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="ba517-133">Nespravovaná funkce C volá metodu v spravovaná knihovna DLL, napsaný v C#.</span><span class="sxs-lookup"><span data-stu-id="ba517-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="ba517-134">Spravovanou C# funkce volá jinou nespravované funkci napsané v jazyce C, také pomocí platformy vyvolat.</span><span class="sxs-lookup"><span data-stu-id="ba517-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="ba517-135">Druhá nespravované funkce vrátí provádění C# funkce.</span><span class="sxs-lookup"><span data-stu-id="ba517-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="ba517-136">C# Funkce vrátí vykonávání do první nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ba517-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="ba517-137">První nespravované funkce vrátí vykonávání do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba517-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="ba517-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba517-138">Requirements</span></span>  
 <span data-ttu-id="ba517-139">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba517-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba517-140">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ba517-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba517-141">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba517-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba517-142">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba517-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba517-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba517-143">See also</span></span>
- [<span data-ttu-id="ba517-144">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba517-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ba517-145">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba517-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ba517-146">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba517-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ba517-147">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba517-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
