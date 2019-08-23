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
ms.openlocfilehash: dbc38d9cf88f2449bbf689e4cf1b4101f47a0577
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943249"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="dd8d3-102">ICLRSyncManager::GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="dd8d3-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="dd8d3-103">Získá další instanci [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , která je blokována aktuálním zámkem zapisovače čtenář.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd8d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd8d3-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd8d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd8d3-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="dd8d3-106">pro Iterátor, který byl vytvořen pomocí volání [CreateRWLockOwnerIterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="dd8d3-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="dd8d3-107">mimo Ukazatel na další `IHostTask` , který čeká na zámek, nebo hodnotu null, pokud úloha nečeká.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd8d3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dd8d3-108">Return Value</span></span>  
  
|<span data-ttu-id="dd8d3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd8d3-109">HRESULT</span></span>|<span data-ttu-id="dd8d3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="dd8d3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd8d3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd8d3-111">S_OK</span></span>|<span data-ttu-id="dd8d3-112">`GetRWLockOwnerNext`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="dd8d3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd8d3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd8d3-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd8d3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd8d3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd8d3-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-116">The call timed out.</span></span>|  
|<span data-ttu-id="dd8d3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd8d3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd8d3-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd8d3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd8d3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd8d3-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd8d3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd8d3-121">E_FAIL</span></span>|<span data-ttu-id="dd8d3-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd8d3-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd8d3-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd8d3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd8d3-125">Remarks</span></span>  
 <span data-ttu-id="dd8d3-126">Pokud `ppOwnerHostTask` je nastaven na hodnotu null, iterace se ukončí a hostitel by měl volat metodu [DeleteRWLockOwnerIterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dd8d3-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd8d3-127">Rozhraní CLR volá `AddRef` na, `IHostTask` které `ppOwnerHostTask` odkazuje na to, aby se zabránilo ukončení této úlohy, zatímco hostitel obsahuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="dd8d3-128">Hostitel musí volat, `Release` aby po dokončení vyvolal počet odkazů.</span><span class="sxs-lookup"><span data-stu-id="dd8d3-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd8d3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd8d3-129">Requirements</span></span>  
 <span data-ttu-id="dd8d3-130">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd8d3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd8d3-131">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd8d3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd8d3-132">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd8d3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd8d3-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd8d3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8d3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd8d3-134">See also</span></span>

- [<span data-ttu-id="dd8d3-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd8d3-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="dd8d3-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd8d3-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
