---
title: ICLRSyncManager::GetRWLockOwnerNext – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3efe80c0442e765274b309e39a79cc867676043
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169647"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="5c206-102">ICLRSyncManager::GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="5c206-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="5c206-103">Získá další [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která je blokována v aktuální zámku pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="5c206-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c206-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c206-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c206-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c206-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="5c206-106">[in] Iterátor, který byl vytvořen pomocí volání [createrwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c206-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="5c206-107">[out] Ukazatel na další `IHostTask` , který čeká na zámek, nebo hodnota null, pokud čekáte na žádné úlohy.</span><span class="sxs-lookup"><span data-stu-id="5c206-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c206-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c206-108">Return Value</span></span>  
  
|<span data-ttu-id="5c206-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c206-109">HRESULT</span></span>|<span data-ttu-id="5c206-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5c206-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c206-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c206-111">S_OK</span></span>|<span data-ttu-id="5c206-112">`GetRWLockOwnerNext` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5c206-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="5c206-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c206-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c206-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5c206-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c206-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c206-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c206-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5c206-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c206-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c206-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c206-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="5c206-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c206-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c206-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c206-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="5c206-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c206-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c206-121">E_FAIL</span></span>|<span data-ttu-id="5c206-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="5c206-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c206-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5c206-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c206-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c206-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c206-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c206-125">Remarks</span></span>  
 <span data-ttu-id="5c206-126">Pokud `ppOwnerHostTask` je nastavena na hodnotu null, byla ukončena iterace a měla by volat hostitele [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5c206-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c206-127">Volání CLR `AddRef` na `IHostTask` ke kterému `ppOwnerHostTask` body zabránit tato úloha ukončení při hostitele obsahuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="5c206-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="5c206-128">Hostitel musí volat `Release` se sníží počet odkazů až po dokončení.</span><span class="sxs-lookup"><span data-stu-id="5c206-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c206-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c206-129">Requirements</span></span>  
 <span data-ttu-id="5c206-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c206-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c206-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c206-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c206-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c206-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c206-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c206-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c206-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c206-134">See also</span></span>

- [<span data-ttu-id="5c206-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c206-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5c206-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c206-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
