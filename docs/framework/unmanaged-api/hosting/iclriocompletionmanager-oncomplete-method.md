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
ms.openlocfilehash: 4f2df623f9d191899390456a20e84a88f06f0b49
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592841"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="911e2-102">ICLRIoCompletionManager::OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="911e2-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="911e2-103">Upozorní common language runtime (CLR) stavu požadavku vstupně-výstupní operace, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="911e2-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="911e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="911e2-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="911e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="911e2-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="911e2-106">[in] Hodnota HRESULT, která označuje stav operace připojení.</span><span class="sxs-lookup"><span data-stu-id="911e2-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="911e2-107">S_OK označuje, že operace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="911e2-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="911e2-108">HOST_E_INTERRUPTED označuje, že volání ukončeno před dokončením.</span><span class="sxs-lookup"><span data-stu-id="911e2-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="911e2-109">E_FAIL označuje, že došlo k neznámé, Neopravitelná, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="911e2-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="911e2-110">[in] Počet bajtů přenesených během zpracování požadavku vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="911e2-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="911e2-111">[in] Ukazatel `OVERLAPPED` struktura, která byla předána volání `IHostIoCompletionManager::Bind` metody.</span><span class="sxs-lookup"><span data-stu-id="911e2-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="911e2-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="911e2-112">Return Value</span></span>  
  
|<span data-ttu-id="911e2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="911e2-113">HRESULT</span></span>|<span data-ttu-id="911e2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="911e2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="911e2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="911e2-115">S_OK</span></span>|<span data-ttu-id="911e2-116">`OnComplete` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="911e2-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="911e2-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="911e2-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="911e2-118">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="911e2-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="911e2-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="911e2-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="911e2-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="911e2-120">The call timed out.</span></span>|  
|<span data-ttu-id="911e2-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="911e2-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="911e2-122">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="911e2-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="911e2-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="911e2-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="911e2-124">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="911e2-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="911e2-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="911e2-125">E_FAIL</span></span>|<span data-ttu-id="911e2-126">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="911e2-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="911e2-127">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="911e2-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="911e2-128">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="911e2-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="911e2-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="911e2-129">Remarks</span></span>  
 <span data-ttu-id="911e2-130">Pokud hostitele implementuje abstrakci dokončení vstupně-výstupních operací, modul CLR provede vstupně-výstupní požadavky přes hostitele pomocí metod [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="911e2-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="911e2-131">Hostitel pak zavolá `OnComplete` metoda upozornit běhové prostředí výsledky těchto požadavků.</span><span class="sxs-lookup"><span data-stu-id="911e2-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="911e2-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="911e2-132">Requirements</span></span>  
 <span data-ttu-id="911e2-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="911e2-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="911e2-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="911e2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="911e2-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="911e2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="911e2-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="911e2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911e2-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="911e2-137">See also</span></span>

- [<span data-ttu-id="911e2-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="911e2-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="911e2-139">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="911e2-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="911e2-140">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="911e2-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
