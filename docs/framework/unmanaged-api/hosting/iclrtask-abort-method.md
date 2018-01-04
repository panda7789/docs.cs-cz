---
title: "ICLRTask::Abort – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Abort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e417e329b38c8f57dedf2926c0d6ff02a0170f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="db973-102">ICLRTask::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="db973-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="db973-103">Požadavky, modul CLR (CLR) přerušit úlohu, aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje.</span><span class="sxs-lookup"><span data-stu-id="db973-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db973-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db973-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="db973-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db973-105">Return Value</span></span>  
  
|<span data-ttu-id="db973-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db973-106">HRESULT</span></span>|<span data-ttu-id="db973-107">Popis</span><span class="sxs-lookup"><span data-stu-id="db973-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db973-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="db973-108">S_OK</span></span>|<span data-ttu-id="db973-109">`Abort`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="db973-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="db973-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db973-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db973-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="db973-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db973-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db973-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db973-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="db973-113">The call timed out.</span></span>|  
|<span data-ttu-id="db973-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db973-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db973-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="db973-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db973-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db973-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db973-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="db973-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db973-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db973-118">E_FAIL</span></span>|<span data-ttu-id="db973-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="db973-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db973-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="db973-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db973-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db973-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db973-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db973-122">Remarks</span></span>  
 <span data-ttu-id="db973-123">Vyvolá modulu CLR <xref:System.Threading.ThreadAbortException> při volání hostitele `Abort`.</span><span class="sxs-lookup"><span data-stu-id="db973-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="db973-124">Vrátí hned po inicializaci informace o výjimce, bez čekání na uživatelského kódu, například finalizační metody nebo zpracování mechanismů výjimek provést.</span><span class="sxs-lookup"><span data-stu-id="db973-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="db973-125">Volání `Abort` proto rychle vrátit.</span><span class="sxs-lookup"><span data-stu-id="db973-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db973-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db973-126">Requirements</span></span>  
 <span data-ttu-id="db973-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db973-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db973-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db973-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db973-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db973-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db973-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db973-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db973-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="db973-131">See Also</span></span>  
 [<span data-ttu-id="db973-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db973-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="db973-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db973-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="db973-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db973-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="db973-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db973-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
