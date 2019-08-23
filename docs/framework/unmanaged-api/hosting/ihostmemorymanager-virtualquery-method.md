---
title: IHostMemoryManager::VirtualQuery – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16d146766786f129d6da38bde1126ce8afe5e70f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963693"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="a4f21-102">IHostMemoryManager::VirtualQuery – metoda</span><span class="sxs-lookup"><span data-stu-id="a4f21-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="a4f21-103">Slouží jako logická obálka odpovídající funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="a4f21-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="a4f21-104">Implementace `VirtualQuery` Win32 načte informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="a4f21-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4f21-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4f21-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4f21-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4f21-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="a4f21-107">pro Ukazatel na adresu ve virtuální paměti, která se má dotazovat.</span><span class="sxs-lookup"><span data-stu-id="a4f21-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="a4f21-108">mimo Ukazatel na strukturu, která obsahuje informace o zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="a4f21-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a4f21-109">pro Velikost vyrovnávací paměti (v bajtech), na `lpBuffer` kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="a4f21-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="a4f21-110">mimo Ukazatel na počet bajtů vrácených vyrovnávací pamětí informací.</span><span class="sxs-lookup"><span data-stu-id="a4f21-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4f21-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4f21-111">Return Value</span></span>  
  
|<span data-ttu-id="a4f21-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4f21-112">HRESULT</span></span>|<span data-ttu-id="a4f21-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a4f21-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4f21-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4f21-114">S_OK</span></span>|<span data-ttu-id="a4f21-115">`VirtualQuery`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a4f21-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="a4f21-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a4f21-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a4f21-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a4f21-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a4f21-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a4f21-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a4f21-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a4f21-119">The call timed out.</span></span>|  
|<span data-ttu-id="a4f21-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a4f21-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a4f21-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="a4f21-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a4f21-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a4f21-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a4f21-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="a4f21-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a4f21-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4f21-124">E_FAIL</span></span>|<span data-ttu-id="a4f21-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="a4f21-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4f21-126">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="a4f21-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a4f21-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a4f21-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4f21-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4f21-128">Remarks</span></span>  
 <span data-ttu-id="a4f21-129">`VirtualQuery`poskytuje informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="a4f21-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="a4f21-130">Tato implementace nastaví hodnotu `pResult` parametru na počet bajtů vrácených v zásobníku informací a vrátí hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a4f21-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="a4f21-131">Ve funkci Win32 `VirtualQuery` je návratovou hodnotou velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a4f21-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="a4f21-132">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="a4f21-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a4f21-133">Implementace `VirtualQuery` operačního systému nenese zablokování a může běžet k dokončení náhodných vláken pozastavených v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="a4f21-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="a4f21-134">Při implementaci hostované verze této metody používejte skvělou opatrnost.</span><span class="sxs-lookup"><span data-stu-id="a4f21-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4f21-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4f21-135">Requirements</span></span>  
 <span data-ttu-id="a4f21-136">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4f21-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4f21-137">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a4f21-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4f21-138">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a4f21-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4f21-139">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4f21-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f21-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4f21-140">See also</span></span>

- [<span data-ttu-id="a4f21-141">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4f21-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
