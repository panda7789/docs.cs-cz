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
ms.openlocfilehash: 9164e64c56a8a4ae908a3d06f878b399550703f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715397"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="230df-102">ICLRTask::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="230df-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="230df-103">Požadavky, že modul CLR (CLR) přerušit úlohu, která aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje.</span><span class="sxs-lookup"><span data-stu-id="230df-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="230df-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="230df-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="230df-105">Return Value</span></span>  
  
|<span data-ttu-id="230df-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="230df-106">HRESULT</span></span>|<span data-ttu-id="230df-107">Popis</span><span class="sxs-lookup"><span data-stu-id="230df-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="230df-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="230df-108">S_OK</span></span>|<span data-ttu-id="230df-109">`Abort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="230df-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="230df-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="230df-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="230df-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="230df-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="230df-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="230df-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="230df-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="230df-113">The call timed out.</span></span>|  
|<span data-ttu-id="230df-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="230df-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="230df-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="230df-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="230df-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="230df-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="230df-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="230df-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="230df-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="230df-118">E_FAIL</span></span>|<span data-ttu-id="230df-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="230df-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="230df-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="230df-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="230df-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="230df-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="230df-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="230df-122">Remarks</span></span>  
 <span data-ttu-id="230df-123">Modul CLR vyvolá <xref:System.Threading.ThreadAbortException> když volá hostitele `Abort`.</span><span class="sxs-lookup"><span data-stu-id="230df-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="230df-124">Vrátí ihned po informace o výjimce inicializaci bez čekání na uživatelský kód, jako je například finalizační metoda nebo mechanismy, zpracování výjimek pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="230df-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="230df-125">Volání `Abort` tak rychle vrátit.</span><span class="sxs-lookup"><span data-stu-id="230df-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="230df-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="230df-126">Requirements</span></span>  
 <span data-ttu-id="230df-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="230df-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="230df-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="230df-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="230df-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="230df-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="230df-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="230df-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230df-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="230df-131">See also</span></span>
- [<span data-ttu-id="230df-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="230df-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="230df-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="230df-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="230df-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="230df-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="230df-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="230df-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
