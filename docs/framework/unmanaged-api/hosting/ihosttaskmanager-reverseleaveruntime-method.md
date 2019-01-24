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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9f5b6ad4765edfdea9f56debad085d69e9fc769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680436"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="6eb0b-102">IHostTaskManager::ReverseLeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="6eb0b-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="6eb0b-103">Upozorňuje hostitele, že je ovládací prvek opuštění common language runtime (CLR) a zadáním nespravované funkci, která byla, pak volá ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eb0b-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6eb0b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6eb0b-105">Return Value</span></span>  
  
|<span data-ttu-id="6eb0b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6eb0b-106">HRESULT</span></span>|<span data-ttu-id="6eb0b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6eb0b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6eb0b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6eb0b-108">S_OK</span></span>|<span data-ttu-id="6eb0b-109">`ReverseLeaveRuntime` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="6eb0b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6eb0b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6eb0b-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6eb0b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6eb0b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6eb0b-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-113">The call timed out.</span></span>|  
|<span data-ttu-id="6eb0b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6eb0b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6eb0b-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6eb0b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6eb0b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6eb0b-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6eb0b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6eb0b-118">E_FAIL</span></span>|<span data-ttu-id="6eb0b-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6eb0b-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6eb0b-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6eb0b-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6eb0b-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6eb0b-123">Nedostatek paměti je k dispozici k dokončení přidělení požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eb0b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eb0b-124">Remarks</span></span>  
 <span data-ttu-id="6eb0b-125">Volání CLR `ReverseLeaveRuntime` informovat hostitele, který vrací právě prováděnou úlohu vyvolání ovládacího prvku na nespravované funkci, která byla, pak volat ze spravovaného kódu prostřednictvím platformy.</span><span class="sxs-lookup"><span data-stu-id="6eb0b-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="6eb0b-126">Každé volání `ReverseLeaveRuntime` odpovídá odpovídající volání [reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="6eb0b-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb0b-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6eb0b-127">Requirements</span></span>  
 <span data-ttu-id="6eb0b-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eb0b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb0b-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6eb0b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6eb0b-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6eb0b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6eb0b-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb0b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb0b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eb0b-132">See also</span></span>
- [<span data-ttu-id="6eb0b-133">CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="6eb0b-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="6eb0b-134">EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="6eb0b-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="6eb0b-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eb0b-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6eb0b-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eb0b-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6eb0b-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eb0b-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6eb0b-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eb0b-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="6eb0b-139">LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="6eb0b-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- [<span data-ttu-id="6eb0b-140">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="6eb0b-140">A Closer Look at Platform Invoke</span></span>](https://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
