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
ms.openlocfilehash: 57efd4f29ba7e28adf1af03030d7f83eb32c1c2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139773"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="41a56-102">ICLRTask::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="41a56-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="41a56-103">Požadavky, že modul CLR (CLR) přerušit úlohu, která aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje.</span><span class="sxs-lookup"><span data-stu-id="41a56-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41a56-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="41a56-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="41a56-105">Return Value</span></span>  
  
|<span data-ttu-id="41a56-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41a56-106">HRESULT</span></span>|<span data-ttu-id="41a56-107">Popis</span><span class="sxs-lookup"><span data-stu-id="41a56-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41a56-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="41a56-108">S_OK</span></span>|`Abort` <span data-ttu-id="41a56-109">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="41a56-109">returned successfully.</span></span>|  
|<span data-ttu-id="41a56-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41a56-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41a56-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="41a56-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41a56-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41a56-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41a56-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="41a56-113">The call timed out.</span></span>|  
|<span data-ttu-id="41a56-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41a56-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41a56-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="41a56-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41a56-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41a56-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41a56-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="41a56-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41a56-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41a56-118">E_FAIL</span></span>|<span data-ttu-id="41a56-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="41a56-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41a56-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="41a56-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41a56-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="41a56-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41a56-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41a56-122">Remarks</span></span>  
 <span data-ttu-id="41a56-123">Modul CLR vyvolá <xref:System.Threading.ThreadAbortException> když volá hostitele `Abort`.</span><span class="sxs-lookup"><span data-stu-id="41a56-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="41a56-124">Vrátí ihned po informace o výjimce inicializaci bez čekání na uživatelský kód, jako je například finalizační metoda nebo mechanismy, zpracování výjimek pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="41a56-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="41a56-125">Volání `Abort` tak rychle vrátit.</span><span class="sxs-lookup"><span data-stu-id="41a56-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41a56-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41a56-126">Requirements</span></span>  
 <span data-ttu-id="41a56-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41a56-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41a56-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41a56-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41a56-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41a56-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="41a56-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="41a56-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="41a56-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41a56-131">See also</span></span>

- [<span data-ttu-id="41a56-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41a56-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="41a56-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41a56-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="41a56-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41a56-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="41a56-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41a56-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
