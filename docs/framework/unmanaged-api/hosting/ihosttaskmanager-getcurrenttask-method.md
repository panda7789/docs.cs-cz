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
ms.openlocfilehash: d1d6ddfe7834a1c6f22b9195042d32363d6ea6cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133045"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="b3006-102">IHostTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="b3006-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="b3006-103">Získá ukazatel rozhraní na úlohu, která je aktuálně prováděna ve vlákně operačního systému, ze kterého je toto volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="b3006-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3006-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3006-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3006-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3006-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="b3006-106">mimo Ukazatel na adresu instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , která představuje aktuálně spuštěnou úlohu nebo hodnotu null, pokud aktuálně není spuštěn žádný úkol.</span><span class="sxs-lookup"><span data-stu-id="b3006-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3006-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b3006-107">Return Value</span></span>  
  
|<span data-ttu-id="b3006-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3006-108">HRESULT</span></span>|<span data-ttu-id="b3006-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b3006-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3006-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3006-110">S_OK</span></span>|<span data-ttu-id="b3006-111">`GetCurrentTask` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b3006-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="b3006-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3006-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3006-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b3006-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3006-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3006-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3006-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b3006-115">The call timed out.</span></span>|  
|<span data-ttu-id="b3006-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3006-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3006-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b3006-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3006-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3006-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3006-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b3006-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3006-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3006-120">E_FAIL</span></span>|<span data-ttu-id="b3006-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b3006-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3006-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b3006-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3006-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b3006-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b3006-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b3006-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b3006-125">`GetCurrentTask` byla volána pro vlákno operačního systému mimo ovládací prvek hostitele.</span><span class="sxs-lookup"><span data-stu-id="b3006-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3006-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3006-126">Remarks</span></span>  
 <span data-ttu-id="b3006-127">Hostitel může také nastavit parametr `pTask` na hodnotu null, aby se zabránilo úloze, kterou nezahájil vstup do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b3006-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3006-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3006-128">Requirements</span></span>  
 <span data-ttu-id="b3006-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3006-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3006-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3006-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3006-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b3006-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3006-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3006-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3006-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3006-133">See also</span></span>

- [<span data-ttu-id="b3006-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3006-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b3006-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3006-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b3006-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3006-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b3006-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3006-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
