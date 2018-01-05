---
title: "IHostTaskManager::ReverseLeaveRuntime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseLeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa16e640cade9304916650c4ea13231cacb967f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="820b0-102">IHostTaskManager::ReverseLeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="820b0-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="820b0-103">Hostitele upozorní, že je ovládací prvek ponechat common language runtime (CLR) a zadáním nespravované funkci, která byla, pak volané ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="820b0-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="820b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="820b0-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="820b0-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="820b0-105">Return Value</span></span>  
  
|<span data-ttu-id="820b0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="820b0-106">HRESULT</span></span>|<span data-ttu-id="820b0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="820b0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="820b0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="820b0-108">S_OK</span></span>|<span data-ttu-id="820b0-109">`ReverseLeaveRuntime`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="820b0-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="820b0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="820b0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="820b0-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="820b0-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="820b0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="820b0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="820b0-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="820b0-113">The call timed out.</span></span>|  
|<span data-ttu-id="820b0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="820b0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="820b0-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="820b0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="820b0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="820b0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="820b0-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="820b0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="820b0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="820b0-118">E_FAIL</span></span>|<span data-ttu-id="820b0-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="820b0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="820b0-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="820b0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="820b0-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="820b0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="820b0-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="820b0-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="820b0-123">Nedostatek paměti je k dispozici k dokončení přidělení požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="820b0-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="820b0-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="820b0-124">Remarks</span></span>  
 <span data-ttu-id="820b0-125">Volání CLR `ReverseLeaveRuntime` k informování hostitele, který vrací aktuálně prováděné úlohy vyvolání ovládacího prvku na nespravované funkci, která byla, pak volané ze spravovaného kódu pomocí platformy.</span><span class="sxs-lookup"><span data-stu-id="820b0-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="820b0-126">Každé volání `ReverseLeaveRuntime` odpovídá odpovídající volání [reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="820b0-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="820b0-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="820b0-127">Requirements</span></span>  
 <span data-ttu-id="820b0-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="820b0-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="820b0-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="820b0-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="820b0-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="820b0-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="820b0-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="820b0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820b0-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="820b0-132">See Also</span></span>  
 [<span data-ttu-id="820b0-133">CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="820b0-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="820b0-134">EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="820b0-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="820b0-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="820b0-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="820b0-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="820b0-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="820b0-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="820b0-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="820b0-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="820b0-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="820b0-139">LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="820b0-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="820b0-140">Vyvolání bližší pohled na platformy</span><span class="sxs-lookup"><span data-stu-id="820b0-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
