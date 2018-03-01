---
title: "IHostMAlloc::Alloc – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7d999425be2bc5963aaa9f15b82bd951f6f564af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="8d1eb-102">IHostMAlloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="8d1eb-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="8d1eb-103">Požadavky z halda vyhradit zadaného množství paměti hostitele.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d1eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d1eb-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d1eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d1eb-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="8d1eb-106">[v] Velikost v bajtech aktuální požadavek na přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="8d1eb-107">[v] Jeden z [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnoty, která určuje dopad došlo k chybě přidělení.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="8d1eb-108">[out] Ukazatel na přidělené paměti, nebo hodnota null, pokud požadavek nebylo možné dokončit.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d1eb-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d1eb-109">Return Value</span></span>  
  
|<span data-ttu-id="8d1eb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d1eb-110">HRESULT</span></span>|<span data-ttu-id="8d1eb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8d1eb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d1eb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d1eb-112">S_OK</span></span>|<span data-ttu-id="8d1eb-113">`Alloc`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="8d1eb-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d1eb-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d1eb-115">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d1eb-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d1eb-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d1eb-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-117">The call timed out.</span></span>|  
|<span data-ttu-id="8d1eb-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d1eb-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d1eb-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d1eb-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d1eb-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d1eb-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d1eb-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d1eb-122">E_FAIL</span></span>|<span data-ttu-id="8d1eb-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d1eb-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d1eb-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8d1eb-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8d1eb-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8d1eb-127">Nedostatek paměti nebylo k dispozici k dokončení požadavek na přidělení.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d1eb-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d1eb-128">Remarks</span></span>  
 <span data-ttu-id="8d1eb-129">Modul CLR získá ukazatele rozhraní k `IHostMalloc` instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d1eb-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d1eb-130">Requirements</span></span>  
 <span data-ttu-id="8d1eb-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d1eb-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d1eb-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d1eb-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d1eb-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d1eb-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d1eb-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d1eb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d1eb-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d1eb-135">See Also</span></span>  
 [<span data-ttu-id="8d1eb-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d1eb-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="8d1eb-137">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d1eb-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
