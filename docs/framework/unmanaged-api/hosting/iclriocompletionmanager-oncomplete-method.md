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
ms.openlocfilehash: 9c3d4674280bf5aa459fec2b195c3164c75c6c3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779623"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="1d90d-102">ICLRIoCompletionManager::OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="1d90d-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="1d90d-103">Upozorní common language runtime (CLR) stavu požadavku vstupně-výstupní operace, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1d90d-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d90d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d90d-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d90d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d90d-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="1d90d-106">[in] Hodnota HRESULT, která označuje stav operace připojení.</span><span class="sxs-lookup"><span data-stu-id="1d90d-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="1d90d-107">S_OK označuje, že operace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="1d90d-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="1d90d-108">HOST_E_INTERRUPTED označuje, že volání ukončeno před dokončením.</span><span class="sxs-lookup"><span data-stu-id="1d90d-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="1d90d-109">E_FAIL označuje, že došlo k neznámé, Neopravitelná, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="1d90d-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="1d90d-110">[in] Počet bajtů přenesených během zpracování požadavku vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="1d90d-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="1d90d-111">[in] Ukazatel `OVERLAPPED` struktura, která byla předána volání `IHostIoCompletionManager::Bind` metody.</span><span class="sxs-lookup"><span data-stu-id="1d90d-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d90d-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1d90d-112">Return Value</span></span>  
  
|<span data-ttu-id="1d90d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d90d-113">HRESULT</span></span>|<span data-ttu-id="1d90d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1d90d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d90d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d90d-115">S_OK</span></span>|<span data-ttu-id="1d90d-116">`OnComplete` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1d90d-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="1d90d-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d90d-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d90d-118">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1d90d-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d90d-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d90d-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d90d-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1d90d-120">The call timed out.</span></span>|  
|<span data-ttu-id="1d90d-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d90d-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d90d-122">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="1d90d-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d90d-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d90d-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d90d-124">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="1d90d-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d90d-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d90d-125">E_FAIL</span></span>|<span data-ttu-id="1d90d-126">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="1d90d-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d90d-127">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1d90d-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d90d-128">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1d90d-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d90d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d90d-129">Remarks</span></span>  
 <span data-ttu-id="1d90d-130">Pokud hostitele implementuje abstrakci dokončení vstupně-výstupních operací, modul CLR provede vstupně-výstupní požadavky přes hostitele pomocí metod [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1d90d-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="1d90d-131">Hostitel pak zavolá `OnComplete` metoda upozornit běhové prostředí výsledky těchto požadavků.</span><span class="sxs-lookup"><span data-stu-id="1d90d-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d90d-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d90d-132">Requirements</span></span>  
 <span data-ttu-id="1d90d-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d90d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d90d-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d90d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d90d-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1d90d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d90d-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d90d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d90d-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d90d-137">See also</span></span>

- [<span data-ttu-id="1d90d-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d90d-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1d90d-139">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d90d-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="1d90d-140">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d90d-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
