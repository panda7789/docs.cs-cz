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
ms.openlocfilehash: c3fa8aeebe529564c0ecc4a970f586fffc97ee05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133880"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="8d2dd-102">IHostIoCompletionManager::CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="8d2dd-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="8d2dd-103">Požaduje, aby hostitel vytvořil nový port pro dokončení vstupu/výstupu.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d2dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d2dd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d2dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d2dd-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="8d2dd-106">mimo Ukazatel na popisovač nově vytvořeného portu pro dokončení vstupně-výstupních operací nebo 0 (nula), pokud port nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d2dd-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d2dd-107">Return Value</span></span>  
  
|<span data-ttu-id="8d2dd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d2dd-108">HRESULT</span></span>|<span data-ttu-id="8d2dd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8d2dd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d2dd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d2dd-110">S_OK</span></span>|<span data-ttu-id="8d2dd-111">`CreateIoCompletionPort` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="8d2dd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d2dd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d2dd-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d2dd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d2dd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d2dd-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-115">The call timed out.</span></span>|  
|<span data-ttu-id="8d2dd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d2dd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d2dd-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d2dd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d2dd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d2dd-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d2dd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d2dd-120">E_FAIL</span></span>|<span data-ttu-id="8d2dd-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d2dd-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d2dd-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8d2dd-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8d2dd-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8d2dd-125">K přidělení požadovaného prostředku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d2dd-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d2dd-126">Remarks</span></span>  
 <span data-ttu-id="8d2dd-127">CLR volá metodu `CreateIoCompletionPort`, aby požádala tohoto hostitele o vytvoření nového portu pro dokončení vstupu/výstupu.</span><span class="sxs-lookup"><span data-stu-id="8d2dd-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="8d2dd-128">Váže vstupně-výstupní operace k tomuto portu prostřednictvím volání metody [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8d2dd-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="8d2dd-129">Hostitel hlásí stav zpět do CLR voláním [ICLRIoCompletionManager –:: doplňování](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="8d2dd-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d2dd-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d2dd-130">Requirements</span></span>  
 <span data-ttu-id="8d2dd-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d2dd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d2dd-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8d2dd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d2dd-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8d2dd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d2dd-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d2dd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2dd-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d2dd-135">See also</span></span>

- [<span data-ttu-id="8d2dd-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d2dd-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="8d2dd-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d2dd-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
