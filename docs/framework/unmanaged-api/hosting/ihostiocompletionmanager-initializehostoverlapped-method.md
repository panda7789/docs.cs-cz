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
ms.openlocfilehash: ac7014962b99ac167e8192c13b2bae5ca92470f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948514"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="3e471-102">IHostIoCompletionManager::InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="3e471-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="3e471-103">Poskytuje hostiteli možnost inicializovat jakákoli vlastní data pro připojení ke struktuře Win32 `OVERLAPPED` , která se používá pro asynchronní vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="3e471-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e471-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e471-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e471-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e471-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="3e471-106">pro Ukazatel na strukturu Win32 `OVERLAPPED` , který se má zahrnout do vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="3e471-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e471-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e471-107">Return Value</span></span>  
  
|<span data-ttu-id="3e471-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e471-108">HRESULT</span></span>|<span data-ttu-id="3e471-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3e471-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e471-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e471-110">S_OK</span></span>|<span data-ttu-id="3e471-111">`InitializeHostOverlapped`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="3e471-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="3e471-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e471-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e471-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3e471-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e471-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e471-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e471-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3e471-115">The call timed out.</span></span>|  
|<span data-ttu-id="3e471-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e471-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e471-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3e471-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e471-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e471-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e471-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3e471-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e471-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e471-120">E_FAIL</span></span>|<span data-ttu-id="3e471-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3e471-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e471-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3e471-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e471-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e471-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e471-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3e471-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3e471-125">K přidělení požadovaného prostředku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="3e471-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e471-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e471-126">Remarks</span></span>  
 <span data-ttu-id="3e471-127">Funkce platformy Windows používají `OVERLAPPED` strukturu pro ukládání stavu asynchronních vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="3e471-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="3e471-128">Modul CLR volá `InitializeHostOverlapped` metodu, aby hostiteli poskytl možnost připojit `OVERLAPPED` k instanci vlastní data.</span><span class="sxs-lookup"><span data-stu-id="3e471-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3e471-129">Chcete-li se dostat na začátek vlastního bloku dat, hostitelé musí nastavit posun na velikost `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="3e471-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="3e471-130">Návratová hodnota E_OUTOFMEMORY značí, že hostitel nedokázal inicializovat vlastní data.</span><span class="sxs-lookup"><span data-stu-id="3e471-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="3e471-131">V tomto případě CLR ohlásí chybu a volání se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3e471-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e471-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e471-132">Requirements</span></span>  
 <span data-ttu-id="3e471-133">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e471-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e471-134">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3e471-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e471-135">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3e471-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e471-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e471-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e471-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e471-137">See also</span></span>

- [<span data-ttu-id="3e471-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e471-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3e471-139">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="3e471-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="3e471-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e471-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
