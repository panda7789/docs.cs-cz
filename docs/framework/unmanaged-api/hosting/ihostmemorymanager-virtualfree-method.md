---
title: "IHostMemoryManager::VirtualFree – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualFree
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 468228101403c7ce3c123401e906e3ccbe301e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="e5d70-102">IHostMemoryManager::VirtualFree – metoda</span><span class="sxs-lookup"><span data-stu-id="e5d70-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="e5d70-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="e5d70-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="e5d70-104">Implementace Win32 `VirtualFree` uvolní, decommits, nebo uvolní a decommits oblast stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="e5d70-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d70-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5d70-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5d70-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5d70-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="e5d70-107">[v] Ukazatel na základní adresu stránky virtuální paměti, které chcete uvolnit.</span><span class="sxs-lookup"><span data-stu-id="e5d70-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="e5d70-108">[v] Velikost v bajtech, oblasti na uvolnění.</span><span class="sxs-lookup"><span data-stu-id="e5d70-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="e5d70-109">[v] Typ operace uvolnění.</span><span class="sxs-lookup"><span data-stu-id="e5d70-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5d70-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5d70-110">Return Value</span></span>  
  
|<span data-ttu-id="e5d70-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5d70-111">HRESULT</span></span>|<span data-ttu-id="e5d70-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e5d70-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5d70-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5d70-113">S_OK</span></span>|<span data-ttu-id="e5d70-114">`VirtualFree`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e5d70-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="e5d70-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e5d70-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e5d70-116">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e5d70-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e5d70-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e5d70-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e5d70-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e5d70-118">The call timed out.</span></span>|  
|<span data-ttu-id="e5d70-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e5d70-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e5d70-120">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e5d70-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e5d70-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e5d70-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e5d70-122">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e5d70-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e5d70-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e5d70-123">E_FAIL</span></span>|<span data-ttu-id="e5d70-124">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e5d70-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e5d70-125">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e5d70-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e5d70-126">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e5d70-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e5d70-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="e5d70-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="e5d70-128">Došlo pokusu o volné paměti, která nebyla přidělena prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="e5d70-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5d70-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5d70-129">Remarks</span></span>  
 <span data-ttu-id="e5d70-130">`VirtualFree`uvolní stránky virtuální paměti, které jsou spojené s `lpAddress` parametr prostřednictvím starší volání [ihostmemorymanager::VirtualAlloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="e5d70-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="e5d70-131">Pokusy o volné paměti, která nebyla přidělena prostřednictvím hostitele by měl vrátit HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="e5d70-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="e5d70-132">Sémantika jsou stejné jako Win32 implementace `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="e5d70-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="e5d70-133">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="e5d70-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5d70-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5d70-134">Requirements</span></span>  
 <span data-ttu-id="e5d70-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5d70-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5d70-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e5d70-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5d70-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5d70-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5d70-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5d70-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d70-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5d70-139">See Also</span></span>  
 [<span data-ttu-id="e5d70-140">Ihostmemorymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5d70-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="e5d70-141">Ihostmalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5d70-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
