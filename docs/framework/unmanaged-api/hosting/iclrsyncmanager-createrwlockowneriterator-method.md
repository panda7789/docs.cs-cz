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
ms.openlocfilehash: f8fde4905c41dffde90c6361b5a8cdffa15deb4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503962"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="790ec-102">ICLRSyncManager::CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="790ec-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="790ec-103">Požadavky, které modul CLR (Common Language Runtime) vytvoří iterátor, který může hostitel použít k určení sady úloh čekajících na zámek pro zápis čtenářů.</span><span class="sxs-lookup"><span data-stu-id="790ec-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="790ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="790ec-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="790ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="790ec-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="790ec-106">pro Soubor cookie přidružený k požadovanému zámku zapisovače čtenářů</span><span class="sxs-lookup"><span data-stu-id="790ec-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="790ec-107">mimo Ukazatel na iterátor, který může být předán metodám [GetRWLockOwnerNext –](iclrsyncmanager-getrwlockownernext-method.md) a [DeleteRWLockOwnerIterator –](iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="790ec-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="790ec-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="790ec-108">Return Value</span></span>  
  
|<span data-ttu-id="790ec-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="790ec-109">HRESULT</span></span>|<span data-ttu-id="790ec-110">Description</span><span class="sxs-lookup"><span data-stu-id="790ec-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="790ec-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="790ec-111">S_OK</span></span>|<span data-ttu-id="790ec-112">`CreateRWLockOwnerIterator`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="790ec-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="790ec-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="790ec-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="790ec-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="790ec-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="790ec-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="790ec-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="790ec-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="790ec-116">The call timed out.</span></span>|  
|<span data-ttu-id="790ec-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="790ec-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="790ec-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="790ec-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="790ec-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="790ec-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="790ec-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="790ec-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="790ec-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="790ec-121">E_FAIL</span></span>|<span data-ttu-id="790ec-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="790ec-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="790ec-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="790ec-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="790ec-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="790ec-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="790ec-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="790ec-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="790ec-126">`CreateRWLockOwnerIterator`bylo voláno ve vlákně, které aktuálně používá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="790ec-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="790ec-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="790ec-127">Remarks</span></span>  
 <span data-ttu-id="790ec-128">Hostitelé obvykle volají `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` metody, a `GetRWLockOwnerNext` během zjišťování vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="790ec-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="790ec-129">Hostitel zodpovídá za to, že zámek zapisovače proti čtečce je stále platný, protože CLR nepokusí zachovat zámek čtečky zapisovače čtenářů.</span><span class="sxs-lookup"><span data-stu-id="790ec-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="790ec-130">K dispozici je několik strategií pro hostitele, aby se zajistila platnost zámku:</span><span class="sxs-lookup"><span data-stu-id="790ec-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="790ec-131">Hostitel může blokovat volání vydaných verzí na zámek zapisovače pro čtení (například [IHostSemaphore:: ReleaseSemaphore –](ihostsemaphore-releasesemaphore-method.md)) a přitom zajistit, že tento blok nezpůsobí zablokování.</span><span class="sxs-lookup"><span data-stu-id="790ec-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="790ec-132">Hostitel může zablokovat ukončení čekání na objekt události přidružený k zámku zapisovače pro čtení a znovu zajistit, aby tento blok nezpůsoboval zablokování.</span><span class="sxs-lookup"><span data-stu-id="790ec-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="790ec-133">`CreateRWLockOwnerIterator`musí být volána pouze v vláknech, které aktuálně spouštějí nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="790ec-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="790ec-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="790ec-134">Requirements</span></span>  
 <span data-ttu-id="790ec-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="790ec-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="790ec-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="790ec-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="790ec-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="790ec-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="790ec-138">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="790ec-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="790ec-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="790ec-139">See also</span></span>

- [<span data-ttu-id="790ec-140">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="790ec-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="790ec-141">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="790ec-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
