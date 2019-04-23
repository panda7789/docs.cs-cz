---
title: IHostMemoryManager::VirtualProtect – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62aa6b1d9be86a9b60abf894d67555f706e6a8ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139903"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="f810e-102">IHostMemoryManager::VirtualProtect – metoda</span><span class="sxs-lookup"><span data-stu-id="f810e-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="f810e-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="f810e-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="f810e-104">Implementace Win32 `VirtualProtect` změní ochrany v oblasti potvrzené stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="f810e-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f810e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f810e-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f810e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f810e-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="f810e-107">[in] Ukazatel na základní adresu virtuální paměti, jejichž atributy ochrany se změnit.</span><span class="sxs-lookup"><span data-stu-id="f810e-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="f810e-108">[in] Velikost v bajtech, oblasti paměťových stránek změnit.</span><span class="sxs-lookup"><span data-stu-id="f810e-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="f810e-109">[in] Typ ochrany paměti, aby mohli použít.</span><span class="sxs-lookup"><span data-stu-id="f810e-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="f810e-110">[out] Ukazatel na hodnotu předchozí ochrana paměti.</span><span class="sxs-lookup"><span data-stu-id="f810e-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f810e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f810e-111">Return Value</span></span>  
  
|<span data-ttu-id="f810e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f810e-112">HRESULT</span></span>|<span data-ttu-id="f810e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f810e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f810e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f810e-114">S_OK</span></span>|<span data-ttu-id="f810e-115">`VirtualProtect` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f810e-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="f810e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f810e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f810e-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f810e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f810e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f810e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f810e-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f810e-119">The call timed out.</span></span>|  
|<span data-ttu-id="f810e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f810e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f810e-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f810e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f810e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f810e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f810e-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f810e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f810e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f810e-124">E_FAIL</span></span>|<span data-ttu-id="f810e-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f810e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f810e-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f810e-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f810e-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f810e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f810e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f810e-128">Remarks</span></span>  
 <span data-ttu-id="f810e-129">Tato implementace `VirtualProtect` vrací hodnotu HRESULT, zatímco implementace Win32 vrací nenulovou hodnotu, čímž indikuje úspěšné provedení a hodnotu 0 označující selhání.</span><span class="sxs-lookup"><span data-stu-id="f810e-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="f810e-130">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="f810e-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f810e-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f810e-131">Requirements</span></span>  
 <span data-ttu-id="f810e-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f810e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f810e-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f810e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f810e-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f810e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f810e-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f810e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f810e-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f810e-136">See also</span></span>

- [<span data-ttu-id="f810e-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f810e-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
