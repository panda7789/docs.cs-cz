---
title: IHostTaskManager::SetCLRTaskManager – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d18ccc18afa3bb3b7079139886c308882b2efc8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616646"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="8d89f-102">IHostTaskManager::SetCLRTaskManager – metoda</span><span class="sxs-lookup"><span data-stu-id="8d89f-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="8d89f-103">Poskytuje ukazatel rozhraní k hostiteli [iclrtaskmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implementován modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8d89f-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d89f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d89f-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d89f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d89f-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="8d89f-106">[in] Ukazatel `ICLRTaskManager` instance implementován modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="8d89f-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d89f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d89f-107">Return Value</span></span>  
  
|<span data-ttu-id="8d89f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d89f-108">HRESULT</span></span>|<span data-ttu-id="8d89f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8d89f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d89f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d89f-110">S_OK</span></span>|<span data-ttu-id="8d89f-111">`SetCLRTaskManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8d89f-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="8d89f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d89f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d89f-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8d89f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d89f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d89f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d89f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8d89f-115">The call timed out.</span></span>|  
|<span data-ttu-id="8d89f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d89f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d89f-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8d89f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d89f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d89f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d89f-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8d89f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d89f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d89f-120">E_FAIL</span></span>|<span data-ttu-id="8d89f-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8d89f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d89f-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8d89f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d89f-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d89f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d89f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d89f-124">Remarks</span></span>  
 <span data-ttu-id="8d89f-125">Modul runtime zavolá `SetCLRTaskManager` poskytnout ukazatele rozhraní na hostiteli `ICLRTaskManager` instance.</span><span class="sxs-lookup"><span data-stu-id="8d89f-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d89f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d89f-126">Requirements</span></span>  
 <span data-ttu-id="8d89f-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d89f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d89f-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d89f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d89f-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d89f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d89f-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d89f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d89f-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d89f-131">See also</span></span>
- [<span data-ttu-id="8d89f-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d89f-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8d89f-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d89f-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8d89f-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d89f-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8d89f-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d89f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
