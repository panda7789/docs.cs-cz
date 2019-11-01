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
ms.openlocfilehash: 00ec0b92a9f7151ee9b831c85548c4f61d87af68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192038"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="e39b3-102">IHostMemoryManager::VirtualQuery – metoda</span><span class="sxs-lookup"><span data-stu-id="e39b3-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="e39b3-103">Slouží jako logická obálka odpovídající funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="e39b3-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="e39b3-104">Implementace Win32 `VirtualQuery` načítá informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="e39b3-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e39b3-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e39b3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e39b3-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="e39b3-107">pro Ukazatel na adresu ve virtuální paměti, která se má dotazovat.</span><span class="sxs-lookup"><span data-stu-id="e39b3-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="e39b3-108">mimo Ukazatel na strukturu, která obsahuje informace o zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="e39b3-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e39b3-109">pro Velikost vyrovnávací paměti (v bajtech), na kterou `lpBuffer` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="e39b3-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="e39b3-110">mimo Ukazatel na počet bajtů vrácených vyrovnávací pamětí informací.</span><span class="sxs-lookup"><span data-stu-id="e39b3-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e39b3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e39b3-111">Return Value</span></span>  
  
|<span data-ttu-id="e39b3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e39b3-112">HRESULT</span></span>|<span data-ttu-id="e39b3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e39b3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e39b3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e39b3-114">S_OK</span></span>|<span data-ttu-id="e39b3-115">`VirtualQuery` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e39b3-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="e39b3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e39b3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e39b3-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e39b3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e39b3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e39b3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e39b3-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e39b3-119">The call timed out.</span></span>|  
|<span data-ttu-id="e39b3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e39b3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e39b3-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e39b3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e39b3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e39b3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e39b3-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e39b3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e39b3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e39b3-124">E_FAIL</span></span>|<span data-ttu-id="e39b3-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e39b3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e39b3-126">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e39b3-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e39b3-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e39b3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e39b3-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e39b3-128">Remarks</span></span>  
 <span data-ttu-id="e39b3-129">`VirtualQuery` poskytuje informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="e39b3-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="e39b3-130">Tato implementace nastaví hodnotu parametru `pResult` na počet bajtů vrácených ve vyrovnávací paměti informací a vrátí hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e39b3-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="e39b3-131">Ve funkci Win32 `VirtualQuery` je návratová hodnota velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e39b3-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="e39b3-132">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="e39b3-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e39b3-133">Implementace `VirtualQuery` operačního systému nenese zablokování a může běžet k dokončení náhodných vláken pozastavených v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="e39b3-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="e39b3-134">Při implementaci hostované verze této metody používejte skvělou opatrnost.</span><span class="sxs-lookup"><span data-stu-id="e39b3-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e39b3-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e39b3-135">Requirements</span></span>  
 <span data-ttu-id="e39b3-136">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e39b3-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e39b3-137">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e39b3-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e39b3-138">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e39b3-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e39b3-139">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e39b3-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39b3-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e39b3-140">See also</span></span>

- [<span data-ttu-id="e39b3-141">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e39b3-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
