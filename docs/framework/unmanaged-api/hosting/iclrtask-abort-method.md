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
ms.openlocfilehash: 76f216b12bccc950a34e2b23404ac305de519f4a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762468"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="9beb6-102">ICLRTask::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="9beb6-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="9beb6-103">Požadavky, které modul CLR (Common Language Runtime) přeruší úlohu, kterou představuje aktuální instance [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9beb6-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9beb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9beb6-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9beb6-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9beb6-105">Return Value</span></span>  
  
|<span data-ttu-id="9beb6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9beb6-106">HRESULT</span></span>|<span data-ttu-id="9beb6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9beb6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9beb6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9beb6-108">S_OK</span></span>|<span data-ttu-id="9beb6-109">`Abort`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="9beb6-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="9beb6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9beb6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9beb6-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9beb6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9beb6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9beb6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9beb6-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9beb6-113">The call timed out.</span></span>|  
|<span data-ttu-id="9beb6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9beb6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9beb6-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="9beb6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9beb6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9beb6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9beb6-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="9beb6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9beb6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9beb6-118">E_FAIL</span></span>|<span data-ttu-id="9beb6-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="9beb6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9beb6-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="9beb6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9beb6-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9beb6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9beb6-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9beb6-122">Remarks</span></span>  
 <span data-ttu-id="9beb6-123">CLR vyvolá <xref:System.Threading.ThreadAbortException> při volání hostitele `Abort` .</span><span class="sxs-lookup"><span data-stu-id="9beb6-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="9beb6-124">Vrátí hned po inicializaci informací o výjimce bez čekání na spuštění uživatelského kódu, jako jsou například finalizační metody nebo zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="9beb6-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="9beb6-125">Volání tak, aby se `Abort` vracela rychleji.</span><span class="sxs-lookup"><span data-stu-id="9beb6-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9beb6-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9beb6-126">Requirements</span></span>  
 <span data-ttu-id="9beb6-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9beb6-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9beb6-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9beb6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9beb6-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9beb6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9beb6-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9beb6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9beb6-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9beb6-131">See also</span></span>

- [<span data-ttu-id="9beb6-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9beb6-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9beb6-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9beb6-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9beb6-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9beb6-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9beb6-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9beb6-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
