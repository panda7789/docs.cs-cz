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
ms.openlocfilehash: 8bcb01f4a19e6043bd59fe6f1565cdf35ed1f77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136729"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="897e8-102">IHostMemoryManager::CreateMAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="897e8-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="897e8-103">Získá ukazatel rozhraní na instanci [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) , která se používá k provádění požadavků na přidělení z haldy vytvořené hostitelem.</span><span class="sxs-lookup"><span data-stu-id="897e8-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="897e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="897e8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="897e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="897e8-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="897e8-106">pro Kombinace příznaků [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) , které určují charakteristiky přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="897e8-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="897e8-107">mimo Ukazatel na adresu `IHostMAlloc` instance poskytnuté hostitelem.</span><span class="sxs-lookup"><span data-stu-id="897e8-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="897e8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="897e8-108">Return Value</span></span>  
  
|<span data-ttu-id="897e8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="897e8-109">HRESULT</span></span>|<span data-ttu-id="897e8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="897e8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="897e8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="897e8-111">S_OK</span></span>|<span data-ttu-id="897e8-112">`CreateMAlloc` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="897e8-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="897e8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="897e8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="897e8-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="897e8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="897e8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="897e8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="897e8-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="897e8-116">The call timed out.</span></span>|  
|<span data-ttu-id="897e8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="897e8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="897e8-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="897e8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="897e8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="897e8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="897e8-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="897e8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="897e8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="897e8-121">E_FAIL</span></span>|<span data-ttu-id="897e8-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="897e8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="897e8-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="897e8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="897e8-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="897e8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="897e8-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="897e8-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="897e8-126">K dokončení žádosti o přidělení není k dispozici dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="897e8-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="897e8-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="897e8-127">Remarks</span></span>  
 <span data-ttu-id="897e8-128">`CreateMAlloc` vrátí objekt, který umožňuje modulu CLR vytvářet požadavky na přidělení prostřednictvím hostitele namísto použití standardních funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="897e8-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="897e8-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="897e8-129">Requirements</span></span>  
 <span data-ttu-id="897e8-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="897e8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="897e8-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="897e8-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="897e8-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="897e8-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="897e8-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="897e8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="897e8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="897e8-134">See also</span></span>

- [<span data-ttu-id="897e8-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="897e8-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="897e8-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="897e8-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
