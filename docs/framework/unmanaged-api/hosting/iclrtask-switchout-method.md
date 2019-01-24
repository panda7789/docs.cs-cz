---
title: ICLRTask::SwitchOut – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b0a4450b6cfa98d0c939c148229d48d0b1d4c7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556571"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="68c75-102">ICLRTask::SwitchOut – metoda</span><span class="sxs-lookup"><span data-stu-id="68c75-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="68c75-103">Upozorní common language runtime (CLR), která úloha je reprezentována aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance již provozuschopného stavu.</span><span class="sxs-lookup"><span data-stu-id="68c75-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68c75-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="68c75-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="68c75-105">Return Value</span></span>  
  
|<span data-ttu-id="68c75-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68c75-106">HRESULT</span></span>|<span data-ttu-id="68c75-107">Popis</span><span class="sxs-lookup"><span data-stu-id="68c75-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68c75-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="68c75-108">S_OK</span></span>|<span data-ttu-id="68c75-109">`SwitchOut` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="68c75-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="68c75-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68c75-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68c75-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="68c75-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="68c75-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="68c75-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="68c75-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="68c75-113">The call timed out.</span></span>|  
|<span data-ttu-id="68c75-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="68c75-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="68c75-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="68c75-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="68c75-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="68c75-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="68c75-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="68c75-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="68c75-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68c75-118">E_FAIL</span></span>|<span data-ttu-id="68c75-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="68c75-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="68c75-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="68c75-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="68c75-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="68c75-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68c75-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68c75-122">Remarks</span></span>  
 <span data-ttu-id="68c75-123">Volá hostitele `SwitchOut` CLR informovat, že dočasně zastavila provádění úlohy, které aktuální `ICLRTask` instance představuje a přeplánuje úkolu.</span><span class="sxs-lookup"><span data-stu-id="68c75-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68c75-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68c75-124">Requirements</span></span>  
 <span data-ttu-id="68c75-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68c75-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68c75-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="68c75-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68c75-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68c75-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68c75-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68c75-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c75-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68c75-129">See also</span></span>
- [<span data-ttu-id="68c75-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68c75-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="68c75-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68c75-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="68c75-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68c75-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="68c75-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68c75-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
