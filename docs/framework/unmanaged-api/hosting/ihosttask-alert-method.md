---
title: "IHostTask::Alert – metoda"
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
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10dc8b9894c6f5444ccfcfd17f749df1a3fb5d05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="3aca4-102">IHostTask::Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="3aca4-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="3aca4-103">Požadavky, že hostitel wake úlohu reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, takže úlohu můžete byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="3aca4-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aca4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aca4-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3aca4-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3aca4-105">Return Value</span></span>  
  
|<span data-ttu-id="3aca4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3aca4-106">HRESULT</span></span>|<span data-ttu-id="3aca4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3aca4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3aca4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3aca4-108">S_OK</span></span>|<span data-ttu-id="3aca4-109">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3aca4-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="3aca4-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3aca4-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3aca4-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3aca4-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3aca4-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3aca4-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3aca4-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3aca4-113">The call timed out.</span></span>|  
|<span data-ttu-id="3aca4-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3aca4-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3aca4-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="3aca4-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3aca4-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3aca4-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3aca4-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="3aca4-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3aca4-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3aca4-118">E_FAIL</span></span>|<span data-ttu-id="3aca4-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="3aca4-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3aca4-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3aca4-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3aca4-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3aca4-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3aca4-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3aca4-122">Remarks</span></span>  
 <span data-ttu-id="3aca4-123">Volání CLR `Alert` metoda při <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> je volána z uživatelského kódu, nebo když <xref:System.AppDomain> přidružené k aktuální <xref:System.Threading.Thread> ukončí.</span><span class="sxs-lookup"><span data-stu-id="3aca4-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="3aca4-124">Hostitel musí vracet okamžitě, protože při volání asynchronně.</span><span class="sxs-lookup"><span data-stu-id="3aca4-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="3aca4-125">Pokud hostitel nemůže výstrahy úloha okamžitě, musí probuzení při příštím přejde do stavu, ve kterém můžete generovat výstrahy.</span><span class="sxs-lookup"><span data-stu-id="3aca4-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3aca4-126">`Alert`ovlivňuje pouze ty úlohy, do kterých byla úspěšná modulu runtime [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnotu WAIT_ALERTABLE metody, jako [připojení](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="3aca4-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aca4-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3aca4-127">Requirements</span></span>  
 <span data-ttu-id="3aca4-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aca4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aca4-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3aca4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3aca4-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3aca4-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3aca4-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aca4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aca4-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3aca4-132">See Also</span></span>  
 [<span data-ttu-id="3aca4-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3aca4-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3aca4-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3aca4-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3aca4-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3aca4-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3aca4-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3aca4-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
