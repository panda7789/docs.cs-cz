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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e48292d1b0bfaa990cca1b290f769d96938d433
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759029"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="95e94-102">ICLRTask::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="95e94-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="95e94-103">Požadavky, že modul CLR (CLR) přerušit úlohu, která aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje.</span><span class="sxs-lookup"><span data-stu-id="95e94-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95e94-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="95e94-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95e94-105">Return Value</span></span>  
  
|<span data-ttu-id="95e94-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95e94-106">HRESULT</span></span>|<span data-ttu-id="95e94-107">Popis</span><span class="sxs-lookup"><span data-stu-id="95e94-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95e94-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="95e94-108">S_OK</span></span>|<span data-ttu-id="95e94-109">`Abort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="95e94-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="95e94-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95e94-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95e94-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="95e94-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95e94-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95e94-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95e94-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="95e94-113">The call timed out.</span></span>|  
|<span data-ttu-id="95e94-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95e94-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95e94-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="95e94-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95e94-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95e94-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95e94-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="95e94-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95e94-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95e94-118">E_FAIL</span></span>|<span data-ttu-id="95e94-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="95e94-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95e94-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="95e94-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95e94-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="95e94-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95e94-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95e94-122">Remarks</span></span>  
 <span data-ttu-id="95e94-123">Modul CLR vyvolá <xref:System.Threading.ThreadAbortException> když volá hostitele `Abort`.</span><span class="sxs-lookup"><span data-stu-id="95e94-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="95e94-124">Vrátí ihned po informace o výjimce inicializaci bez čekání na uživatelský kód, jako je například finalizační metoda nebo mechanismy, zpracování výjimek pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="95e94-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="95e94-125">Volání `Abort` tak rychle vrátit.</span><span class="sxs-lookup"><span data-stu-id="95e94-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95e94-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95e94-126">Requirements</span></span>  
 <span data-ttu-id="95e94-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95e94-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e94-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95e94-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95e94-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95e94-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95e94-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e94-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e94-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95e94-131">See also</span></span>

- [<span data-ttu-id="95e94-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95e94-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="95e94-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95e94-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="95e94-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95e94-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="95e94-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95e94-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
