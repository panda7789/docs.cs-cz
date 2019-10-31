---
title: IHostMAlloc::Alloc – metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: 9837e4e3428a0293c8e689b3f3e081aa07f055b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192071"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="600ab-102">IHostMAlloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="600ab-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="600ab-103">Požaduje, aby hostitel přidělil určenou velikost paměti z haldy.</span><span class="sxs-lookup"><span data-stu-id="600ab-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="600ab-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="600ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="600ab-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="600ab-106">pro Velikost aktuální žádosti o přidělení paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="600ab-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="600ab-107">pro Jedna z hodnot [EMemoryCriticalLevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) , která indikuje dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="600ab-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="600ab-108">mimo Ukazatel na přidělenou paměť nebo hodnotu null, pokud požadavek nebylo možné dokončit.</span><span class="sxs-lookup"><span data-stu-id="600ab-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="600ab-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="600ab-109">Return Value</span></span>  
  
|<span data-ttu-id="600ab-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="600ab-110">HRESULT</span></span>|<span data-ttu-id="600ab-111">Popis</span><span class="sxs-lookup"><span data-stu-id="600ab-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="600ab-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="600ab-112">S_OK</span></span>|<span data-ttu-id="600ab-113">`Alloc` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="600ab-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="600ab-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="600ab-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="600ab-115">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="600ab-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="600ab-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="600ab-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="600ab-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="600ab-117">The call timed out.</span></span>|  
|<span data-ttu-id="600ab-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="600ab-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="600ab-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="600ab-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="600ab-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="600ab-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="600ab-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="600ab-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="600ab-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="600ab-122">E_FAIL</span></span>|<span data-ttu-id="600ab-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="600ab-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="600ab-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="600ab-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="600ab-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="600ab-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="600ab-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="600ab-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="600ab-127">K dokončení žádosti o přidělení není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="600ab-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="600ab-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="600ab-128">Remarks</span></span>  
 <span data-ttu-id="600ab-129">Modul CLR získá ukazatel rozhraní na instanci `IHostMalloc` voláním metody [IHostMemoryManager:: CreateMalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="600ab-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="600ab-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="600ab-130">Requirements</span></span>  
 <span data-ttu-id="600ab-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="600ab-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="600ab-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="600ab-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="600ab-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="600ab-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="600ab-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="600ab-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600ab-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="600ab-135">See also</span></span>

- [<span data-ttu-id="600ab-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="600ab-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="600ab-137">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="600ab-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
