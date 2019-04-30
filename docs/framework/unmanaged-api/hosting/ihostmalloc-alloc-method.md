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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32499e74e8af9a865347bd800d3db4c303a7344c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796731"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="a79df-102">IHostMAlloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="a79df-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="a79df-103">Požadavky, že hostitel přidělit zadaného množství paměti z haldy.</span><span class="sxs-lookup"><span data-stu-id="a79df-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a79df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a79df-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a79df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a79df-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="a79df-106">[in] Velikost v bajtech, aktuální požadavek na přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="a79df-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="a79df-107">[in] Jeden z [ememorycriticallevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnoty určující dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="a79df-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="a79df-108">[out] Ukazatel do přidělené paměti nebo hodnota null, pokud požadavek nešlo dokončit.</span><span class="sxs-lookup"><span data-stu-id="a79df-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a79df-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a79df-109">Return Value</span></span>  
  
|<span data-ttu-id="a79df-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a79df-110">HRESULT</span></span>|<span data-ttu-id="a79df-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a79df-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a79df-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a79df-112">S_OK</span></span>|<span data-ttu-id="a79df-113">`Alloc` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a79df-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="a79df-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a79df-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a79df-115">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a79df-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a79df-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a79df-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a79df-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a79df-117">The call timed out.</span></span>|  
|<span data-ttu-id="a79df-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a79df-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a79df-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a79df-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a79df-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a79df-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a79df-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a79df-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a79df-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a79df-122">E_FAIL</span></span>|<span data-ttu-id="a79df-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a79df-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a79df-124">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a79df-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a79df-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a79df-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a79df-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a79df-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a79df-127">Nedostatek paměti nebyly k dispozici k dokončení požadavek na přidělení.</span><span class="sxs-lookup"><span data-stu-id="a79df-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a79df-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a79df-128">Remarks</span></span>  
 <span data-ttu-id="a79df-129">Modul CLR načte ukazatel rozhraní k `IHostMalloc` instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a79df-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a79df-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a79df-130">Requirements</span></span>  
 <span data-ttu-id="a79df-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a79df-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a79df-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a79df-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a79df-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a79df-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a79df-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a79df-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79df-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a79df-135">See also</span></span>

- [<span data-ttu-id="a79df-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a79df-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="a79df-137">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a79df-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
