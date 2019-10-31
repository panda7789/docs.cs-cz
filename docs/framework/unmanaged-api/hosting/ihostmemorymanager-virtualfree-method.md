---
title: IHostMemoryManager::VirtualFree – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: b53c0bb38922ae8de048c131807eb32f97423d6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128580"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="29e32-102">IHostMemoryManager::VirtualFree – metoda</span><span class="sxs-lookup"><span data-stu-id="29e32-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="29e32-103">Slouží jako logická obálka odpovídající funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="29e32-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="29e32-104">Implementace Win32 `VirtualFree` vydání, zrušení potvrzení nebo uvolnění a zrušení potvrzení oblasti stránek v rámci virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="29e32-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e32-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29e32-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29e32-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="29e32-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="29e32-107">pro Ukazatel na základní adresu stránky virtuální paměti, která se uvolní.</span><span class="sxs-lookup"><span data-stu-id="29e32-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="29e32-108">pro Velikost oblasti, která se má uvolnit (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="29e32-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="29e32-109">pro Typ uvolnění operace.</span><span class="sxs-lookup"><span data-stu-id="29e32-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29e32-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="29e32-110">Return Value</span></span>  
  
|<span data-ttu-id="29e32-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29e32-111">HRESULT</span></span>|<span data-ttu-id="29e32-112">Popis</span><span class="sxs-lookup"><span data-stu-id="29e32-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29e32-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="29e32-113">S_OK</span></span>|<span data-ttu-id="29e32-114">`VirtualFree` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="29e32-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="29e32-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29e32-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29e32-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="29e32-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29e32-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29e32-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29e32-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="29e32-118">The call timed out.</span></span>|  
|<span data-ttu-id="29e32-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29e32-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29e32-120">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="29e32-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29e32-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29e32-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29e32-122">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="29e32-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29e32-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29e32-123">E_FAIL</span></span>|<span data-ttu-id="29e32-124">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="29e32-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29e32-125">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="29e32-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29e32-126">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="29e32-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="29e32-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="29e32-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="29e32-128">Byl proveden pokus o uvolnění paměti, která nebyla přidělena prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="29e32-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29e32-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29e32-129">Remarks</span></span>  
 <span data-ttu-id="29e32-130">`VirtualFree` uvolní stránky virtuální paměti přidružené k parametru `lpAddress` prostřednictvím předchozího volání funkce [IHostMemoryManager:: VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="29e32-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="29e32-131">Pokusy o volnou paměť, která nebyla přidělena prostřednictvím hostitele, by měly vracet HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="29e32-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="29e32-132">Sémantika je stejná jako u implementace `VirtualFree`v systému Win32.</span><span class="sxs-lookup"><span data-stu-id="29e32-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="29e32-133">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="29e32-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e32-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29e32-134">Requirements</span></span>  
 <span data-ttu-id="29e32-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29e32-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e32-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="29e32-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29e32-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="29e32-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29e32-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e32-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e32-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29e32-139">See also</span></span>

- [<span data-ttu-id="29e32-140">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29e32-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="29e32-141">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29e32-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
