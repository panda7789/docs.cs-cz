---
title: ICLRTask::LocksHeld – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f548d8b19a76aaccbae276dd63f091e4488690b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106805"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="10f67-102">ICLRTask::LocksHeld – metoda</span><span class="sxs-lookup"><span data-stu-id="10f67-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="10f67-103">Získá počet zámků právě načtený v úloze.</span><span class="sxs-lookup"><span data-stu-id="10f67-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10f67-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10f67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10f67-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="10f67-106">[out] Počet uzamčení na úlohu v okamžiku volání metody.</span><span class="sxs-lookup"><span data-stu-id="10f67-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10f67-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="10f67-107">Return Value</span></span>  
  
|<span data-ttu-id="10f67-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10f67-108">HRESULT</span></span>|<span data-ttu-id="10f67-109">Popis</span><span class="sxs-lookup"><span data-stu-id="10f67-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10f67-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10f67-110">S_OK</span></span>|<span data-ttu-id="10f67-111">`LocksHeld` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="10f67-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="10f67-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10f67-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10f67-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="10f67-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10f67-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10f67-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10f67-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="10f67-115">The call timed out.</span></span>|  
|<span data-ttu-id="10f67-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10f67-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10f67-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="10f67-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10f67-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10f67-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10f67-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="10f67-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10f67-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10f67-120">E_FAIL</span></span>|<span data-ttu-id="10f67-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="10f67-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10f67-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="10f67-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10f67-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10f67-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10f67-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10f67-124">Requirements</span></span>  
 <span data-ttu-id="10f67-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10f67-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10f67-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10f67-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10f67-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10f67-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10f67-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10f67-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f67-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10f67-129">See also</span></span>

- [<span data-ttu-id="10f67-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10f67-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="10f67-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10f67-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="10f67-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10f67-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="10f67-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10f67-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
