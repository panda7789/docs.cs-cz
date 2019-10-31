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
ms.openlocfilehash: b2fc1d6c45eb72410ccfa1071064aa1a31ae46e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121408"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="c9f87-102">IHostTask::Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="c9f87-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="c9f87-103">Vyžádá, aby hostitel probudil úlohu reprezentovanou aktuální instancí [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , takže úlohu můžete zrušit.</span><span class="sxs-lookup"><span data-stu-id="c9f87-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9f87-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c9f87-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c9f87-105">Return Value</span></span>  
  
|<span data-ttu-id="c9f87-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9f87-106">HRESULT</span></span>|<span data-ttu-id="c9f87-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c9f87-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9f87-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9f87-108">S_OK</span></span>|<span data-ttu-id="c9f87-109">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c9f87-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="c9f87-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9f87-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9f87-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c9f87-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9f87-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9f87-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9f87-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c9f87-113">The call timed out.</span></span>|  
|<span data-ttu-id="c9f87-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9f87-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9f87-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c9f87-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9f87-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9f87-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9f87-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="c9f87-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9f87-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9f87-118">E_FAIL</span></span>|<span data-ttu-id="c9f87-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c9f87-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9f87-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c9f87-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9f87-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9f87-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9f87-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9f87-122">Remarks</span></span>  
 <span data-ttu-id="c9f87-123">Modul CLR volá metodu `Alert`, pokud je <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> volána z uživatelského kódu nebo když <xref:System.AppDomain> přidružená k aktuálnímu <xref:System.Threading.Thread> ukončena.</span><span class="sxs-lookup"><span data-stu-id="c9f87-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="c9f87-124">Hostitel musí vracet okamžitě, protože volání je provedeno asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c9f87-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="c9f87-125">Pokud hostitel nemůže úlohu okamžitě upozornit, musí se vystavit při příštím vstupu do stavu, ve kterém může být upozorněn.</span><span class="sxs-lookup"><span data-stu-id="c9f87-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9f87-126">`Alert` ovlivňuje pouze ty úlohy, na které modul runtime předal hodnotu [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) WAIT_ALERTABLE do metod, jako je [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="c9f87-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f87-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9f87-127">Requirements</span></span>  
 <span data-ttu-id="c9f87-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f87-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f87-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9f87-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9f87-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c9f87-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9f87-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f87-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f87-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9f87-132">See also</span></span>

- [<span data-ttu-id="c9f87-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9f87-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c9f87-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9f87-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c9f87-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9f87-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c9f87-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9f87-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
