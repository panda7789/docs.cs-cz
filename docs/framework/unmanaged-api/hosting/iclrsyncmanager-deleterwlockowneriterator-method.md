---
title: "ICLRSyncManager::DeleteRWLockOwnerIterator – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.DeleteRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3df37a9572c47ce4b4a5080f6aed3f307adba360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="bf5a2-102">ICLRSyncManager::DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="bf5a2-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="bf5a2-103">Požadavky, že modul CLR (CLR) destroy iterátor, který byl vytvořen volání [iclrsyncmanager::createrwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf5a2-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf5a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf5a2-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="bf5a2-106">[v] Iterator, který byl vytvořen pomocí volání `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf5a2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf5a2-107">Return Value</span></span>  
  
|<span data-ttu-id="bf5a2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf5a2-108">HRESULT</span></span>|<span data-ttu-id="bf5a2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bf5a2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf5a2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf5a2-110">S_OK</span></span>|<span data-ttu-id="bf5a2-111">`DeleteRWLockOwnerIterator`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="bf5a2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf5a2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf5a2-113">Modul CLR nebyla načtena do procesu, nebo je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="bf5a2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf5a2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf5a2-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-115">The call timed out.</span></span>|  
|<span data-ttu-id="bf5a2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf5a2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf5a2-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf5a2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf5a2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf5a2-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf5a2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf5a2-120">E_FAIL</span></span>|<span data-ttu-id="bf5a2-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf5a2-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf5a2-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf5a2-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf5a2-124">Remarks</span></span>  
 <span data-ttu-id="bf5a2-125">Tuto metodu můžete volat hostitele a `CreateRWLockOwnerIterator` aby zůstaly synchronizované jeho vláken provádění.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5a2-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf5a2-126">Requirements</span></span>  
 <span data-ttu-id="bf5a2-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf5a2-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf5a2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf5a2-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf5a2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf5a2-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf5a2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5a2-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf5a2-131">See Also</span></span>  
 [<span data-ttu-id="bf5a2-132">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf5a2-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="bf5a2-133">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf5a2-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
