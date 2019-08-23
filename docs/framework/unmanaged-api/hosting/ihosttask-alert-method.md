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
ms.openlocfilehash: 75b3fc0b1dde35e743e699d22c5766cab4cf0faf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964721"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="8ed5e-102">IHostTask::Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="8ed5e-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="8ed5e-103">Vyžádá, aby hostitel probudil úlohu reprezentovanou aktuální instancí [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , takže úlohu můžete zrušit.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ed5e-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8ed5e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8ed5e-105">Return Value</span></span>  
  
|<span data-ttu-id="8ed5e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ed5e-106">HRESULT</span></span>|<span data-ttu-id="8ed5e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8ed5e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ed5e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ed5e-108">S_OK</span></span>|<span data-ttu-id="8ed5e-109">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="8ed5e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ed5e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ed5e-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ed5e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ed5e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ed5e-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-113">The call timed out.</span></span>|  
|<span data-ttu-id="8ed5e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ed5e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ed5e-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ed5e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ed5e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ed5e-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ed5e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ed5e-118">E_FAIL</span></span>|<span data-ttu-id="8ed5e-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ed5e-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ed5e-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ed5e-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ed5e-122">Remarks</span></span>  
 <span data-ttu-id="8ed5e-123">CLR volá `Alert` metodu, pokud <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> je volána z uživatelského <xref:System.AppDomain> kódu nebo když je přidružena k aktuálnímu <xref:System.Threading.Thread> vypnutí.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="8ed5e-124">Hostitel musí vracet okamžitě, protože volání je provedeno asynchronně.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="8ed5e-125">Pokud hostitel nemůže úlohu okamžitě upozornit, musí se vystavit při příštím vstupu do stavu, ve kterém může být upozorněn.</span><span class="sxs-lookup"><span data-stu-id="8ed5e-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ed5e-126">`Alert`má vliv pouze na úlohy, ke kterým modul runtime předal hodnotu [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) WAIT_ALERTABLE do metod, jako je [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="8ed5e-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed5e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ed5e-127">Requirements</span></span>  
 <span data-ttu-id="8ed5e-128">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ed5e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed5e-129">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8ed5e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ed5e-130">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ed5e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ed5e-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed5e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed5e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ed5e-132">See also</span></span>

- [<span data-ttu-id="8ed5e-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ed5e-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8ed5e-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ed5e-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8ed5e-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ed5e-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8ed5e-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ed5e-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
