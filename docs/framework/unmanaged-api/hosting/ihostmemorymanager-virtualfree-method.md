---
title: IHostMemoryManager::VirtualFree – metoda
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 663c01d7e4b551ecf18bdd85a63aefc43f9750e2
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="9c9aa-102">IHostMemoryManager::VirtualFree – metoda</span><span class="sxs-lookup"><span data-stu-id="9c9aa-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="9c9aa-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="9c9aa-104">Implementace Win32 `VirtualFree` uvolní, decommits, nebo uvolní a decommits oblast stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c9aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c9aa-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c9aa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c9aa-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="9c9aa-107">[v] Ukazatel na základní adresu stránky virtuální paměti, které chcete uvolnit.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="9c9aa-108">[v] Velikost v bajtech, oblasti na uvolnění.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="9c9aa-109">[v] Typ operace uvolnění.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c9aa-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9c9aa-110">Return Value</span></span>  
  
|<span data-ttu-id="9c9aa-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c9aa-111">HRESULT</span></span>|<span data-ttu-id="9c9aa-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9c9aa-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c9aa-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c9aa-113">S_OK</span></span>|<span data-ttu-id="9c9aa-114">`VirtualFree` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="9c9aa-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c9aa-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c9aa-116">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c9aa-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c9aa-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c9aa-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-118">The call timed out.</span></span>|  
|<span data-ttu-id="9c9aa-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c9aa-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c9aa-120">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c9aa-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c9aa-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c9aa-122">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c9aa-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c9aa-123">E_FAIL</span></span>|<span data-ttu-id="9c9aa-124">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c9aa-125">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c9aa-126">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9c9aa-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="9c9aa-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="9c9aa-128">Došlo pokusu o volné paměti, která nebyla přidělena prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c9aa-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c9aa-129">Remarks</span></span>  
 <span data-ttu-id="9c9aa-130">`VirtualFree` uvolní stránky virtuální paměti, které jsou spojené s `lpAddress` parametr prostřednictvím starší volání [ihostmemorymanager::VirtualAlloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="9c9aa-131">Pokusy o volné paměti, která nebyla přidělena prostřednictvím hostitele by měl vrátit HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="9c9aa-132">Sémantika jsou stejné jako Win32 implementace `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="9c9aa-133">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="9c9aa-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c9aa-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c9aa-134">Requirements</span></span>  
 <span data-ttu-id="9c9aa-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c9aa-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c9aa-136">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c9aa-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c9aa-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c9aa-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c9aa-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c9aa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c9aa-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c9aa-139">See Also</span></span>  
 [<span data-ttu-id="9c9aa-140">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c9aa-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="9c9aa-141">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c9aa-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
