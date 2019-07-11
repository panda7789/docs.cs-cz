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
ms.openlocfilehash: 684d5e41e1d7cee2775aa0988d33a974315eac4e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772738"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="96ec3-102">IHostMemoryManager::VirtualQuery – metoda</span><span class="sxs-lookup"><span data-stu-id="96ec3-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="96ec3-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="96ec3-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="96ec3-104">Implementace Win32 `VirtualQuery` načte informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="96ec3-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ec3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96ec3-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96ec3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="96ec3-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="96ec3-107">[in] Ukazatel na adresu ve virtuální paměti, aby se dalo dotazovat.</span><span class="sxs-lookup"><span data-stu-id="96ec3-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="96ec3-108">[out] Ukazatel na strukturu, která obsahuje informace o zadané paměťové oblasti.</span><span class="sxs-lookup"><span data-stu-id="96ec3-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="96ec3-109">[in] Velikost v bajtech, vyrovnávací paměti, která `lpBuffer` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="96ec3-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="96ec3-110">[out] Ukazatel na počet bajtů vrácených informace vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="96ec3-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96ec3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96ec3-111">Return Value</span></span>  
  
|<span data-ttu-id="96ec3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96ec3-112">HRESULT</span></span>|<span data-ttu-id="96ec3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="96ec3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96ec3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="96ec3-114">S_OK</span></span>|<span data-ttu-id="96ec3-115">`VirtualQuery` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="96ec3-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="96ec3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="96ec3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="96ec3-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="96ec3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="96ec3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="96ec3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="96ec3-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="96ec3-119">The call timed out.</span></span>|  
|<span data-ttu-id="96ec3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="96ec3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="96ec3-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="96ec3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="96ec3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="96ec3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="96ec3-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="96ec3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="96ec3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="96ec3-124">E_FAIL</span></span>|<span data-ttu-id="96ec3-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="96ec3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="96ec3-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="96ec3-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="96ec3-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="96ec3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96ec3-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96ec3-128">Remarks</span></span>  
 <span data-ttu-id="96ec3-129">`VirtualQuery` poskytuje informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="96ec3-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="96ec3-130">Tato implementace nastaví hodnotu vlastnosti `pResult` parametr počet bajtů, vrátí ve vyrovnávací paměti informace a vrací hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="96ec3-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="96ec3-131">V rozhraní Win32 `VirtualQuery` funkce, vrácená hodnota je velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="96ec3-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="96ec3-132">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="96ec3-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96ec3-133">Operační systém provádění `VirtualQuery` nesnižuje zablokování a můžete spustit až do ukončení se náhodný vlákna pozastaveno v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="96ec3-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="96ec3-134">Používejte opatrní při implementaci verze prostředí této metody.</span><span class="sxs-lookup"><span data-stu-id="96ec3-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ec3-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96ec3-135">Requirements</span></span>  
 <span data-ttu-id="96ec3-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96ec3-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ec3-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96ec3-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96ec3-138">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96ec3-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96ec3-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ec3-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ec3-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96ec3-140">See also</span></span>

- [<span data-ttu-id="96ec3-141">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96ec3-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
