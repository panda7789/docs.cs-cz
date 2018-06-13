---
title: IHostTaskManager::BeginDelayAbort – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65bb59efa9d38fa32baa38eb239103f5cfa8be86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441913"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="a3625-102">IHostTaskManager::BeginDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="a3625-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="a3625-103">Upozorní, že hostitele, který spravovaný kód je zadání období, ve kterém nesmí přerušil aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="a3625-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3625-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3625-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a3625-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a3625-105">Return Value</span></span>  
  
|<span data-ttu-id="a3625-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3625-106">HRESULT</span></span>|<span data-ttu-id="a3625-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a3625-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3625-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3625-108">S_OK</span></span>|<span data-ttu-id="a3625-109">`BeginDelayAbort` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a3625-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="a3625-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3625-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3625-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a3625-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a3625-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a3625-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a3625-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a3625-113">The call timed out.</span></span>|  
|<span data-ttu-id="a3625-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a3625-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a3625-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="a3625-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a3625-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a3625-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a3625-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="a3625-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a3625-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3625-118">E_FAIL</span></span>|<span data-ttu-id="a3625-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="a3625-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a3625-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a3625-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a3625-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a3625-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a3625-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="a3625-122">E_UNEXPECTED</span></span>|<span data-ttu-id="a3625-123">`BeginDelayAbort` již byla volána, ale odpovídající volání [enddelayabort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) ještě nebylo přijato.</span><span class="sxs-lookup"><span data-stu-id="a3625-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3625-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3625-124">Remarks</span></span>  
 <span data-ttu-id="a3625-125">Hostitele nesmí přerušit aktuální úlohy, dokud `EndDelayAbort` je volána.</span><span class="sxs-lookup"><span data-stu-id="a3625-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="a3625-126">Pokud jiné volat na `BeginDelayAbort` přišla bez použité volání `EndDelayAbort`, hostitele by měla vrátit E_UNEXPECTED z `BeginDelayAbort`a měli provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="a3625-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3625-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3625-127">Requirements</span></span>  
 <span data-ttu-id="a3625-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3625-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3625-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3625-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3625-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3625-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3625-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3625-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3625-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3625-132">See Also</span></span>  
 [<span data-ttu-id="a3625-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3625-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a3625-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3625-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a3625-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3625-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="a3625-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3625-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
