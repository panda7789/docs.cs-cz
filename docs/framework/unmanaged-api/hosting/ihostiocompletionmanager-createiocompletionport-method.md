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
ms.openlocfilehash: 52e1dd05a87eaf06b5352d7c8d63c402a65d95ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439072"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="80e04-102">IHostIoCompletionManager::CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="80e04-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="80e04-103">Počet požadavků, hostitele vytvořit nový port dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="80e04-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80e04-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80e04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80e04-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="80e04-106">[out] Ukazatel na popisovač pro nově vytvořený portu dokončení vstupně-výstupních operací, nebo 0 (nula), pokud nebylo možné vytvořit port.</span><span class="sxs-lookup"><span data-stu-id="80e04-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80e04-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="80e04-107">Return Value</span></span>  
  
|<span data-ttu-id="80e04-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80e04-108">HRESULT</span></span>|<span data-ttu-id="80e04-109">Popis</span><span class="sxs-lookup"><span data-stu-id="80e04-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80e04-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="80e04-110">S_OK</span></span>|<span data-ttu-id="80e04-111">`CreateIoCompletionPort` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="80e04-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="80e04-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80e04-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80e04-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="80e04-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80e04-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80e04-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80e04-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="80e04-115">The call timed out.</span></span>|  
|<span data-ttu-id="80e04-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80e04-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80e04-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="80e04-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80e04-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80e04-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80e04-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="80e04-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80e04-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80e04-120">E_FAIL</span></span>|<span data-ttu-id="80e04-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="80e04-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80e04-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="80e04-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80e04-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="80e04-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="80e04-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="80e04-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="80e04-125">Nedostatek paměti nebylo k dispozici pro přidělení požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="80e04-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80e04-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80e04-126">Remarks</span></span>  
 <span data-ttu-id="80e04-127">Volání CLR `CreateIoCompletionPort` metoda k vyžádání, že hostitel vytvořit nový port dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="80e04-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="80e04-128">Vytvoří vazbu mezi vstupně-výstupních operací na tento port prostřednictvím volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="80e04-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="80e04-129">Hostitel oznámí stav zpět do modulu CLR voláním [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="80e04-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e04-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80e04-130">Requirements</span></span>  
 <span data-ttu-id="80e04-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e04-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e04-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80e04-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80e04-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80e04-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80e04-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e04-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e04-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="80e04-135">See Also</span></span>  
 [<span data-ttu-id="80e04-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80e04-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="80e04-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80e04-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
