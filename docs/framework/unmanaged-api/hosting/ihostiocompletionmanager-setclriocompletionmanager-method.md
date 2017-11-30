---
title: "IHostIoCompletionManager::SetCLRIoCompletionManager – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetCLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2447ba9cf3ee5968bde26b0a578cc06ef5c614c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="5f61f-102">IHostIoCompletionManager::SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="5f61f-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="5f61f-103">Poskytuje ukazatele rozhraní na hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementované common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5f61f-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f61f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f61f-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f61f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f61f-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="5f61f-106">[v] Ukazatele rozhraní k `ICLRIoCompletionManager` instance poskytované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5f61f-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f61f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5f61f-107">Return Value</span></span>  
  
|<span data-ttu-id="5f61f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f61f-108">HRESULT</span></span>|<span data-ttu-id="5f61f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5f61f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f61f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f61f-110">S_OK</span></span>|<span data-ttu-id="5f61f-111">`SetCLRIoCompletionManager`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="5f61f-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="5f61f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f61f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f61f-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5f61f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5f61f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5f61f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5f61f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5f61f-115">The call timed out.</span></span>|  
|<span data-ttu-id="5f61f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5f61f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5f61f-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="5f61f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5f61f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5f61f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5f61f-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="5f61f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5f61f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f61f-120">E_FAIL</span></span>|<span data-ttu-id="5f61f-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="5f61f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5f61f-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5f61f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5f61f-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5f61f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f61f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f61f-124">Remarks</span></span>  
 <span data-ttu-id="5f61f-125">Poté, co zavolal modulu CLR `SetCLRIoCompletionManager`, musí volat hostitele [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) upozornit modulu CLR, když požadavek vstupně-výstupní operace byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="5f61f-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f61f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f61f-126">Requirements</span></span>  
 <span data-ttu-id="5f61f-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f61f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f61f-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f61f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f61f-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f61f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f61f-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f61f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f61f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f61f-131">See Also</span></span>  
 [<span data-ttu-id="5f61f-132">Iclriocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f61f-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="5f61f-133">Ihostiocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f61f-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
