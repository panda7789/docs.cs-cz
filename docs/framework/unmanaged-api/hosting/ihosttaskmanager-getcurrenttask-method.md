---
title: IHostTaskManager::GetCurrentTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2436288e2f2f241cab15b16abf4df99c73caec25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093719"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="c5147-102">IHostTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="c5147-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="c5147-103">Získá ukazatel rozhraní k úkolu, který aktuálně spouští ve vlákně operačního systému, ze kterého je provedeno toto volání.</span><span class="sxs-lookup"><span data-stu-id="c5147-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5147-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5147-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5147-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5147-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="c5147-106">[out] Ukazatel na adresu [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, která reprezentuje aktuálně prováděné úlohy nebo hodnota null, pokud je aktuálně spuštěny žádné úlohy.</span><span class="sxs-lookup"><span data-stu-id="c5147-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5147-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c5147-107">Return Value</span></span>  
  
|<span data-ttu-id="c5147-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5147-108">HRESULT</span></span>|<span data-ttu-id="c5147-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c5147-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5147-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5147-110">S_OK</span></span>|`GetCurrentTask` <span data-ttu-id="c5147-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c5147-111">returned successfully.</span></span>|  
|<span data-ttu-id="c5147-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5147-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5147-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c5147-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5147-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5147-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5147-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c5147-115">The call timed out.</span></span>|  
|<span data-ttu-id="c5147-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5147-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5147-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c5147-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5147-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5147-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5147-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c5147-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5147-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5147-120">E_FAIL</span></span>|<span data-ttu-id="c5147-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c5147-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5147-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c5147-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5147-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5147-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c5147-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="c5147-124">HOST_E_INVALIDOPERATION</span></span>|`GetCurrentTask` <span data-ttu-id="c5147-125">byla volána pro vlákna operačního systému mimo ovládací prvek hostitele.</span><span class="sxs-lookup"><span data-stu-id="c5147-125">was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5147-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5147-126">Remarks</span></span>  
 <span data-ttu-id="c5147-127">Můžete také nastavit hostitele `pTask` parametr na hodnotu null pro úlohu, která se nezahájila zabránit vstupují do platformy CLR.</span><span class="sxs-lookup"><span data-stu-id="c5147-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5147-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5147-128">Requirements</span></span>  
 <span data-ttu-id="c5147-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5147-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5147-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5147-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5147-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5147-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c5147-132">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c5147-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5147-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5147-133">See also</span></span>

- [<span data-ttu-id="c5147-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5147-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c5147-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5147-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c5147-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5147-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c5147-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5147-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
