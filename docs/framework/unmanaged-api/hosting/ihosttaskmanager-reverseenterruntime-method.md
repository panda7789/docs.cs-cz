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
ms.openlocfilehash: 20b6fcd0e5e4ce4055a6678e931dee50a6a4ccc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496185"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="48074-102">IHostTaskManager::ReverseEnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="48074-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="48074-103">Upozorňuje hostitele, že je se k volání do common language runtime (CLR) z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="48074-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48074-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48074-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="48074-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="48074-105">Return Value</span></span>  
  
|<span data-ttu-id="48074-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48074-106">HRESULT</span></span>|<span data-ttu-id="48074-107">Popis</span><span class="sxs-lookup"><span data-stu-id="48074-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48074-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="48074-108">S_OK</span></span>|<span data-ttu-id="48074-109">`ReverseEnterRuntime` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="48074-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="48074-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48074-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48074-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="48074-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48074-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48074-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48074-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="48074-113">The call timed out.</span></span>|  
|<span data-ttu-id="48074-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48074-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48074-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="48074-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48074-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48074-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48074-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="48074-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48074-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48074-118">E_FAIL</span></span>|<span data-ttu-id="48074-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="48074-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48074-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="48074-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48074-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="48074-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="48074-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="48074-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="48074-123">Nedostatek paměti je k dispozici k dokončení přidělení požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="48074-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48074-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48074-124">Remarks</span></span>  
 <span data-ttu-id="48074-125">Pokud je provedeno volání do modulu CLR z sekvenci, která pochází ve spravovaném kódu, každé volání `ReverseEnterRuntime` odpovídá volání [reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="48074-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48074-126">Volání můžou pocházet z nespravovaného kódu bez je vnořená.</span><span class="sxs-lookup"><span data-stu-id="48074-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="48074-127">V takovém případě není žádná volání [enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [leaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), nebo `ReverseLeaveRuntime`a počet volání `ReverseEnterRuntime` se nerovná počtu volání `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="48074-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48074-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48074-128">Requirements</span></span>  
 <span data-ttu-id="48074-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48074-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48074-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48074-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48074-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48074-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48074-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48074-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48074-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48074-133">See also</span></span>
- [<span data-ttu-id="48074-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48074-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="48074-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48074-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="48074-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48074-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="48074-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48074-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
