---
title: IHostTaskManager::BeginThreadAffinity – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eb5c7ec85c0adb301fb722155caaed3c14e0e19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137719"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="17348-102">IHostTaskManager::BeginThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="17348-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="17348-103">Upozorní, že na hostitele, spravovaný kód je zadání období, ve kterém nesmí aktuální úlohy přesunout do jiného vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="17348-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17348-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17348-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="17348-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="17348-105">Return Value</span></span>  
  
|<span data-ttu-id="17348-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17348-106">HRESULT</span></span>|<span data-ttu-id="17348-107">Popis</span><span class="sxs-lookup"><span data-stu-id="17348-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17348-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="17348-108">S_OK</span></span>|<span data-ttu-id="17348-109">`BeginThreadAffinity` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="17348-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="17348-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17348-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17348-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="17348-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17348-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17348-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17348-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="17348-113">The call timed out.</span></span>|  
|<span data-ttu-id="17348-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17348-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17348-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="17348-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17348-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17348-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17348-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="17348-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17348-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17348-118">E_FAIL</span></span>|<span data-ttu-id="17348-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="17348-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17348-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="17348-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17348-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="17348-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17348-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17348-122">Remarks</span></span>  
 <span data-ttu-id="17348-123">CLR volá obvykle `IHostTaskManager::BeginThreadAffinity` v rámci volání <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="17348-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17348-124">Aktuální úloha nesmí přeplánovat, dokud je provedeno odpovídající volání [ihosttaskmanager::endthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="17348-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="17348-125">Úlohy lze přepnout navýšení kapacity, ale při přepnutí zpět, je třeba je přiřadit na stejném vlákně operačního systému, ze kterého byly přepnutí. Vnořená volání `BeginThreadAffinity` nemají žádný vliv, protože volání odkazuje na aktuální úlohu.</span><span class="sxs-lookup"><span data-stu-id="17348-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17348-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17348-126">Requirements</span></span>  
 <span data-ttu-id="17348-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17348-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17348-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="17348-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17348-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17348-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17348-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17348-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17348-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17348-131">See also</span></span>

- [<span data-ttu-id="17348-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17348-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="17348-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17348-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="17348-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17348-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="17348-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17348-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
