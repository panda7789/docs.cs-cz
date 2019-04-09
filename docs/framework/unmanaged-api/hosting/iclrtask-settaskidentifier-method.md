---
title: ICLRTask::SetTaskIdentifier – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abd8848ed54b26b66090e4865f9c3a0e5c4d20db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078314"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="8fc8c-102">ICLRTask::SetTaskIdentifier – metoda</span><span class="sxs-lookup"><span data-stu-id="8fc8c-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="8fc8c-103">Dá pokyn, modul CLR (CLR), která přidružit hodnota zadaného identifikátoru úlohy reprezentované aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fc8c-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fc8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fc8c-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="8fc8c-106">[in] Jedinečný identifikátor pro modul common language runtime pro přidružení k úkolu reprezentované aktuální `ICLRTask` instance.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fc8c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8fc8c-107">Return Value</span></span>  
  
|<span data-ttu-id="8fc8c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8fc8c-108">HRESULT</span></span>|<span data-ttu-id="8fc8c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8fc8c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8fc8c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8fc8c-110">S_OK</span></span>|`SetTaskIdentifier` <span data-ttu-id="8fc8c-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-111">returned successfully.</span></span>|  
|<span data-ttu-id="8fc8c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8fc8c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8fc8c-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8fc8c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8fc8c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8fc8c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-115">The call timed out.</span></span>|  
|<span data-ttu-id="8fc8c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8fc8c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8fc8c-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8fc8c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8fc8c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8fc8c-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8fc8c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8fc8c-120">E_FAIL</span></span>|<span data-ttu-id="8fc8c-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8fc8c-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8fc8c-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fc8c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fc8c-124">Remarks</span></span>  
 <span data-ttu-id="8fc8c-125">Hostitel možné přidružit identifikátor úlohu k integraci modulu CLR a hostitele v prostředí ladění.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="8fc8c-126">Identifikátor nemá žádný význam pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="8fc8c-127">Modul CLR podél předává do aplikace ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="8fc8c-128">Ladicí program můžete použít tento identifikátor pro přidružení k hostiteli zásobník volání zásobníku volání modulu CLR a povolit jejich odpovídajících trasovací informace na unified, při zobrazení v uživatelském rozhraní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="8fc8c-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc8c-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fc8c-129">Requirements</span></span>  
 <span data-ttu-id="8fc8c-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc8c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc8c-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8fc8c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8fc8c-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fc8c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8fc8c-133">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8fc8c-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8fc8c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fc8c-134">See also</span></span>

- [<span data-ttu-id="8fc8c-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fc8c-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8fc8c-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fc8c-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8fc8c-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fc8c-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8fc8c-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fc8c-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
