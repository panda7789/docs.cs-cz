---
title: IHostTask::Alert – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a5e3b82645456ffa574f63931abbf60a2194540
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764533"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="c8d8d-102">IHostTask::Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="c8d8d-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="c8d8d-103">Požadavky, že hostitel probuzení úloh reprezentovaný aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, tak můžete přeruší úlohu.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8d8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8d8d-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c8d8d-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c8d8d-105">Return Value</span></span>  
  
|<span data-ttu-id="c8d8d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8d8d-106">HRESULT</span></span>|<span data-ttu-id="c8d8d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c8d8d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8d8d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8d8d-108">S_OK</span></span>|<span data-ttu-id="c8d8d-109">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="c8d8d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8d8d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8d8d-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8d8d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8d8d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8d8d-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-113">The call timed out.</span></span>|  
|<span data-ttu-id="c8d8d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8d8d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8d8d-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8d8d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8d8d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8d8d-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8d8d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8d8d-118">E_FAIL</span></span>|<span data-ttu-id="c8d8d-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8d8d-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8d8d-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8d8d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8d8d-122">Remarks</span></span>  
 <span data-ttu-id="c8d8d-123">Volání CLR `Alert` metoda při <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> je volání z uživatelského kódu, nebo když <xref:System.AppDomain> spojené s aktuálním <xref:System.Threading.Thread> vypne.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="c8d8d-124">Hostitel musí vracet okamžitě, protože volání se provádí asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="c8d8d-125">Pokud hostitele nelze okamžitě upozorní úkolu, musí probuzení při příštím přešel do stavu, ve kterém můžete být upozorněni.</span><span class="sxs-lookup"><span data-stu-id="c8d8d-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8d8d-126">`Alert` ovlivňuje pouze úlohy, pro které modul runtime uplynutí [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnotu WAIT_ALERTABLE metody jako [připojit](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="c8d8d-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8d8d-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8d8d-127">Requirements</span></span>  
 <span data-ttu-id="c8d8d-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8d8d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8d8d-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8d8d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8d8d-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8d8d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8d8d-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8d8d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d8d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8d8d-132">See also</span></span>

- [<span data-ttu-id="c8d8d-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8d8d-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c8d8d-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8d8d-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c8d8d-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8d8d-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c8d8d-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8d8d-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
