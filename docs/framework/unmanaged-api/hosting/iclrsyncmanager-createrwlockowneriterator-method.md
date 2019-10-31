---
title: ICLRSyncManager::CreateRWLockOwnerIterator – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: fcf034d93ceb7ececd5f6c71708d442f62a00f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092256"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="3cce0-102">ICLRSyncManager::CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="3cce0-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="3cce0-103">Požadavky, které modul CLR (Common Language Runtime) vytvoří iterátor, který může hostitel použít k určení sady úloh čekajících na zámek pro zápis čtenářů.</span><span class="sxs-lookup"><span data-stu-id="3cce0-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cce0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cce0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cce0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cce0-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="3cce0-106">pro Soubor cookie přidružený k požadovanému zámku zapisovače čtenářů</span><span class="sxs-lookup"><span data-stu-id="3cce0-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="3cce0-107">mimo Ukazatel na iterátor, který může být předán metodám [GetRWLockOwnerNext –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) a [DeleteRWLockOwnerIterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3cce0-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cce0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3cce0-108">Return Value</span></span>  
  
|<span data-ttu-id="3cce0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3cce0-109">HRESULT</span></span>|<span data-ttu-id="3cce0-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3cce0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3cce0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3cce0-111">S_OK</span></span>|<span data-ttu-id="3cce0-112">`CreateRWLockOwnerIterator` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3cce0-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="3cce0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3cce0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3cce0-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3cce0-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3cce0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3cce0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3cce0-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3cce0-116">The call timed out.</span></span>|  
|<span data-ttu-id="3cce0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3cce0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3cce0-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3cce0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3cce0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3cce0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3cce0-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3cce0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3cce0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3cce0-121">E_FAIL</span></span>|<span data-ttu-id="3cce0-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3cce0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3cce0-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3cce0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3cce0-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3cce0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3cce0-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3cce0-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3cce0-126">`CreateRWLockOwnerIterator` byla volána ve vlákně, které aktuálně používá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3cce0-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cce0-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cce0-127">Remarks</span></span>  
 <span data-ttu-id="3cce0-128">Hostitelé obvykle volají metody `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`a `GetRWLockOwnerNext` během zjišťování vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="3cce0-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="3cce0-129">Hostitel zodpovídá za to, že zámek zapisovače proti čtečce je stále platný, protože CLR nepokusí zachovat zámek čtečky zapisovače čtenářů.</span><span class="sxs-lookup"><span data-stu-id="3cce0-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="3cce0-130">K dispozici je několik strategií pro hostitele, aby se zajistila platnost zámku:</span><span class="sxs-lookup"><span data-stu-id="3cce0-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="3cce0-131">Hostitel může blokovat volání vydaných verzí na zámek zapisovače pro čtení (například [IHostSemaphore:: ReleaseSemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) a přitom zajistit, že tento blok nezpůsobí zablokování.</span><span class="sxs-lookup"><span data-stu-id="3cce0-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="3cce0-132">Hostitel může zablokovat ukončení čekání na objekt události přidružený k zámku zapisovače pro čtení a znovu zajistit, aby tento blok nezpůsoboval zablokování.</span><span class="sxs-lookup"><span data-stu-id="3cce0-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cce0-133">`CreateRWLockOwnerIterator` musí být volána pouze v vláknech, které aktuálně spouštějí nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3cce0-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cce0-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3cce0-134">Requirements</span></span>  
 <span data-ttu-id="3cce0-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cce0-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cce0-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3cce0-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cce0-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3cce0-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cce0-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cce0-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cce0-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cce0-139">See also</span></span>

- [<span data-ttu-id="3cce0-140">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cce0-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3cce0-141">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cce0-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
