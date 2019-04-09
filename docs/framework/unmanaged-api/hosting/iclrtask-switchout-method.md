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
ms.openlocfilehash: a215189461bd22011462842bf02ff6c0109119fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090034"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="2141e-102">ICLRTask::SwitchOut – metoda</span><span class="sxs-lookup"><span data-stu-id="2141e-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="2141e-103">Upozorní common language runtime (CLR), která úloha je reprezentována aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance již provozuschopného stavu.</span><span class="sxs-lookup"><span data-stu-id="2141e-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2141e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2141e-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2141e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2141e-105">Return Value</span></span>  
  
|<span data-ttu-id="2141e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2141e-106">HRESULT</span></span>|<span data-ttu-id="2141e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2141e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2141e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2141e-108">S_OK</span></span>|`SwitchOut` <span data-ttu-id="2141e-109">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2141e-109">returned successfully.</span></span>|  
|<span data-ttu-id="2141e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2141e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2141e-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2141e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2141e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2141e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2141e-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2141e-113">The call timed out.</span></span>|  
|<span data-ttu-id="2141e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2141e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2141e-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="2141e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2141e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2141e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2141e-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="2141e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2141e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2141e-118">E_FAIL</span></span>|<span data-ttu-id="2141e-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="2141e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2141e-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2141e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2141e-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2141e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2141e-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2141e-122">Remarks</span></span>  
 <span data-ttu-id="2141e-123">Volá hostitele `SwitchOut` CLR informovat, že dočasně zastavila provádění úlohy, které aktuální `ICLRTask` instance představuje a přeplánuje úkolu.</span><span class="sxs-lookup"><span data-stu-id="2141e-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2141e-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2141e-124">Requirements</span></span>  
 <span data-ttu-id="2141e-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2141e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2141e-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2141e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2141e-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2141e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2141e-128">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2141e-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2141e-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2141e-129">See also</span></span>

- [<span data-ttu-id="2141e-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2141e-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2141e-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2141e-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2141e-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2141e-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2141e-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2141e-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
