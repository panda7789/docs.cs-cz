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
ms.openlocfilehash: 1aa4ab44fc8ef1033dcef1a9b36d7487da86cd58
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779356"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="2c2bb-102">IHostMemoryManager::VirtualProtect – metoda</span><span class="sxs-lookup"><span data-stu-id="2c2bb-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="2c2bb-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="2c2bb-104">Implementace Win32 `VirtualProtect` změní ochrany v oblasti potvrzené stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c2bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c2bb-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c2bb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c2bb-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="2c2bb-107">[in] Ukazatel na základní adresu virtuální paměti, jejichž atributy ochrany se změnit.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="2c2bb-108">[in] Velikost v bajtech, oblasti paměťových stránek změnit.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="2c2bb-109">[in] Typ ochrany paměti, aby mohli použít.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="2c2bb-110">[out] Ukazatel na hodnotu předchozí ochrana paměti.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c2bb-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2c2bb-111">Return Value</span></span>  
  
|<span data-ttu-id="2c2bb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c2bb-112">HRESULT</span></span>|<span data-ttu-id="2c2bb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2c2bb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c2bb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c2bb-114">S_OK</span></span>|<span data-ttu-id="2c2bb-115">`VirtualProtect` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="2c2bb-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c2bb-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c2bb-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c2bb-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c2bb-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c2bb-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-119">The call timed out.</span></span>|  
|<span data-ttu-id="2c2bb-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c2bb-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c2bb-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c2bb-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c2bb-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c2bb-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c2bb-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c2bb-124">E_FAIL</span></span>|<span data-ttu-id="2c2bb-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c2bb-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c2bb-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c2bb-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c2bb-128">Remarks</span></span>  
 <span data-ttu-id="2c2bb-129">Tato implementace `VirtualProtect` vrací hodnotu HRESULT, zatímco implementace Win32 vrací nenulovou hodnotu, čímž indikuje úspěšné provedení a hodnotu 0 označující selhání.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="2c2bb-130">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="2c2bb-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c2bb-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c2bb-131">Requirements</span></span>  
 <span data-ttu-id="2c2bb-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c2bb-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c2bb-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c2bb-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c2bb-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c2bb-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c2bb-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c2bb-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2bb-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c2bb-136">See also</span></span>

- [<span data-ttu-id="2c2bb-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c2bb-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
