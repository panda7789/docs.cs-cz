---
title: "ICLRTask::ExitTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff2adafa41ce68a824f6b01888c3565bf054c031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="e4fb7-102">ICLRTask::ExitTask – metoda</span><span class="sxs-lookup"><span data-stu-id="e4fb7-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="e4fb7-103">Modul CLR (CLR), úloha reprezentována aktuální upozorní [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance ukončuje a pokusí se korektně vypnout úlohu.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4fb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4fb7-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e4fb7-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e4fb7-105">Return Value</span></span>  
  
|<span data-ttu-id="e4fb7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4fb7-106">HRESULT</span></span>|<span data-ttu-id="e4fb7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e4fb7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4fb7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4fb7-108">S_OK</span></span>|<span data-ttu-id="e4fb7-109">`ExitTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="e4fb7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4fb7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4fb7-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4fb7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4fb7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4fb7-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-113">The call timed out.</span></span>|  
|<span data-ttu-id="e4fb7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4fb7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4fb7-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4fb7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4fb7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4fb7-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4fb7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4fb7-118">E_FAIL</span></span>|<span data-ttu-id="e4fb7-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4fb7-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4fb7-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4fb7-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4fb7-122">Remarks</span></span>  
 <span data-ttu-id="e4fb7-123">`ExitTask`se pokusí provést čisté vypnutí úlohy, způsobem, který je obdobou vlákno se odpojuje od nespravovaný typ knihovny.</span><span class="sxs-lookup"><span data-stu-id="e4fb7-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4fb7-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4fb7-124">Requirements</span></span>  
 <span data-ttu-id="e4fb7-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4fb7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4fb7-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4fb7-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4fb7-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4fb7-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4fb7-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4fb7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4fb7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4fb7-129">See Also</span></span>  
 [<span data-ttu-id="e4fb7-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4fb7-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e4fb7-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4fb7-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e4fb7-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4fb7-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e4fb7-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4fb7-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
