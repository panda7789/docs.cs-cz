---
title: IHostIoCompletionManager::Bind – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c03cdb9f9205676d17d6e18b9b2e074132ee26f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594769"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="e5f8a-102">IHostIoCompletionManager::Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="e5f8a-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="e5f8a-103">Vytvoří vazbu určený port dokončení vstupně-výstupních operací, který byl vytvořen v dřívějším volání [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5f8a-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5f8a-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5f8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5f8a-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="e5f8a-106">[in] Port dokončení vstupně-výstupních operací, ke kterému se vytvořit vazbu `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="e5f8a-107">Pokud hodnota `hPort` má hodnotu null, `hHandle` je vázán na výchozí port dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="e5f8a-108">[in] Popisovač operačního systému vytvořit vazbu na `hPort`.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5f8a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5f8a-109">Return Value</span></span>  
  
|<span data-ttu-id="e5f8a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5f8a-110">HRESULT</span></span>|<span data-ttu-id="e5f8a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e5f8a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5f8a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5f8a-112">S_OK</span></span>|<span data-ttu-id="e5f8a-113">`Bind` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="e5f8a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e5f8a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e5f8a-115">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e5f8a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e5f8a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e5f8a-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-117">The call timed out.</span></span>|  
|<span data-ttu-id="e5f8a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e5f8a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e5f8a-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e5f8a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e5f8a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e5f8a-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e5f8a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e5f8a-122">E_FAIL</span></span>|<span data-ttu-id="e5f8a-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e5f8a-124">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e5f8a-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5f8a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5f8a-126">Remarks</span></span>  
 <span data-ttu-id="e5f8a-127">Port dokončení vstupně-výstupních operací je vytvořena pomocí volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="e5f8a-128">Volání CLR `Bind` svázat popisovač na daný port.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5f8a-129">Po dokončení se požadavek na vstupně-výstupních operací, musí volat hostitele [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5f8a-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f8a-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5f8a-130">Requirements</span></span>  
 <span data-ttu-id="e5f8a-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5f8a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5f8a-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e5f8a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5f8a-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5f8a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5f8a-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5f8a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f8a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5f8a-135">See also</span></span>
- [<span data-ttu-id="e5f8a-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5f8a-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
