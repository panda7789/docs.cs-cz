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
ms.openlocfilehash: e0945a4b32a155e99e0402dfcdcc826d1eff3eb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442017"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="ccae3-102">IHostTaskManager::ReverseEnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="ccae3-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="ccae3-103">Upozorní hostitele, že se provádí volání do common language runtime (CLR) z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ccae3-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccae3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccae3-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ccae3-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ccae3-105">Return Value</span></span>  
  
|<span data-ttu-id="ccae3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ccae3-106">HRESULT</span></span>|<span data-ttu-id="ccae3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ccae3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ccae3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ccae3-108">S_OK</span></span>|<span data-ttu-id="ccae3-109">`ReverseEnterRuntime` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ccae3-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="ccae3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ccae3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ccae3-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ccae3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ccae3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ccae3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ccae3-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ccae3-113">The call timed out.</span></span>|  
|<span data-ttu-id="ccae3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ccae3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ccae3-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ccae3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ccae3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ccae3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ccae3-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ccae3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ccae3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ccae3-118">E_FAIL</span></span>|<span data-ttu-id="ccae3-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ccae3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ccae3-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ccae3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ccae3-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ccae3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ccae3-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ccae3-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ccae3-123">Nedostatek paměti je k dispozici k dokončení přidělení požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="ccae3-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccae3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccae3-124">Remarks</span></span>  
 <span data-ttu-id="ccae3-125">Pokud ve spravovaném kódu je provedeno volání do modulu CLR z pořadí, které pochází, každé volání `ReverseEnterRuntime` odpovídá volání [reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="ccae3-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccae3-126">Volání můžete bez vnořenými pocházejí z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ccae3-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="ccae3-127">V takovém případě není bez volání [enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [leaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), nebo `ReverseLeaveRuntime`a počet volání `ReverseEnterRuntime` se nerovná počtu volání `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="ccae3-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccae3-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccae3-128">Requirements</span></span>  
 <span data-ttu-id="ccae3-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccae3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccae3-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ccae3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ccae3-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ccae3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccae3-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccae3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccae3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccae3-133">See Also</span></span>  
 [<span data-ttu-id="ccae3-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccae3-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ccae3-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccae3-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ccae3-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccae3-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ccae3-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccae3-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
