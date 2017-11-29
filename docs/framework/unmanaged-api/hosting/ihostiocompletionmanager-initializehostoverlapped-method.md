---
title: "IHostIoCompletionManager::InitializeHostOverlapped – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.InitializeHostOverlapped
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26e8f9d963e6924a8c6abd73c3e025543c7d5b83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="965fe-102">IHostIoCompletionManager::InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="965fe-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="965fe-103">Poskytuje hostitele příležitost k inicializaci vlastní dat připojit k Win32 `OVERLAPPED` struktura, která se používá pro asynchronní vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="965fe-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="965fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="965fe-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="965fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="965fe-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="965fe-106">[v] Ukazatel na Win32 `OVERLAPPED` struktura bude zahrnuta v žádosti o vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="965fe-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="965fe-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="965fe-107">Return Value</span></span>  
  
|<span data-ttu-id="965fe-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="965fe-108">HRESULT</span></span>|<span data-ttu-id="965fe-109">Popis</span><span class="sxs-lookup"><span data-stu-id="965fe-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="965fe-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="965fe-110">S_OK</span></span>|<span data-ttu-id="965fe-111">`InitializeHostOverlapped`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="965fe-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="965fe-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="965fe-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="965fe-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="965fe-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="965fe-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="965fe-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="965fe-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="965fe-115">The call timed out.</span></span>|  
|<span data-ttu-id="965fe-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="965fe-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="965fe-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="965fe-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="965fe-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="965fe-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="965fe-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="965fe-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="965fe-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="965fe-120">E_FAIL</span></span>|<span data-ttu-id="965fe-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="965fe-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="965fe-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="965fe-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="965fe-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="965fe-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="965fe-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="965fe-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="965fe-125">Nedostatek paměti nebylo k dispozici pro přidělení požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="965fe-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="965fe-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="965fe-126">Remarks</span></span>  
 <span data-ttu-id="965fe-127">Použití funkce na platformu Windows `OVERLAPPED` struktura k uložení stavu pro asynchronní vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="965fe-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="965fe-128">Volání CLR `InitializeHostOverlapped` metoda poskytnout možnost připojit vlastní data pro hostitele `OVERLAPPED` instance.</span><span class="sxs-lookup"><span data-stu-id="965fe-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="965fe-129">Abyste se dostali na začátku bloku svá vlastní data, hostitelé musí nastavit posun na velikost `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="965fe-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="965fe-130">Vrácená hodnota E_OUTOFMEMORY označuje, že hostitele se nepodařilo inicializovat svá vlastní data.</span><span class="sxs-lookup"><span data-stu-id="965fe-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="965fe-131">V takovém případě modulu CLR nahlásí chybu a selže volání.</span><span class="sxs-lookup"><span data-stu-id="965fe-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="965fe-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="965fe-132">Requirements</span></span>  
 <span data-ttu-id="965fe-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="965fe-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="965fe-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="965fe-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="965fe-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="965fe-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="965fe-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="965fe-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="965fe-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="965fe-137">See Also</span></span>  
 [<span data-ttu-id="965fe-138">Iclriocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="965fe-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="965fe-139">Gethostoverlappedsize – metoda</span><span class="sxs-lookup"><span data-stu-id="965fe-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="965fe-140">Ihostiocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="965fe-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
