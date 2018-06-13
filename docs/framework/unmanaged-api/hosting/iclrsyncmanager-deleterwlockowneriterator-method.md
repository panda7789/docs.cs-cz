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
ms.openlocfilehash: 5ee4a09902be093bdbfe0b367f4add35bdda571c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434064"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="dde26-102">ICLRSyncManager::DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="dde26-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="dde26-103">Požadavky, že modul CLR (CLR) destroy iterátor, který byl vytvořen volání [iclrsyncmanager::createrwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="dde26-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dde26-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dde26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dde26-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="dde26-106">[v] Iterator, který byl vytvořen pomocí volání `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="dde26-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dde26-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dde26-107">Return Value</span></span>  
  
|<span data-ttu-id="dde26-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dde26-108">HRESULT</span></span>|<span data-ttu-id="dde26-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dde26-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dde26-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dde26-110">S_OK</span></span>|<span data-ttu-id="dde26-111">`DeleteRWLockOwnerIterator` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="dde26-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="dde26-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dde26-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dde26-113">Modul CLR nebyla načtena do procesu, nebo je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dde26-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="dde26-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dde26-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dde26-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dde26-115">The call timed out.</span></span>|  
|<span data-ttu-id="dde26-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dde26-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dde26-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="dde26-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dde26-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dde26-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dde26-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="dde26-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dde26-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dde26-120">E_FAIL</span></span>|<span data-ttu-id="dde26-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="dde26-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dde26-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="dde26-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dde26-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dde26-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dde26-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dde26-124">Remarks</span></span>  
 <span data-ttu-id="dde26-125">Tuto metodu můžete volat hostitele a `CreateRWLockOwnerIterator` aby zůstaly synchronizované jeho vláken provádění.</span><span class="sxs-lookup"><span data-stu-id="dde26-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dde26-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dde26-126">Requirements</span></span>  
 <span data-ttu-id="dde26-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde26-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde26-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dde26-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dde26-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dde26-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dde26-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dde26-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde26-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="dde26-131">See Also</span></span>  
 [<span data-ttu-id="dde26-132">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dde26-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="dde26-133">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dde26-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
