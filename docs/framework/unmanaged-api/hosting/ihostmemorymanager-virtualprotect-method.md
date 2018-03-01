---
title: "IHostMemoryManager::VirtualProtect – metoda"
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
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77e8e163a16752934d0a1d826cc8463b3d3281bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="7577a-102">IHostMemoryManager::VirtualProtect – metoda</span><span class="sxs-lookup"><span data-stu-id="7577a-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="7577a-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="7577a-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="7577a-104">Implementace Win32 `VirtualProtect` změny ochrany v oblasti potvrdit stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="7577a-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7577a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7577a-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7577a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7577a-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="7577a-107">[v] Ukazatel na adresu základní virtuální paměti, jejichž atributy ochrany se změnit.</span><span class="sxs-lookup"><span data-stu-id="7577a-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="7577a-108">[v] Velikost v bajtech, oblasti paměťových stránek, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="7577a-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="7577a-109">[v] Typ ochrany paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="7577a-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="7577a-110">[out] Ukazatel na předchozí hodnotu ochrany paměti.</span><span class="sxs-lookup"><span data-stu-id="7577a-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7577a-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7577a-111">Return Value</span></span>  
  
|<span data-ttu-id="7577a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7577a-112">HRESULT</span></span>|<span data-ttu-id="7577a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7577a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7577a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7577a-114">S_OK</span></span>|<span data-ttu-id="7577a-115">`VirtualProtect`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7577a-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="7577a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7577a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7577a-117">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7577a-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7577a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7577a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7577a-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7577a-119">The call timed out.</span></span>|  
|<span data-ttu-id="7577a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7577a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7577a-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="7577a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7577a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7577a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7577a-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="7577a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7577a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7577a-124">E_FAIL</span></span>|<span data-ttu-id="7577a-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="7577a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7577a-126">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7577a-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7577a-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7577a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7577a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7577a-128">Remarks</span></span>  
 <span data-ttu-id="7577a-129">Tato implementace `VirtualProtect` vrátí hodnotu HRESULT, zatímco Win32 implementace vrátí nenulovou hodnotu, čímž indikuje úspěšné provedení a nulová hodnota označující selhání.</span><span class="sxs-lookup"><span data-stu-id="7577a-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="7577a-130">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="7577a-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7577a-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7577a-131">Requirements</span></span>  
 <span data-ttu-id="7577a-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7577a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7577a-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7577a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7577a-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7577a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7577a-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7577a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7577a-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="7577a-136">See Also</span></span>  
 [<span data-ttu-id="7577a-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7577a-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
