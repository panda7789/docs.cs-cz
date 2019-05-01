---
title: IHostIoCompletionManager::CreateIoCompletionPort – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cf7978af4081b84a361e0a96a6c9da7180cb217
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951720"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="18359-102">IHostIoCompletionManager::CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="18359-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="18359-103">Požadavky, že hostitele, vytvořte nový port dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="18359-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18359-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18359-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18359-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18359-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="18359-106">[out] Ukazatel na popisovač do nově vytvořeného port dokončení vstupně-výstupních operací nebo 0 (nula), pokud nebylo možné vytvořit port.</span><span class="sxs-lookup"><span data-stu-id="18359-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18359-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18359-107">Return Value</span></span>  
  
|<span data-ttu-id="18359-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18359-108">HRESULT</span></span>|<span data-ttu-id="18359-109">Popis</span><span class="sxs-lookup"><span data-stu-id="18359-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18359-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="18359-110">S_OK</span></span>|<span data-ttu-id="18359-111">`CreateIoCompletionPort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="18359-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="18359-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18359-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18359-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="18359-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18359-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18359-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18359-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="18359-115">The call timed out.</span></span>|  
|<span data-ttu-id="18359-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18359-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18359-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="18359-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18359-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18359-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18359-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="18359-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18359-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18359-120">E_FAIL</span></span>|<span data-ttu-id="18359-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="18359-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18359-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="18359-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18359-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18359-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="18359-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="18359-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="18359-125">Nedostatek paměti bylo možné přidělit požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="18359-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18359-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18359-126">Remarks</span></span>  
 <span data-ttu-id="18359-127">Volání CLR `CreateIoCompletionPort` metoda požadavku, že hostitele, vytvořte nový port dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="18359-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="18359-128">Vytvoří vazbu mezi vstupně-výstupních operací na tento port přímo pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="18359-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="18359-129">Hostitel hlásí stav zpět do modulu CLR voláním [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="18359-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18359-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18359-130">Requirements</span></span>  
 <span data-ttu-id="18359-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18359-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18359-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18359-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18359-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18359-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18359-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18359-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18359-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18359-135">See also</span></span>

- [<span data-ttu-id="18359-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18359-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="18359-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18359-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
