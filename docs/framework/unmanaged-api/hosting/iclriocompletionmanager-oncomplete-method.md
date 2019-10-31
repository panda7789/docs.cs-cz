---
title: ICLRIoCompletionManager::OnComplete – metoda
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: b44a71137e39130bb0fe4c303fdff62c76d38cbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141008"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="4338b-102">ICLRIoCompletionManager::OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="4338b-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="4338b-103">Upozorňuje modul CLR (Common Language Runtime) na stav vstupně-výstupních požadavků, který byl proveden pomocí volání metody [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4338b-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4338b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4338b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4338b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4338b-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="4338b-106">pro Hodnota HRESULT, která indikuje stav operace vazby.</span><span class="sxs-lookup"><span data-stu-id="4338b-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="4338b-107">S_OK znamená, že operace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="4338b-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="4338b-108">HOST_E_INTERRUPTED označuje, že volání bylo ukončeno před dokončením.</span><span class="sxs-lookup"><span data-stu-id="4338b-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="4338b-109">E_FAIL označuje, že došlo k neznámé, neobnovitelné, závažné chybě.</span><span class="sxs-lookup"><span data-stu-id="4338b-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="4338b-110">pro Počet bajtů přenesených během zpracování vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="4338b-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="4338b-111">pro Ukazatel na strukturu `OVERLAPPED`, která byla předána volání metody `IHostIoCompletionManager::Bind`.</span><span class="sxs-lookup"><span data-stu-id="4338b-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4338b-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4338b-112">Return Value</span></span>  
  
|<span data-ttu-id="4338b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4338b-113">HRESULT</span></span>|<span data-ttu-id="4338b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4338b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4338b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4338b-115">S_OK</span></span>|<span data-ttu-id="4338b-116">`OnComplete` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4338b-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="4338b-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4338b-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4338b-118">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4338b-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4338b-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4338b-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4338b-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4338b-120">The call timed out.</span></span>|  
|<span data-ttu-id="4338b-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4338b-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4338b-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="4338b-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4338b-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4338b-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4338b-124">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="4338b-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4338b-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4338b-125">E_FAIL</span></span>|<span data-ttu-id="4338b-126">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="4338b-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4338b-127">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="4338b-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4338b-128">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4338b-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4338b-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4338b-129">Remarks</span></span>  
 <span data-ttu-id="4338b-130">Pokud hostitel implementuje abstrakci dokončení vstupně-výstupních operací, CLR vytvoří požadavky na vstupně-výstupní operace prostřednictvím hostitele pomocí metod [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4338b-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="4338b-131">Hostitel pak zavolá metodu `OnComplete` a upozorní modul runtime na výsledek takových požadavků.</span><span class="sxs-lookup"><span data-stu-id="4338b-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4338b-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4338b-132">Requirements</span></span>  
 <span data-ttu-id="4338b-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4338b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4338b-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4338b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4338b-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4338b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4338b-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4338b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4338b-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4338b-137">See also</span></span>

- [<span data-ttu-id="4338b-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4338b-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4338b-139">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4338b-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="4338b-140">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4338b-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
