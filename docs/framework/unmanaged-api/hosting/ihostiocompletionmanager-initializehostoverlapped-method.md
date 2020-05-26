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
ms.openlocfilehash: cf257ab86d27946c861c89dff5e6f09a42013e58
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804711"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="cc968-102">IHostIoCompletionManager::InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="cc968-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="cc968-103">Poskytuje hostiteli možnost inicializovat jakákoli vlastní data pro připojení ke `OVERLAPPED` struktuře Win32, která se používá pro asynchronní vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="cc968-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc968-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc968-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc968-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc968-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="cc968-106">pro Ukazatel na `OVERLAPPED` strukturu Win32, který se má zahrnout do vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="cc968-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc968-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc968-107">Return Value</span></span>  
  
|<span data-ttu-id="cc968-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc968-108">HRESULT</span></span>|<span data-ttu-id="cc968-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cc968-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc968-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc968-110">S_OK</span></span>|<span data-ttu-id="cc968-111">`InitializeHostOverlapped`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="cc968-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="cc968-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc968-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc968-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cc968-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc968-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc968-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc968-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="cc968-115">The call timed out.</span></span>|  
|<span data-ttu-id="cc968-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc968-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc968-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="cc968-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc968-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc968-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc968-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="cc968-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc968-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc968-120">E_FAIL</span></span>|<span data-ttu-id="cc968-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="cc968-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc968-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="cc968-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc968-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc968-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cc968-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cc968-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cc968-125">K přidělení požadovaného prostředku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="cc968-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc968-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc968-126">Remarks</span></span>  
 <span data-ttu-id="cc968-127">Funkce platformy Windows používají `OVERLAPPED` strukturu pro ukládání stavu asynchronních vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="cc968-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="cc968-128">Modul CLR volá `InitializeHostOverlapped` metodu, aby hostiteli poskytl možnost připojit k instanci vlastní data `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="cc968-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cc968-129">Chcete-li se dostat na začátek vlastního bloku dat, hostitelé musí nastavit posun na velikost `OVERLAPPED` struktury ( `sizeof(OVERLAPPED)` ).</span><span class="sxs-lookup"><span data-stu-id="cc968-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="cc968-130">Návratová hodnota E_OUTOFMEMORY značí, že hostitel nedokázal inicializovat vlastní data.</span><span class="sxs-lookup"><span data-stu-id="cc968-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="cc968-131">V tomto případě CLR ohlásí chybu a volání se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="cc968-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc968-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc968-132">Requirements</span></span>  
 <span data-ttu-id="cc968-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc968-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc968-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc968-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc968-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc968-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc968-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc968-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc968-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc968-137">See also</span></span>

- [<span data-ttu-id="cc968-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc968-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="cc968-139">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="cc968-139">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="cc968-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc968-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
