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
ms.openlocfilehash: 118aa3820f422941bea1707dbf7eef2a85027eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439668"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="65c81-102">ICLRTask::SwitchOut – metoda</span><span class="sxs-lookup"><span data-stu-id="65c81-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="65c81-103">Modul CLR (CLR), úloha reprezentována aktuální upozorní [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance je již v spustitelného stavu.</span><span class="sxs-lookup"><span data-stu-id="65c81-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65c81-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="65c81-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="65c81-105">Return Value</span></span>  
  
|<span data-ttu-id="65c81-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65c81-106">HRESULT</span></span>|<span data-ttu-id="65c81-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65c81-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65c81-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="65c81-108">S_OK</span></span>|<span data-ttu-id="65c81-109">`SwitchOut` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="65c81-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="65c81-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65c81-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65c81-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="65c81-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65c81-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65c81-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65c81-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="65c81-113">The call timed out.</span></span>|  
|<span data-ttu-id="65c81-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65c81-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65c81-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="65c81-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65c81-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65c81-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65c81-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="65c81-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65c81-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65c81-118">E_FAIL</span></span>|<span data-ttu-id="65c81-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="65c81-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65c81-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="65c81-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65c81-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65c81-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65c81-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65c81-122">Remarks</span></span>  
 <span data-ttu-id="65c81-123">Hostitel volá `SwitchOut` k informování modulu CLR, aby byla dočasně zastavena, provádění úlohy, aktuální `ICLRTask` instance představuje a přeplánuje úlohu.</span><span class="sxs-lookup"><span data-stu-id="65c81-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c81-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65c81-124">Requirements</span></span>  
 <span data-ttu-id="65c81-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c81-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c81-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65c81-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65c81-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65c81-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65c81-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c81-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c81-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="65c81-129">See Also</span></span>  
 [<span data-ttu-id="65c81-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c81-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="65c81-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c81-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="65c81-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c81-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="65c81-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c81-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
