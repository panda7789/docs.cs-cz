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
ms.openlocfilehash: eda20543c28a7b97979463928ce307df9b830103
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436017"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="2bc9e-102">ICLRSyncManager::CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="2bc9e-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="2bc9e-103">Požadavky, které modul CLR (CLR) vytvořit iterace pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bc9e-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bc9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bc9e-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="2bc9e-106">[v] Soubor cookie přidružený zámek požadované čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="2bc9e-107">[out] Ukazatel na iterátor, který se dá předat do [getrwlockownernext –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) a [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bc9e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2bc9e-108">Return Value</span></span>  
  
|<span data-ttu-id="2bc9e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2bc9e-109">HRESULT</span></span>|<span data-ttu-id="2bc9e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2bc9e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2bc9e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2bc9e-111">S_OK</span></span>|<span data-ttu-id="2bc9e-112">`CreateRWLockOwnerIterator` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="2bc9e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2bc9e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2bc9e-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2bc9e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2bc9e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2bc9e-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-116">The call timed out.</span></span>|  
|<span data-ttu-id="2bc9e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2bc9e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2bc9e-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2bc9e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2bc9e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2bc9e-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2bc9e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2bc9e-121">E_FAIL</span></span>|<span data-ttu-id="2bc9e-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2bc9e-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2bc9e-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2bc9e-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2bc9e-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2bc9e-126">`CreateRWLockOwnerIterator` byla volána na vlákno, které běží v současné době spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bc9e-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bc9e-127">Remarks</span></span>  
 <span data-ttu-id="2bc9e-128">Hostitelé obvykle volání `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, a `GetRWLockOwnerNext` metod zjišťování zablokování.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="2bc9e-129">Hostitel je odpovědný za dodržování, čtení a zápis zámek je stále platný, protože modulu CLR nesnaží se zámek čtení a zápis zachování připojení.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="2bc9e-130">Několik strategií jsou k dispozici pro hostitele zajistit platnost zámku:</span><span class="sxs-lookup"><span data-stu-id="2bc9e-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="2bc9e-131">Hostitel může blokovat verzi volání na čtení a zápis zámek (například [ihostsemaphore::releasesemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) a zajistit, že tento blok nezpůsobí vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="2bc9e-132">Hostitel může blokovat ukončení z čekání na objekt události související s zámek čtení a zápis znovu zajistíte, že tento blok nezpůsobí vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bc9e-133">`CreateRWLockOwnerIterator` musí být volána pouze na vláken, které aktuálně provádějí nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2bc9e-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc9e-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bc9e-134">Requirements</span></span>  
 <span data-ttu-id="2bc9e-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bc9e-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc9e-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2bc9e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bc9e-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bc9e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bc9e-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bc9e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc9e-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bc9e-139">See Also</span></span>  
 [<span data-ttu-id="2bc9e-140">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bc9e-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="2bc9e-141">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bc9e-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
