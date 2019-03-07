---
title: IHostMemoryManager::CreateMAlloc – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18c6390e0874dfe658911b4e9ce55527b2558bc2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500223"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="6a5a1-102">IHostMemoryManager::CreateMAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="6a5a1-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="6a5a1-103">Získá ukazatel rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která slouží k podání žádostí o přidělení z haldy vytvořené hostitele.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a5a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a5a1-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a5a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a5a1-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="6a5a1-106">[in] Kombinace [malloc_type –](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) příznak, který určuje vlastnosti paměti, které je právě přiděleno.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="6a5a1-107">[out] Ukazatel na adresu `IHostMAlloc` instance, které jsou poskytovány tímto hostitelem.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a5a1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a5a1-108">Return Value</span></span>  
  
|<span data-ttu-id="6a5a1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a5a1-109">HRESULT</span></span>|<span data-ttu-id="6a5a1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6a5a1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a5a1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a5a1-111">S_OK</span></span>|<span data-ttu-id="6a5a1-112">`CreateMAlloc` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="6a5a1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a5a1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a5a1-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a5a1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a5a1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a5a1-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-116">The call timed out.</span></span>|  
|<span data-ttu-id="6a5a1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a5a1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a5a1-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a5a1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a5a1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a5a1-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a5a1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a5a1-121">E_FAIL</span></span>|<span data-ttu-id="6a5a1-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a5a1-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a5a1-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6a5a1-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6a5a1-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6a5a1-126">Není dostatek fyzické paměti nebyly k dispozici k dokončení požadavek na přidělení.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a5a1-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a5a1-127">Remarks</span></span>  
 <span data-ttu-id="6a5a1-128">`CreateMAlloc` Vrátí objekt, který umožňuje CLR k podání žádostí o přidělení přes hostitele namísto použití standardní funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="6a5a1-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a5a1-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a5a1-129">Requirements</span></span>  
 <span data-ttu-id="6a5a1-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a5a1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a5a1-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6a5a1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a5a1-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a5a1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a5a1-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a5a1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5a1-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a5a1-134">See also</span></span>
- [<span data-ttu-id="6a5a1-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a5a1-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="6a5a1-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a5a1-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
