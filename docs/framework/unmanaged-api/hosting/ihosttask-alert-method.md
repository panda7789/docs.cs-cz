---
title: "IHostTask::Alert – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Alert
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf48d3decd071c4c0f483476b885fc023b466f3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="05ad1-102">IHostTask::Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="05ad1-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="05ad1-103">Požadavky, že hostitel wake úlohu reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, takže úlohu můžete byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="05ad1-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ad1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05ad1-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05ad1-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05ad1-105">Return Value</span></span>  
  
|<span data-ttu-id="05ad1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05ad1-106">HRESULT</span></span>|<span data-ttu-id="05ad1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="05ad1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05ad1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="05ad1-108">S_OK</span></span>|<span data-ttu-id="05ad1-109">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="05ad1-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="05ad1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05ad1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05ad1-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="05ad1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05ad1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05ad1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05ad1-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="05ad1-113">The call timed out.</span></span>|  
|<span data-ttu-id="05ad1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05ad1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05ad1-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="05ad1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05ad1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05ad1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05ad1-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="05ad1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05ad1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05ad1-118">E_FAIL</span></span>|<span data-ttu-id="05ad1-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="05ad1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05ad1-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="05ad1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05ad1-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="05ad1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05ad1-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05ad1-122">Remarks</span></span>  
 <span data-ttu-id="05ad1-123">Volání CLR `Alert` metoda při <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> je volána z uživatelského kódu, nebo když <xref:System.AppDomain> přidružené k aktuální <xref:System.Threading.Thread> ukončí.</span><span class="sxs-lookup"><span data-stu-id="05ad1-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="05ad1-124">Hostitel musí vracet okamžitě, protože při volání asynchronně.</span><span class="sxs-lookup"><span data-stu-id="05ad1-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="05ad1-125">Pokud hostitel nemůže výstrahy úloha okamžitě, musí probuzení při příštím přejde do stavu, ve kterém můžete generovat výstrahy.</span><span class="sxs-lookup"><span data-stu-id="05ad1-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05ad1-126">`Alert`ovlivňuje pouze ty úlohy, do kterých byla úspěšná modulu runtime [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnotu WAIT_ALERTABLE metody, jako [připojení](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="05ad1-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ad1-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05ad1-127">Requirements</span></span>  
 <span data-ttu-id="05ad1-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ad1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ad1-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05ad1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05ad1-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05ad1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05ad1-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ad1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ad1-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="05ad1-132">See Also</span></span>  
 [<span data-ttu-id="05ad1-133">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ad1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="05ad1-134">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ad1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="05ad1-135">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ad1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="05ad1-136">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ad1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
