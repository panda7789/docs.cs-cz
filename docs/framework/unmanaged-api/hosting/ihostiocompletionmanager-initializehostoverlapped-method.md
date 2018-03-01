---
title: "IHostIoCompletionManager::InitializeHostOverlapped – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b558d638e598ba6e3d0055e3a842976896e99d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="ecb97-102">IHostIoCompletionManager::InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="ecb97-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="ecb97-103">Poskytuje hostitele příležitost k inicializaci vlastní dat připojit k Win32 `OVERLAPPED` struktura, která se používá pro asynchronní vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="ecb97-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecb97-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecb97-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecb97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecb97-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="ecb97-106">[v] Ukazatel na Win32 `OVERLAPPED` struktura bude zahrnuta v žádosti o vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="ecb97-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecb97-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ecb97-107">Return Value</span></span>  
  
|<span data-ttu-id="ecb97-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecb97-108">HRESULT</span></span>|<span data-ttu-id="ecb97-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ecb97-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecb97-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecb97-110">S_OK</span></span>|<span data-ttu-id="ecb97-111">`InitializeHostOverlapped`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ecb97-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="ecb97-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecb97-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecb97-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ecb97-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecb97-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecb97-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecb97-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ecb97-115">The call timed out.</span></span>|  
|<span data-ttu-id="ecb97-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecb97-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecb97-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ecb97-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecb97-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecb97-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecb97-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ecb97-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecb97-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecb97-120">E_FAIL</span></span>|<span data-ttu-id="ecb97-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ecb97-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecb97-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ecb97-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecb97-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecb97-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ecb97-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ecb97-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ecb97-125">Nedostatek paměti nebylo k dispozici pro přidělení požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="ecb97-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecb97-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecb97-126">Remarks</span></span>  
 <span data-ttu-id="ecb97-127">Použití funkce na platformu Windows `OVERLAPPED` struktura k uložení stavu pro asynchronní vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="ecb97-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="ecb97-128">Volání CLR `InitializeHostOverlapped` metoda poskytnout možnost připojit vlastní data pro hostitele `OVERLAPPED` instance.</span><span class="sxs-lookup"><span data-stu-id="ecb97-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecb97-129">Abyste se dostali na začátku bloku svá vlastní data, hostitelé musí nastavit posun na velikost `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="ecb97-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="ecb97-130">Vrácená hodnota E_OUTOFMEMORY označuje, že hostitele se nepodařilo inicializovat svá vlastní data.</span><span class="sxs-lookup"><span data-stu-id="ecb97-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="ecb97-131">V takovém případě modulu CLR nahlásí chybu a selže volání.</span><span class="sxs-lookup"><span data-stu-id="ecb97-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecb97-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecb97-132">Requirements</span></span>  
 <span data-ttu-id="ecb97-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecb97-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecb97-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ecb97-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecb97-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecb97-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecb97-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecb97-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb97-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecb97-137">See Also</span></span>  
 [<span data-ttu-id="ecb97-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecb97-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="ecb97-139">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="ecb97-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="ecb97-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecb97-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
