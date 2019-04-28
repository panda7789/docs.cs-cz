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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c742410da8e7dbce53b53978516ab94243455849
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763708"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="1344f-102">ICLRSyncManager::CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="1344f-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="1344f-103">Požadavky, které modul CLR (CLR) vytvořit iterátor pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="1344f-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1344f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1344f-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1344f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1344f-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="1344f-106">[in] Soubor cookie, přidružené k požadované čtení a zápis zámku.</span><span class="sxs-lookup"><span data-stu-id="1344f-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="1344f-107">[out] Ukazatel na iterátor, který lze předat [getrwlockownernext –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) a [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1344f-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1344f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1344f-108">Return Value</span></span>  
  
|<span data-ttu-id="1344f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1344f-109">HRESULT</span></span>|<span data-ttu-id="1344f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1344f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1344f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1344f-111">S_OK</span></span>|<span data-ttu-id="1344f-112">`CreateRWLockOwnerIterator` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1344f-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="1344f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1344f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1344f-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1344f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1344f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1344f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1344f-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1344f-116">The call timed out.</span></span>|  
|<span data-ttu-id="1344f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1344f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1344f-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="1344f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1344f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1344f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1344f-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="1344f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1344f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1344f-121">E_FAIL</span></span>|<span data-ttu-id="1344f-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="1344f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1344f-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1344f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1344f-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1344f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1344f-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="1344f-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="1344f-126">`CreateRWLockOwnerIterator` byla volána pro vlákno, které aktuálně běží spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1344f-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1344f-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1344f-127">Remarks</span></span>  
 <span data-ttu-id="1344f-128">Hostitelé obvykle volání `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, a `GetRWLockOwnerNext` metod rozpoznávání zablokování.</span><span class="sxs-lookup"><span data-stu-id="1344f-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="1344f-129">Hostitel zodpovídá za to, že zámek pro čtení a zápis je stále platný, protože modul CLR nesnaží se zachování zámku pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="1344f-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="1344f-130">Jsou dostupné pro hostitele, aby platnost zámku několik strategií:</span><span class="sxs-lookup"><span data-stu-id="1344f-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="1344f-131">Hostitel zablokovat volání uvolnění zámku pro čtení a zápis (například [ihostsemaphore::releasesemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) při zajištění, že tento blok způsobit zablokování.</span><span class="sxs-lookup"><span data-stu-id="1344f-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="1344f-132">Hostitel může blokovat výstupu z čekání na událost objekt přidružený k zámku pro čtení a zápis, znovu zajistit, že tento blok způsobit zablokování.</span><span class="sxs-lookup"><span data-stu-id="1344f-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1344f-133">`CreateRWLockOwnerIterator` musí být volána pouze na vlákna, která jsou aktuálně spuštěny nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1344f-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1344f-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1344f-134">Requirements</span></span>  
 <span data-ttu-id="1344f-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1344f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1344f-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1344f-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1344f-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1344f-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1344f-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1344f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1344f-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1344f-139">See also</span></span>

- [<span data-ttu-id="1344f-140">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1344f-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="1344f-141">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1344f-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
