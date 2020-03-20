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
ms.openlocfilehash: dded37fdef02963f60883b289462aa6a96693b3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176302"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="c91b5-102">IHostMAlloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="c91b5-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="c91b5-103">Požaduje, aby hostitel přidělit zadané množství paměti z haldy.</span><span class="sxs-lookup"><span data-stu-id="c91b5-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c91b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c91b5-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c91b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c91b5-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="c91b5-106">[v] Velikost aktuálního požadavku na přidělení paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c91b5-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="c91b5-107">[v] Jedna z hodnot [EMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) označující dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="c91b5-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="c91b5-108">[out] Ukazatel na přidělenou paměť nebo hodnotu null, pokud požadavek nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="c91b5-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c91b5-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c91b5-109">Return Value</span></span>  
  
|<span data-ttu-id="c91b5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c91b5-110">HRESULT</span></span>|<span data-ttu-id="c91b5-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c91b5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c91b5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c91b5-112">S_OK</span></span>|<span data-ttu-id="c91b5-113">`Alloc`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c91b5-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="c91b5-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c91b5-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c91b5-115">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c91b5-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c91b5-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c91b5-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c91b5-117">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="c91b5-117">The call timed out.</span></span>|  
|<span data-ttu-id="c91b5-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c91b5-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c91b5-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c91b5-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c91b5-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c91b5-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c91b5-121">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="c91b5-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c91b5-122">E_fail</span><span class="sxs-lookup"><span data-stu-id="c91b5-122">E_FAIL</span></span>|<span data-ttu-id="c91b5-123">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="c91b5-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c91b5-124">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c91b5-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c91b5-125">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c91b5-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c91b5-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c91b5-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c91b5-127">K dokončení požadavku na přidělení nebylo k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="c91b5-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c91b5-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c91b5-128">Remarks</span></span>  
 <span data-ttu-id="c91b5-129">CLR získá ukazatel rozhraní `IHostMalloc` k instanci voláním metody [IHostMemoryManager::CreateMalloc.](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)</span><span class="sxs-lookup"><span data-stu-id="c91b5-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c91b5-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c91b5-130">Requirements</span></span>  
 <span data-ttu-id="c91b5-131">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c91b5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c91b5-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c91b5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c91b5-133">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c91b5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c91b5-134">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c91b5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91b5-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c91b5-135">See also</span></span>

- [<span data-ttu-id="c91b5-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c91b5-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="c91b5-137">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c91b5-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
