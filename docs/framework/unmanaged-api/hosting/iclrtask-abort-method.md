---
title: ICLRTask::Abort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
ms.openlocfilehash: 026d4c14abed030b80e8e1b3f8363fbd59ac05e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124908"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="0e188-102">ICLRTask::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="0e188-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="0e188-103">Požadavky, které modul CLR (Common Language Runtime) přeruší úlohu, kterou představuje aktuální instance [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0e188-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e188-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e188-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0e188-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0e188-105">Return Value</span></span>  
  
|<span data-ttu-id="0e188-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e188-106">HRESULT</span></span>|<span data-ttu-id="0e188-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0e188-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e188-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e188-108">S_OK</span></span>|<span data-ttu-id="0e188-109">`Abort` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0e188-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="0e188-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e188-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e188-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0e188-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e188-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e188-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e188-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0e188-113">The call timed out.</span></span>|  
|<span data-ttu-id="0e188-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e188-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e188-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0e188-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e188-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e188-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e188-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0e188-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e188-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e188-118">E_FAIL</span></span>|<span data-ttu-id="0e188-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0e188-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e188-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0e188-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e188-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0e188-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e188-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e188-122">Remarks</span></span>  
 <span data-ttu-id="0e188-123">CLR vyvolá <xref:System.Threading.ThreadAbortException>, když hostitel volá `Abort`.</span><span class="sxs-lookup"><span data-stu-id="0e188-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="0e188-124">Vrátí hned po inicializaci informací o výjimce bez čekání na spuštění uživatelského kódu, jako jsou například finalizační metody nebo zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="0e188-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="0e188-125">Volání `Abort` tak, aby se vrátila rychle.</span><span class="sxs-lookup"><span data-stu-id="0e188-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e188-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e188-126">Requirements</span></span>  
 <span data-ttu-id="0e188-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e188-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e188-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e188-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e188-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0e188-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e188-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e188-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e188-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e188-131">See also</span></span>

- [<span data-ttu-id="0e188-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e188-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0e188-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e188-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0e188-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e188-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0e188-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e188-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
