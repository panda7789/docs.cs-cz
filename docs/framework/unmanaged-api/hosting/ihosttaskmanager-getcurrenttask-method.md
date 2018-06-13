---
title: IHostTaskManager::GetCurrentTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2420ddb5cf9be2cfb08f89d27d9aa277305e7ffb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442689"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="c1934-102">IHostTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="c1934-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="c1934-103">Získá ukazatele rozhraní pro úlohu, která je aktuálně spuštěných ve vláknu operačního systému, ze kterého přišla tato žádost.</span><span class="sxs-lookup"><span data-stu-id="c1934-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1934-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1934-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1934-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1934-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="c1934-106">[out] Ukazatel na adresu [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která představuje aktuálně spuštěné úlohy nebo null, pokud je aktuálně spuštěné žádné úlohy.</span><span class="sxs-lookup"><span data-stu-id="c1934-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1934-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1934-107">Return Value</span></span>  
  
|<span data-ttu-id="c1934-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1934-108">HRESULT</span></span>|<span data-ttu-id="c1934-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c1934-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1934-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1934-110">S_OK</span></span>|<span data-ttu-id="c1934-111">`GetCurrentTask` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c1934-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="c1934-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1934-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1934-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c1934-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1934-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1934-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1934-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c1934-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1934-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1934-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1934-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c1934-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1934-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1934-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1934-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c1934-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1934-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1934-120">E_FAIL</span></span>|<span data-ttu-id="c1934-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c1934-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1934-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c1934-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1934-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c1934-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c1934-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="c1934-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="c1934-125">`GetCurrentTask` byla volána ve vlákně operačního systému mimo ovládací prvek hostitele.</span><span class="sxs-lookup"><span data-stu-id="c1934-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1934-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1934-126">Remarks</span></span>  
 <span data-ttu-id="c1934-127">Hostitele lze také nastavit `pTask` parametr na hodnotu null pro úlohu, která nezahájila zabránit v přechodu do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c1934-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1934-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1934-128">Requirements</span></span>  
 <span data-ttu-id="c1934-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1934-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1934-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1934-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1934-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1934-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1934-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1934-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1934-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1934-133">See Also</span></span>  
 [<span data-ttu-id="c1934-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1934-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c1934-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1934-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c1934-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1934-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c1934-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1934-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
