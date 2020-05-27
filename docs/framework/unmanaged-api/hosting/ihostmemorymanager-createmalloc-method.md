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
ms.openlocfilehash: 89c1d7b043d4369bf16a851924711c3c9d75791e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804534"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="d4517-102">IHostMemoryManager::CreateMAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="d4517-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="d4517-103">Získá ukazatel rozhraní na instanci [IHostMalloc](ihostmalloc-interface.md) , která se používá k provádění požadavků na přidělení z haldy vytvořené hostitelem.</span><span class="sxs-lookup"><span data-stu-id="d4517-103">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4517-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4517-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4517-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4517-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="d4517-106">pro Kombinace příznaků [MALLOC_TYPE](malloc-type-enumeration.md) , které určují charakteristiky přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="d4517-106">[in] A combination of [MALLOC_TYPE](malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="d4517-107">mimo Ukazatel na adresu `IHostMAlloc` instance poskytnuté hostitelem.</span><span class="sxs-lookup"><span data-stu-id="d4517-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4517-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4517-108">Return Value</span></span>  
  
|<span data-ttu-id="d4517-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4517-109">HRESULT</span></span>|<span data-ttu-id="d4517-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d4517-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4517-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4517-111">S_OK</span></span>|<span data-ttu-id="d4517-112">`CreateMAlloc`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d4517-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="d4517-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4517-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4517-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d4517-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4517-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4517-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4517-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d4517-116">The call timed out.</span></span>|  
|<span data-ttu-id="d4517-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4517-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4517-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d4517-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4517-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4517-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4517-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d4517-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4517-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4517-121">E_FAIL</span></span>|<span data-ttu-id="d4517-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d4517-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4517-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d4517-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4517-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d4517-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d4517-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d4517-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d4517-126">K dokončení žádosti o přidělení není k dispozici dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="d4517-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4517-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4517-127">Remarks</span></span>  
 <span data-ttu-id="d4517-128">`CreateMAlloc`Vrátí objekt, který umožňuje modulu CLR vytvářet požadavky na přidělení prostřednictvím hostitele namísto použití standardních funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="d4517-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4517-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4517-129">Requirements</span></span>  
 <span data-ttu-id="d4517-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4517-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4517-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4517-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4517-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4517-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4517-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4517-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4517-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4517-134">See also</span></span>

- [<span data-ttu-id="d4517-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4517-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="d4517-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4517-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
