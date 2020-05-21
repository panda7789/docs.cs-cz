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
ms.openlocfilehash: e5a8f69e66bb4b6373aea2c753bff9351bff8128
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762484"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="b4d5e-102">ICLRSyncManager::GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="b4d5e-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="b4d5e-103">Získá další instanci [IHostTask](ihosttask-interface.md) , která je blokována aktuálním zámkem zapisovače čtenář.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-103">Gets the next [IHostTask](ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4d5e-104">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4d5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4d5e-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="b4d5e-106">pro Iterátor, který byl vytvořen pomocí volání [CreateRWLockOwnerIterator –](iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="b4d5e-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="b4d5e-107">mimo Ukazatel na další `IHostTask` , který čeká na zámek, nebo hodnotu null, pokud úloha nečeká.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4d5e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4d5e-108">Return Value</span></span>  
  
|<span data-ttu-id="b4d5e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4d5e-109">HRESULT</span></span>|<span data-ttu-id="b4d5e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b4d5e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4d5e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4d5e-111">S_OK</span></span>|<span data-ttu-id="b4d5e-112">`GetRWLockOwnerNext`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="b4d5e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4d5e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4d5e-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b4d5e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4d5e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b4d5e-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-116">The call timed out.</span></span>|  
|<span data-ttu-id="b4d5e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4d5e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b4d5e-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b4d5e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b4d5e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b4d5e-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b4d5e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4d5e-121">E_FAIL</span></span>|<span data-ttu-id="b4d5e-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b4d5e-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b4d5e-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d5e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4d5e-125">Remarks</span></span>  
 <span data-ttu-id="b4d5e-126">Pokud `ppOwnerHostTask` je nastaven na hodnotu null, iterace se ukončí a hostitel by měl volat metodu [DeleteRWLockOwnerIterator –](iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b4d5e-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4d5e-127">Rozhraní CLR volá na `AddRef` , `IHostTask` které `ppOwnerHostTask` odkazuje na to, aby se zabránilo ukončení této úlohy, zatímco hostitel obsahuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="b4d5e-128">Hostitel musí volat `Release` , aby po dokončení vyvolal počet odkazů.</span><span class="sxs-lookup"><span data-stu-id="b4d5e-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d5e-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4d5e-129">Requirements</span></span>  
 <span data-ttu-id="b4d5e-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d5e-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d5e-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b4d5e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4d5e-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b4d5e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4d5e-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d5e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d5e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4d5e-134">See also</span></span>

- [<span data-ttu-id="b4d5e-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4d5e-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="b4d5e-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4d5e-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
