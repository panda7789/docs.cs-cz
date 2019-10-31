---
title: ICLRTaskManager::GetCurrentTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: a57610d1b41d80d54a245b9744aafd78a1e88177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195909"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="0a103-102">ICLRTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="0a103-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="0a103-103">Získá instanci [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) , která je aktuálně spuštěna ve vlákně operačního systému, ze kterého bylo volání metody provedeno.</span><span class="sxs-lookup"><span data-stu-id="0a103-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a103-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a103-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a103-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a103-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="0a103-106">mimo Ukazatel na adresu `ICLRTask` instance, která je aktuálně prováděna ve vlákně operačního systému, ze kterého volání vyvolala, nebo null, pokud aktuálně není v tomto vlákně prováděna žádná úloha.</span><span class="sxs-lookup"><span data-stu-id="0a103-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a103-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a103-107">Return Value</span></span>  
  
|<span data-ttu-id="0a103-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a103-108">HRESULT</span></span>|<span data-ttu-id="0a103-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0a103-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a103-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a103-110">S_OK</span></span>|<span data-ttu-id="0a103-111">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0a103-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="0a103-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a103-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a103-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0a103-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a103-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a103-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a103-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0a103-115">The call timed out.</span></span>|  
|<span data-ttu-id="0a103-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a103-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a103-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0a103-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a103-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a103-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a103-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0a103-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a103-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a103-120">E_FAIL</span></span>|<span data-ttu-id="0a103-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0a103-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a103-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0a103-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a103-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0a103-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a103-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a103-124">Remarks</span></span>  
 <span data-ttu-id="0a103-125">Instance `ICLRTask`, kterou parametr `ppTask` ukazuje, představuje aktuálně spuštěnou úlohu pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="0a103-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="0a103-126">Instance `ICLRTask` je přidružená k odpovídající instanci [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , která představuje úlohu pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="0a103-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a103-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a103-127">Requirements</span></span>  
 <span data-ttu-id="0a103-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a103-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a103-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a103-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a103-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0a103-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a103-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a103-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a103-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a103-132">See also</span></span>

- [<span data-ttu-id="0a103-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a103-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0a103-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a103-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0a103-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a103-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0a103-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a103-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
