---
title: IHostGCManager::ThreadIsBlockingForSuspension – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85921156860f52eb2a898e6be356e191c2a4f02d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439267"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="a0673-102">IHostGCManager::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="a0673-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="a0673-103">Upozorní na hostitele, vlákno, ze kterého bylo provedeno volání metody se rozhodli jste se blokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a0673-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0673-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0673-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a0673-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0673-105">Return Value</span></span>  
  
|<span data-ttu-id="a0673-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0673-106">HRESULT</span></span>|<span data-ttu-id="a0673-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a0673-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0673-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0673-108">S_OK</span></span>|<span data-ttu-id="a0673-109">`ThreadIsBlockingForSuspension` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a0673-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="a0673-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0673-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0673-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a0673-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0673-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0673-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0673-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a0673-113">The call timed out.</span></span>|  
|<span data-ttu-id="a0673-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0673-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0673-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="a0673-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0673-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0673-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0673-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="a0673-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0673-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0673-118">E_FAIL</span></span>|<span data-ttu-id="a0673-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="a0673-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0673-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a0673-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0673-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a0673-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0673-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0673-122">Remarks</span></span>  
 <span data-ttu-id="a0673-123">Modul CLR obvykle volá `ThreadIsBlockForSuspension` metoda v rámci přípravy uvolňování umožnit hostitele příležitost přeplánovat vlákno pro nespravovaná úlohy.</span><span class="sxs-lookup"><span data-stu-id="a0673-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0673-124">Hostitele lze změnit plán naplánovaných úloh až po volání `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="a0673-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="a0673-125">Po volání modulu runtime [suspensionstarting –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), hostitele nesmí změnit plán úlohy.</span><span class="sxs-lookup"><span data-stu-id="a0673-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0673-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0673-126">Requirements</span></span>  
 <span data-ttu-id="a0673-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0673-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0673-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0673-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0673-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0673-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0673-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0673-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0673-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0673-131">See Also</span></span>  
 [<span data-ttu-id="a0673-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0673-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a0673-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0673-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a0673-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0673-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a0673-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0673-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="a0673-136">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0673-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
