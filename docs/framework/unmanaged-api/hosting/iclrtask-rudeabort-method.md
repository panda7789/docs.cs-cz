---
title: "ICLRTask::RudeAbort – metoda"
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
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f48de1fb44d978b1d9c8960c3e44c360b0801e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="12f1b-102">ICLRTask::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="12f1b-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="12f1b-103">Dá pokyn, modul CLR (CLR) na zrušení úlohy reprezentována aktuální [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance okamžitě a bezpodmínečně.</span><span class="sxs-lookup"><span data-stu-id="12f1b-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12f1b-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="12f1b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12f1b-105">Return Value</span></span>  
  
|<span data-ttu-id="12f1b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12f1b-106">HRESULT</span></span>|<span data-ttu-id="12f1b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="12f1b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12f1b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="12f1b-108">S_OK</span></span>|<span data-ttu-id="12f1b-109">`RudeAbort`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="12f1b-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="12f1b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12f1b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12f1b-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="12f1b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="12f1b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="12f1b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="12f1b-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="12f1b-113">The call timed out.</span></span>|  
|<span data-ttu-id="12f1b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="12f1b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="12f1b-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="12f1b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="12f1b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="12f1b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="12f1b-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="12f1b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="12f1b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12f1b-118">E_FAIL</span></span>|<span data-ttu-id="12f1b-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="12f1b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="12f1b-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="12f1b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="12f1b-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="12f1b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12f1b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12f1b-122">Remarks</span></span>  
 <span data-ttu-id="12f1b-123">Hostitel volá `RudeAbort` na zrušení úlohy okamžitě.</span><span class="sxs-lookup"><span data-stu-id="12f1b-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="12f1b-124">Finalizační metody a rutiny zpracování výjimek není zaručena bezpečnost pro provést.</span><span class="sxs-lookup"><span data-stu-id="12f1b-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f1b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12f1b-125">Requirements</span></span>  
 <span data-ttu-id="12f1b-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f1b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f1b-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="12f1b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12f1b-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12f1b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12f1b-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f1b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f1b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="12f1b-130">See Also</span></span>  
 [<span data-ttu-id="12f1b-131">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f1b-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="12f1b-132">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f1b-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="12f1b-133">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f1b-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="12f1b-134">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f1b-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
