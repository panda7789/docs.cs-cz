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
ms.openlocfilehash: 7c157cf27d2fe86288024a6c35e6dcbea3c46347
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133107"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="b9c4b-102">IHostTaskManager::BeginThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="b9c4b-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="b9c4b-103">Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém se aktuální úloha nesmí přesunout do jiného vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9c4b-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b9c4b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9c4b-105">Return Value</span></span>  
  
|<span data-ttu-id="b9c4b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9c4b-106">HRESULT</span></span>|<span data-ttu-id="b9c4b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b9c4b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9c4b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9c4b-108">S_OK</span></span>|<span data-ttu-id="b9c4b-109">`BeginThreadAffinity` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="b9c4b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9c4b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9c4b-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9c4b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9c4b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9c4b-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-113">The call timed out.</span></span>|  
|<span data-ttu-id="b9c4b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9c4b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9c4b-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9c4b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9c4b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9c4b-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9c4b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9c4b-118">E_FAIL</span></span>|<span data-ttu-id="b9c4b-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9c4b-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9c4b-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9c4b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9c4b-122">Remarks</span></span>  
 <span data-ttu-id="b9c4b-123">CLR obvykle volá `IHostTaskManager::BeginThreadAffinity` v kontextu volání <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b9c4b-124">Aktuální úlohu nesmí být přeplánována, dokud nebude provedeno odpovídající volání [IHostTaskManager:: EndThreadAffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="b9c4b-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="b9c4b-125">Úlohy je možné přepnout, ale pokud jsou znovu přepnuty, musí být přiřazeny ke stejnému vláknu operačního systému, ze kterého byly přepnuty. Vnořené volání `BeginThreadAffinity` nemají žádný účinek, protože volání odkazuje na aktuální úlohu.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c4b-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9c4b-126">Requirements</span></span>  
 <span data-ttu-id="b9c4b-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9c4b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c4b-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b9c4b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9c4b-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9c4b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9c4b-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9c4b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c4b-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9c4b-131">See also</span></span>

- [<span data-ttu-id="b9c4b-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9c4b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b9c4b-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9c4b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b9c4b-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9c4b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b9c4b-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9c4b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
