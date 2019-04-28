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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763604"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="b94d8-102">ICLRSyncManager::GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="b94d8-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="b94d8-103">Získá další [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která je blokována v aktuální zámku pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="b94d8-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b94d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b94d8-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b94d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b94d8-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="b94d8-106">[in] Iterátor, který byl vytvořen pomocí volání [createrwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="b94d8-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="b94d8-107">[out] Ukazatel na další `IHostTask` , který čeká na zámek, nebo hodnota null, pokud čekáte na žádné úlohy.</span><span class="sxs-lookup"><span data-stu-id="b94d8-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b94d8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b94d8-108">Return Value</span></span>  
  
|<span data-ttu-id="b94d8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b94d8-109">HRESULT</span></span>|<span data-ttu-id="b94d8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b94d8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b94d8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b94d8-111">S_OK</span></span>|<span data-ttu-id="b94d8-112">`GetRWLockOwnerNext` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b94d8-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="b94d8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b94d8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b94d8-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b94d8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b94d8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b94d8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b94d8-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b94d8-116">The call timed out.</span></span>|  
|<span data-ttu-id="b94d8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b94d8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b94d8-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="b94d8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b94d8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b94d8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b94d8-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="b94d8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b94d8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b94d8-121">E_FAIL</span></span>|<span data-ttu-id="b94d8-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="b94d8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b94d8-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="b94d8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b94d8-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b94d8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b94d8-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b94d8-125">Remarks</span></span>  
 <span data-ttu-id="b94d8-126">Pokud `ppOwnerHostTask` je nastavena na hodnotu null, byla ukončena iterace a měla by volat hostitele [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b94d8-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b94d8-127">Volání CLR `AddRef` na `IHostTask` ke kterému `ppOwnerHostTask` body zabránit tato úloha ukončení při hostitele obsahuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="b94d8-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="b94d8-128">Hostitel musí volat `Release` se sníží počet odkazů až po dokončení.</span><span class="sxs-lookup"><span data-stu-id="b94d8-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b94d8-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b94d8-129">Requirements</span></span>  
 <span data-ttu-id="b94d8-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b94d8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b94d8-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b94d8-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b94d8-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b94d8-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b94d8-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b94d8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94d8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b94d8-134">See also</span></span>

- [<span data-ttu-id="b94d8-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b94d8-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b94d8-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b94d8-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
