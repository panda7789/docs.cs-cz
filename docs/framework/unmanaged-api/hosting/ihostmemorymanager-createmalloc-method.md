---
title: "IHostMemoryManager::CreateMAlloc – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.CreateMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19b43ccf7cb2429c28c052ab8ab3a009ec4a30a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="07bd9-102">IHostMemoryManager::CreateMAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="07bd9-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="07bd9-103">Získá ukazatele rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která se používá k zajištění požadavků na přidělení z haldy vytvořené hostitele.</span><span class="sxs-lookup"><span data-stu-id="07bd9-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07bd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07bd9-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07bd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07bd9-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="07bd9-106">[v] Kombinace [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) příznaky, které určuje charakteristiky paměti, které je právě přiděleno.</span><span class="sxs-lookup"><span data-stu-id="07bd9-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="07bd9-107">[out] Ukazatel na adresu `IHostMAlloc` instance od hostitele.</span><span class="sxs-lookup"><span data-stu-id="07bd9-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07bd9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="07bd9-108">Return Value</span></span>  
  
|<span data-ttu-id="07bd9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07bd9-109">HRESULT</span></span>|<span data-ttu-id="07bd9-110">Popis</span><span class="sxs-lookup"><span data-stu-id="07bd9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07bd9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="07bd9-111">S_OK</span></span>|<span data-ttu-id="07bd9-112">`CreateMAlloc`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="07bd9-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="07bd9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07bd9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07bd9-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="07bd9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07bd9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07bd9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07bd9-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="07bd9-116">The call timed out.</span></span>|  
|<span data-ttu-id="07bd9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07bd9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07bd9-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="07bd9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07bd9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07bd9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07bd9-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="07bd9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07bd9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07bd9-121">E_FAIL</span></span>|<span data-ttu-id="07bd9-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="07bd9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07bd9-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="07bd9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07bd9-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="07bd9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="07bd9-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="07bd9-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="07bd9-126">Není dostatek fyzické paměti nebylo k dispozici k dokončení požadavek na přidělení.</span><span class="sxs-lookup"><span data-stu-id="07bd9-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07bd9-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07bd9-127">Remarks</span></span>  
 <span data-ttu-id="07bd9-128">`CreateMAlloc`Vrátí objekt, který umožňuje provádět požadavky na přidělení prostřednictvím hostitele místo použití standardní Win32 funkce modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="07bd9-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07bd9-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07bd9-129">Requirements</span></span>  
 <span data-ttu-id="07bd9-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07bd9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07bd9-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07bd9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07bd9-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07bd9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07bd9-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07bd9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07bd9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="07bd9-134">See Also</span></span>  
 [<span data-ttu-id="07bd9-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07bd9-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="07bd9-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07bd9-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
