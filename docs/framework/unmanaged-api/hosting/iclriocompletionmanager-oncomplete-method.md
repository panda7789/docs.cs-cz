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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c11fa66ed583df93accc8ff1e5e95164d4de659d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434451"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="bac42-102">ICLRIoCompletionManager::OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="bac42-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="bac42-103">Modul CLR (CLR) upozorní stavu požadavek vstupně-výstupních operací, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="bac42-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bac42-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bac42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bac42-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="bac42-106">[v] Hodnota HRESULT, které uvádí stav operace vazby.</span><span class="sxs-lookup"><span data-stu-id="bac42-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
-   <span data-ttu-id="bac42-107">S_OK označuje, že operace úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="bac42-107">S_OK indicates that the operation completed successfully.</span></span>  
  
-   <span data-ttu-id="bac42-108">HOST_E_INTERRUPTED označuje, že volání ukončeno před dokončením.</span><span class="sxs-lookup"><span data-stu-id="bac42-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
-   <span data-ttu-id="bac42-109">E_FAIL označuje, že došlo k neznámé, neopravitelné, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="bac42-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="bac42-110">[v] Počet bajtů přenesených během zpracování požadavku vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="bac42-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="bac42-111">[v] Ukazatel `OVERLAPPED` struktura, která byla předána volání `IHostIoCompletionManager::Bind` metoda.</span><span class="sxs-lookup"><span data-stu-id="bac42-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bac42-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bac42-112">Return Value</span></span>  
  
|<span data-ttu-id="bac42-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bac42-113">HRESULT</span></span>|<span data-ttu-id="bac42-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bac42-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bac42-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bac42-115">S_OK</span></span>|<span data-ttu-id="bac42-116">`OnComplete` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="bac42-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="bac42-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bac42-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bac42-118">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="bac42-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bac42-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bac42-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bac42-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="bac42-120">The call timed out.</span></span>|  
|<span data-ttu-id="bac42-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bac42-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bac42-122">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="bac42-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bac42-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bac42-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bac42-124">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="bac42-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bac42-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bac42-125">E_FAIL</span></span>|<span data-ttu-id="bac42-126">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="bac42-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bac42-127">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="bac42-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bac42-128">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bac42-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bac42-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bac42-129">Remarks</span></span>  
 <span data-ttu-id="bac42-130">Pokud se hostitel implementuje abstrakci dokončení vstupně-výstupních operací, modulu CLR provede vstupně-výstupní požadavky přes hostitele pomocí metody [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bac42-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="bac42-131">Hostitel pak zavolá `OnComplete` metoda upozornit běhové prostředí na výsledek takových žádostí.</span><span class="sxs-lookup"><span data-stu-id="bac42-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac42-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bac42-132">Requirements</span></span>  
 <span data-ttu-id="bac42-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac42-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac42-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bac42-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bac42-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bac42-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bac42-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac42-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac42-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="bac42-137">See Also</span></span>  
 [<span data-ttu-id="bac42-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bac42-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="bac42-139">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bac42-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="bac42-140">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bac42-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
