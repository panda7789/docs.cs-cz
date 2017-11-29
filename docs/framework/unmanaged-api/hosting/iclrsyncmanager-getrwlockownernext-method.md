---
title: "ICLRSyncManager::GetRWLockOwnerNext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetRWLockOwnerNext
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8551a6981efd1005f5433c8c862623766bf838f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="0c7df-102">ICLRSyncManager::GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="0c7df-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="0c7df-103">Získá další [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, který je blokovaný na aktuální zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="0c7df-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c7df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c7df-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c7df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c7df-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="0c7df-106">[v] Iterator, který byl vytvořen pomocí volání [createrwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="0c7df-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="0c7df-107">[out] Ukazatel na další `IHostTask` , čeká na zámek, nebo hodnota null, pokud žádná úloha čeká.</span><span class="sxs-lookup"><span data-stu-id="0c7df-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c7df-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0c7df-108">Return Value</span></span>  
  
|<span data-ttu-id="0c7df-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c7df-109">HRESULT</span></span>|<span data-ttu-id="0c7df-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0c7df-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c7df-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c7df-111">S_OK</span></span>|<span data-ttu-id="0c7df-112">`GetRWLockOwnerNext`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0c7df-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="0c7df-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c7df-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c7df-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0c7df-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c7df-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c7df-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c7df-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0c7df-116">The call timed out.</span></span>|  
|<span data-ttu-id="0c7df-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c7df-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c7df-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0c7df-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c7df-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c7df-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c7df-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0c7df-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c7df-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c7df-121">E_FAIL</span></span>|<span data-ttu-id="0c7df-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0c7df-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c7df-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0c7df-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c7df-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c7df-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c7df-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c7df-125">Remarks</span></span>  
 <span data-ttu-id="0c7df-126">Pokud `ppOwnerHostTask` je nastaven na hodnotu null, ukončilo iterace a měla by volat hostitele [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="0c7df-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c7df-127">Volání CLR `AddRef` na `IHostTask` ke kterému `ppOwnerHostTask` body zabránit tato úloha ukončení při hostitele obsahuje ukazatele.</span><span class="sxs-lookup"><span data-stu-id="0c7df-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="0c7df-128">Hostitel musí volat `Release` se sníží počet odkazů až po dokončení.</span><span class="sxs-lookup"><span data-stu-id="0c7df-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c7df-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c7df-129">Requirements</span></span>  
 <span data-ttu-id="0c7df-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c7df-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c7df-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c7df-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c7df-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c7df-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c7df-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c7df-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7df-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c7df-134">See Also</span></span>  
 [<span data-ttu-id="0c7df-135">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c7df-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0c7df-136">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c7df-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
