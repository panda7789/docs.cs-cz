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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a30ac0ab8c985af04709ddd8e8e5dd9bca776dcb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759089"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="0b379-102">ICLRSyncManager::DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="0b379-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="0b379-103">Požadavky, že modul CLR (CLR) zničit iterátor, který byl vytvořen voláním [iclrsyncmanager::createrwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="0b379-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b379-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b379-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b379-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b379-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="0b379-106">[in] Iterátor, který byl vytvořen pomocí volání `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="0b379-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b379-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0b379-107">Return Value</span></span>  
  
|<span data-ttu-id="0b379-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b379-108">HRESULT</span></span>|<span data-ttu-id="0b379-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0b379-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b379-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b379-110">S_OK</span></span>|<span data-ttu-id="0b379-111">`DeleteRWLockOwnerIterator` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0b379-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="0b379-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b379-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b379-113">Modul CLR nebyl načten do procesu, nebo je ve stavu, ve kterém nemůže spouštět spravovaný kód a úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0b379-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="0b379-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b379-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b379-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0b379-115">The call timed out.</span></span>|  
|<span data-ttu-id="0b379-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b379-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b379-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="0b379-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b379-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b379-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b379-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="0b379-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b379-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b379-120">E_FAIL</span></span>|<span data-ttu-id="0b379-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="0b379-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b379-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0b379-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b379-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b379-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b379-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b379-124">Remarks</span></span>  
 <span data-ttu-id="0b379-125">Tuto metodu můžete volat hostitele a `CreateRWLockOwnerIterator` zajistit, že jeho implementace dělení na vlákna zůstane synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="0b379-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b379-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b379-126">Requirements</span></span>  
 <span data-ttu-id="0b379-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b379-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b379-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b379-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b379-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b379-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b379-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b379-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b379-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b379-131">See also</span></span>

- [<span data-ttu-id="0b379-132">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b379-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0b379-133">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b379-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
