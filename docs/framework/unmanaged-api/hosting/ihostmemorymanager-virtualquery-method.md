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
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760100"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="ddcec-102">IHostMemoryManager::VirtualQuery – metoda</span><span class="sxs-lookup"><span data-stu-id="ddcec-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="ddcec-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="ddcec-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="ddcec-104">Implementace Win32 `VirtualQuery` načte informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="ddcec-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcec-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddcec-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddcec-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddcec-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="ddcec-107">[in] Ukazatel na adresu ve virtuální paměti, aby se dalo dotazovat.</span><span class="sxs-lookup"><span data-stu-id="ddcec-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="ddcec-108">[out] Ukazatel na strukturu, která obsahuje informace o zadané paměťové oblasti.</span><span class="sxs-lookup"><span data-stu-id="ddcec-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ddcec-109">[in] Velikost v bajtech, vyrovnávací paměti, která `lpBuffer` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="ddcec-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="ddcec-110">[out] Ukazatel na počet bajtů vrácených informace vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ddcec-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddcec-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ddcec-111">Return Value</span></span>  
  
|<span data-ttu-id="ddcec-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ddcec-112">HRESULT</span></span>|<span data-ttu-id="ddcec-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ddcec-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ddcec-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddcec-114">S_OK</span></span>|<span data-ttu-id="ddcec-115">`VirtualQuery` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ddcec-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="ddcec-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ddcec-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ddcec-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ddcec-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ddcec-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ddcec-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ddcec-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ddcec-119">The call timed out.</span></span>|  
|<span data-ttu-id="ddcec-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddcec-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ddcec-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="ddcec-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ddcec-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ddcec-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ddcec-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="ddcec-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ddcec-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ddcec-124">E_FAIL</span></span>|<span data-ttu-id="ddcec-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="ddcec-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ddcec-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ddcec-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ddcec-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ddcec-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddcec-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddcec-128">Remarks</span></span>  
 <span data-ttu-id="ddcec-129">`VirtualQuery` poskytuje informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="ddcec-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="ddcec-130">Tato implementace nastaví hodnotu vlastnosti `pResult` parametr počet bajtů, vrátí ve vyrovnávací paměti informace a vrací hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ddcec-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="ddcec-131">V rozhraní Win32 `VirtualQuery` funkce, vrácená hodnota je velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ddcec-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="ddcec-132">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="ddcec-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ddcec-133">Operační systém provádění `VirtualQuery` nesnižuje zablokování a můžete spustit až do ukončení se náhodný vlákna pozastaveno v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="ddcec-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="ddcec-134">Používejte opatrní při implementaci verze prostředí této metody.</span><span class="sxs-lookup"><span data-stu-id="ddcec-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcec-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddcec-135">Requirements</span></span>  
 <span data-ttu-id="ddcec-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddcec-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddcec-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ddcec-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ddcec-138">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddcec-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ddcec-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcec-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcec-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddcec-140">See also</span></span>

- [<span data-ttu-id="ddcec-141">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddcec-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
