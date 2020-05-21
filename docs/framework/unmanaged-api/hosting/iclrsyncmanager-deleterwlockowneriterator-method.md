---
title: ICLRSyncManager::DeleteRWLockOwnerIterator – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: a4094a64d27072ce257341398bb49419bef9b8bb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763147"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="51a61-102">ICLRSyncManager::DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="51a61-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="51a61-103">Požaduje, aby modul CLR (Common Language Runtime) zničil iterátor, který byl vytvořen voláním metody [ICLRSyncManager:: CreateRWLockOwnerIterator –](iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="51a61-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51a61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51a61-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51a61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51a61-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="51a61-106">pro Iterátor, který byl vytvořen pomocí volání `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="51a61-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51a61-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51a61-107">Return Value</span></span>  
  
|<span data-ttu-id="51a61-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51a61-108">HRESULT</span></span>|<span data-ttu-id="51a61-109">Popis</span><span class="sxs-lookup"><span data-stu-id="51a61-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51a61-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51a61-110">S_OK</span></span>|<span data-ttu-id="51a61-111">`DeleteRWLockOwnerIterator`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="51a61-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="51a61-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51a61-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51a61-113">Modul CLR nebyl načten do procesu nebo je ve stavu, ve kterém nemůže spustit spravovaný kód, nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="51a61-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="51a61-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51a61-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51a61-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="51a61-115">The call timed out.</span></span>|  
|<span data-ttu-id="51a61-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51a61-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51a61-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="51a61-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51a61-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51a61-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51a61-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="51a61-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51a61-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51a61-120">E_FAIL</span></span>|<span data-ttu-id="51a61-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="51a61-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51a61-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="51a61-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51a61-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="51a61-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51a61-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51a61-124">Remarks</span></span>  
 <span data-ttu-id="51a61-125">Hostitel může zavolat tuto metodu a `CreateRWLockOwnerIterator` zajistit, aby její implementace vlákna zůstala synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="51a61-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51a61-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51a61-126">Requirements</span></span>  
 <span data-ttu-id="51a61-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51a61-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51a61-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="51a61-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51a61-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51a61-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51a61-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51a61-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a61-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="51a61-131">See also</span></span>

- [<span data-ttu-id="51a61-132">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51a61-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="51a61-133">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51a61-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
