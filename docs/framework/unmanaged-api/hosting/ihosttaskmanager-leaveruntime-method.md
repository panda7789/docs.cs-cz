---
title: "IHostTaskManager::LeaveRuntime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4c168cffba44a21d6705e8abd921ecbf8a9da6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="c90c6-102">IHostTaskManager::LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="c90c6-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="c90c6-103">Upozorní hostitele, aktuálně prováděné úlohy je nechte common language runtime (CLR) a zadejte nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c90c6-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c90c6-104">Odpovídající volání [ihosttaskmanager::enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) upozorní hostitele aktuálně prováděné úlohy je nutnosti opětovného zadávání spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c90c6-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c90c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c90c6-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c90c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c90c6-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="c90c6-107">[v] Adresa v rámci namapované přenosné spustitelný soubor nespravované funkce, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="c90c6-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c90c6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c90c6-108">Return Value</span></span>  
  
|<span data-ttu-id="c90c6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c90c6-109">HRESULT</span></span>|<span data-ttu-id="c90c6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c90c6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c90c6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c90c6-111">S_OK</span></span>|<span data-ttu-id="c90c6-112">`LeaveRuntime`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c90c6-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="c90c6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c90c6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c90c6-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c90c6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c90c6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c90c6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c90c6-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c90c6-116">The call timed out.</span></span>|  
|<span data-ttu-id="c90c6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c90c6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c90c6-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c90c6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c90c6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c90c6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c90c6-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c90c6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c90c6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c90c6-121">E_FAIL</span></span>|<span data-ttu-id="c90c6-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c90c6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c90c6-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c90c6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c90c6-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c90c6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c90c6-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c90c6-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c90c6-126">Je k dispozici k dokončení požadované přidělení není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="c90c6-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c90c6-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c90c6-127">Remarks</span></span>  
 <span data-ttu-id="c90c6-128">Mohou být vnořené pořadí volání do a z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c90c6-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="c90c6-129">Například následující seznam popisuje hypotetický situace, ve kterém je pořadí volání `LeaveRuntime`, [ihosttaskmanager::reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [ihosttaskmanager::reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), a `IHostTaskManager::EnterRuntime` umožňuje hostitele k identifikaci vnořené vrstvy.</span><span class="sxs-lookup"><span data-stu-id="c90c6-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="c90c6-130">Akce</span><span class="sxs-lookup"><span data-stu-id="c90c6-130">Action</span></span>|<span data-ttu-id="c90c6-131">Odpovídající volání metody</span><span class="sxs-lookup"><span data-stu-id="c90c6-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="c90c6-132">Vyvolání nespravované funkce napsané v jazyce C pomocí platformy spravované spustitelné volání jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c90c6-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="c90c6-133">Nespravované funkce C volá metodu v spravovanou knihovnu DLL napsané v C#.</span><span class="sxs-lookup"><span data-stu-id="c90c6-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="c90c6-134">Spravované funkce jazyka C# volá jinou funkci nespravované napsané v jazyce C, také pomocí platformy vyvolání.</span><span class="sxs-lookup"><span data-stu-id="c90c6-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="c90c6-135">Nespravované funkce second vrátí provádění funkce jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="c90c6-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="c90c6-136">Funkce jazyka C# vrací provádění první nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="c90c6-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="c90c6-137">První nespravované funkce vrátí provádění programu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c90c6-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="c90c6-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c90c6-138">Requirements</span></span>  
 <span data-ttu-id="c90c6-139">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c90c6-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c90c6-140">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c90c6-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c90c6-141">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c90c6-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c90c6-142">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c90c6-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90c6-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="c90c6-143">See Also</span></span>  
 [<span data-ttu-id="c90c6-144">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c90c6-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c90c6-145">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c90c6-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c90c6-146">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c90c6-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c90c6-147">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c90c6-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
