---
title: "IHostTask::GetPriority – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.GetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 468a2e29ed3c031889fdc5df3d4defa6506d8fcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="f6696-102">IHostTask::GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="f6696-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="f6696-103">Získá přístup z více vláken úroveň priority úlohy reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="f6696-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6696-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6696-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6696-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6696-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="f6696-106">[out] Ukazatel na celé číslo, které určuje úroveň priority vlákno úlohy reprezentována aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="f6696-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6696-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f6696-107">Return Value</span></span>  
  
|<span data-ttu-id="f6696-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6696-108">HRESULT</span></span>|<span data-ttu-id="f6696-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f6696-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6696-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6696-110">S_OK</span></span>|<span data-ttu-id="f6696-111">`GetPriority`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f6696-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="f6696-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6696-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6696-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f6696-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6696-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6696-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6696-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f6696-115">The call timed out.</span></span>|  
|<span data-ttu-id="f6696-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6696-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6696-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="f6696-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6696-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6696-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6696-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="f6696-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6696-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6696-120">E_FAIL</span></span>|<span data-ttu-id="f6696-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="f6696-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6696-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f6696-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6696-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f6696-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6696-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6696-124">Remarks</span></span>  
 <span data-ttu-id="f6696-125">Přístup z více vláken s prioritou úrovně hodnoty jsou definovány Win32 `SetThreadPriority` funkce.</span><span class="sxs-lookup"><span data-stu-id="f6696-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6696-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6696-126">Requirements</span></span>  
 <span data-ttu-id="f6696-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6696-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6696-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6696-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6696-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6696-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6696-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6696-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6696-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6696-131">See Also</span></span>  
 [<span data-ttu-id="f6696-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6696-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f6696-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6696-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f6696-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6696-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f6696-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6696-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
