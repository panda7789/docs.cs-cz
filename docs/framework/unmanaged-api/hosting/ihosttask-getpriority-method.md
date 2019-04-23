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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 702992ab4edfea3f0b699efefedb195cd87586ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136770"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="461b4-102">IHostTask::GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="461b4-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="461b4-103">Získá úroveň priority vlákna úloh reprezentovaný aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="461b4-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="461b4-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="461b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="461b4-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="461b4-106">[out] Ukazatel na celé číslo, které určuje úroveň priority vlákna úloh reprezentovaný aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="461b4-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="461b4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="461b4-107">Return Value</span></span>  
  
|<span data-ttu-id="461b4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="461b4-108">HRESULT</span></span>|<span data-ttu-id="461b4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="461b4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="461b4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="461b4-110">S_OK</span></span>|<span data-ttu-id="461b4-111">`GetPriority` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="461b4-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="461b4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="461b4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="461b4-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="461b4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="461b4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="461b4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="461b4-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="461b4-115">The call timed out.</span></span>|  
|<span data-ttu-id="461b4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="461b4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="461b4-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="461b4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="461b4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="461b4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="461b4-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="461b4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="461b4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="461b4-120">E_FAIL</span></span>|<span data-ttu-id="461b4-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="461b4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="461b4-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="461b4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="461b4-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="461b4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="461b4-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="461b4-124">Remarks</span></span>  
 <span data-ttu-id="461b4-125">Hodnoty úroveň priority vlákna jsou definovány Win32 `SetThreadPriority` funkce.</span><span class="sxs-lookup"><span data-stu-id="461b4-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461b4-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="461b4-126">Requirements</span></span>  
 <span data-ttu-id="461b4-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461b4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="461b4-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="461b4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="461b4-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="461b4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="461b4-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461b4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461b4-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="461b4-131">See also</span></span>

- [<span data-ttu-id="461b4-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="461b4-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="461b4-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="461b4-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="461b4-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="461b4-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="461b4-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="461b4-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
