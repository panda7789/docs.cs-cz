---
title: IHostTask::GetPriority – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: 6c33fa6d2e6cb09f013c5334461e61235db549f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121423"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="e896f-102">IHostTask::GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="e896f-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="e896f-103">Získá úroveň priority vlákna úlohy reprezentované aktuální instancí [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e896f-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e896f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e896f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e896f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e896f-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="e896f-106">mimo Ukazatel na celé číslo, které označuje úroveň priority vlákna úlohy reprezentované aktuální instancí `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="e896f-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e896f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e896f-107">Return Value</span></span>  
  
|<span data-ttu-id="e896f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e896f-108">HRESULT</span></span>|<span data-ttu-id="e896f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e896f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e896f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e896f-110">S_OK</span></span>|<span data-ttu-id="e896f-111">`GetPriority` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e896f-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="e896f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e896f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e896f-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e896f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e896f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e896f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e896f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e896f-115">The call timed out.</span></span>|  
|<span data-ttu-id="e896f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e896f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e896f-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e896f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e896f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e896f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e896f-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e896f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e896f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e896f-120">E_FAIL</span></span>|<span data-ttu-id="e896f-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e896f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e896f-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e896f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e896f-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e896f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e896f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e896f-124">Remarks</span></span>  
 <span data-ttu-id="e896f-125">Hodnoty úrovně priority vlákna jsou definovány funkcí Win32 `SetThreadPriority`.</span><span class="sxs-lookup"><span data-stu-id="e896f-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e896f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e896f-126">Requirements</span></span>  
 <span data-ttu-id="e896f-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e896f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e896f-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e896f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e896f-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e896f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e896f-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e896f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e896f-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e896f-131">See also</span></span>

- [<span data-ttu-id="e896f-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e896f-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e896f-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e896f-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e896f-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e896f-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e896f-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e896f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
