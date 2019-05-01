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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03cac2b8433d6491d1fa474a0d4064ef4e260d6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993223"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="baf44-102">IHostMemoryManager::VirtualFree – metoda</span><span class="sxs-lookup"><span data-stu-id="baf44-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="baf44-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="baf44-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="baf44-104">Implementace Win32 `VirtualFree` uvolní, rozváže, uvolní nebo rozváže oblast stránky v rámci virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="baf44-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf44-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baf44-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baf44-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="baf44-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="baf44-107">[in] Ukazatel na základní adresa stránky virtuální paměti k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="baf44-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="baf44-108">[in] Velikost v bajtech, oblasti, kterou chcete být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="baf44-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="baf44-109">[in] Typ operace uvolnění.</span><span class="sxs-lookup"><span data-stu-id="baf44-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baf44-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="baf44-110">Return Value</span></span>  
  
|<span data-ttu-id="baf44-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baf44-111">HRESULT</span></span>|<span data-ttu-id="baf44-112">Popis</span><span class="sxs-lookup"><span data-stu-id="baf44-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baf44-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="baf44-113">S_OK</span></span>|<span data-ttu-id="baf44-114">`VirtualFree` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="baf44-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="baf44-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="baf44-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="baf44-116">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="baf44-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="baf44-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="baf44-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="baf44-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="baf44-118">The call timed out.</span></span>|  
|<span data-ttu-id="baf44-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="baf44-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="baf44-120">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="baf44-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="baf44-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="baf44-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="baf44-122">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="baf44-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="baf44-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="baf44-123">E_FAIL</span></span>|<span data-ttu-id="baf44-124">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="baf44-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="baf44-125">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="baf44-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="baf44-126">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="baf44-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="baf44-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="baf44-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="baf44-128">Byl proveden pokus o uvolnění paměti, který nebyl přidělen prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="baf44-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baf44-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="baf44-129">Remarks</span></span>  
 <span data-ttu-id="baf44-130">`VirtualFree` uvolní stránky virtuální paměti, které jsou spojené s `lpAddress` parametr prostřednictvím dřívějším volání [ihostmemorymanager::VirtualAlloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="baf44-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="baf44-131">Pokusy o uvolnění paměti, který nebyl přidělen prostřednictvím hostitele by měl vrátit HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="baf44-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="baf44-132">Sémantika je stejné jako ty Win32 provádění `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="baf44-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="baf44-133">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="baf44-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baf44-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="baf44-134">Requirements</span></span>  
 <span data-ttu-id="baf44-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baf44-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baf44-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="baf44-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baf44-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="baf44-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baf44-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baf44-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf44-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="baf44-139">See also</span></span>

- [<span data-ttu-id="baf44-140">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="baf44-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="baf44-141">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="baf44-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
