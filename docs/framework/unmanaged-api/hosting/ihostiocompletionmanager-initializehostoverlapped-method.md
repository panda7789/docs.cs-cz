---
title: IHostIoCompletionManager::InitializeHostOverlapped – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dea19a13cd2c741a24695b293ae1c8621ad5688
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796796"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="6a81d-102">IHostIoCompletionManager::InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="6a81d-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="6a81d-103">Poskytuje hostitele příležitost k inicializaci vlastních dat pro připojení k Win32 `OVERLAPPED` struktura, která se používá pro asynchronní vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="6a81d-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a81d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a81d-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a81d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a81d-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="6a81d-106">[in] Ukazatel na Win32 `OVERLAPPED` struktury mají být zahrnuty s žádostí o vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="6a81d-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a81d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a81d-107">Return Value</span></span>  
  
|<span data-ttu-id="6a81d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a81d-108">HRESULT</span></span>|<span data-ttu-id="6a81d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6a81d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a81d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a81d-110">S_OK</span></span>|<span data-ttu-id="6a81d-111">`InitializeHostOverlapped` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6a81d-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="6a81d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a81d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a81d-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6a81d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a81d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a81d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a81d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6a81d-115">The call timed out.</span></span>|  
|<span data-ttu-id="6a81d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a81d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a81d-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="6a81d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a81d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a81d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a81d-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="6a81d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a81d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a81d-120">E_FAIL</span></span>|<span data-ttu-id="6a81d-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="6a81d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a81d-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6a81d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a81d-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6a81d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6a81d-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6a81d-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6a81d-125">Nedostatek paměti bylo možné přidělit požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="6a81d-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a81d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a81d-126">Remarks</span></span>  
 <span data-ttu-id="6a81d-127">Použití funkce platformy Windows `OVERLAPPED` strukturu pro ukládání stavu pro asynchronní vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="6a81d-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="6a81d-128">Volání CLR `InitializeHostOverlapped` metoda poskytnout příležitosti pro připojení vlastních dat do hostitele `OVERLAPPED` instance.</span><span class="sxs-lookup"><span data-stu-id="6a81d-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a81d-129">Pokud chcete vrátit do začátku bloku svá vlastní data, musí hostitele nastavte posun velikosti `OVERLAPPED` strukturu (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="6a81d-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="6a81d-130">Návratová hodnota E_OUTOFMEMORY označuje, že hostitele se nepodařilo inicializovat svá vlastní data.</span><span class="sxs-lookup"><span data-stu-id="6a81d-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="6a81d-131">V takovém případě CLR nahlásí chybu a volání se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="6a81d-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a81d-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a81d-132">Requirements</span></span>  
 <span data-ttu-id="6a81d-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a81d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a81d-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6a81d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a81d-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a81d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a81d-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a81d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a81d-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a81d-137">See also</span></span>

- [<span data-ttu-id="6a81d-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a81d-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="6a81d-139">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6a81d-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="6a81d-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a81d-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
