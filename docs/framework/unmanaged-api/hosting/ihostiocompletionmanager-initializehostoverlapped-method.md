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
ms.openlocfilehash: 9fd299ad25166bcbcf0202da13a5b4cbdd20d7d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133793"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="e6e3b-102">IHostIoCompletionManager::InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="e6e3b-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="e6e3b-103">Poskytuje hostiteli možnost inicializovat jakákoli vlastní data pro připojení ke struktuře Win32 `OVERLAPPED`, která se používá pro asynchronní vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6e3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6e3b-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="e6e3b-106">pro Ukazatel na strukturu `OVERLAPPED` Win32, která se má zahrnout do vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6e3b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e6e3b-107">Return Value</span></span>  
  
|<span data-ttu-id="e6e3b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6e3b-108">HRESULT</span></span>|<span data-ttu-id="e6e3b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e6e3b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6e3b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6e3b-110">S_OK</span></span>|<span data-ttu-id="e6e3b-111">`InitializeHostOverlapped` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="e6e3b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6e3b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6e3b-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6e3b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6e3b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6e3b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-115">The call timed out.</span></span>|  
|<span data-ttu-id="e6e3b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6e3b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6e3b-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6e3b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6e3b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6e3b-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6e3b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6e3b-120">E_FAIL</span></span>|<span data-ttu-id="e6e3b-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6e3b-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6e3b-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e6e3b-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e6e3b-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e6e3b-125">K přidělení požadovaného prostředku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6e3b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6e3b-126">Remarks</span></span>  
 <span data-ttu-id="e6e3b-127">Funkce platformy Windows používají strukturu `OVERLAPPED` k uložení stavu asynchronních vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="e6e3b-128">CLR volá metodu `InitializeHostOverlapped`, aby hostitel mohl připojit vlastní data k instanci `OVERLAPPED`.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e6e3b-129">Chcete-li se dostat na začátek vlastního bloku dat, musí hostitelé nastavit posun na velikost `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="e6e3b-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="e6e3b-130">Návratová hodnota E_OUTOFMEMORY značí, že hostitel nedokázal inicializovat vlastní data.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="e6e3b-131">V tomto případě CLR ohlásí chybu a volání se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6e3b-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6e3b-132">Requirements</span></span>  
 <span data-ttu-id="e6e3b-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6e3b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6e3b-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e6e3b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6e3b-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e6e3b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6e3b-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6e3b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e3b-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6e3b-137">See also</span></span>

- [<span data-ttu-id="e6e3b-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6e3b-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e6e3b-139">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e6e3b-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="e6e3b-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6e3b-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
