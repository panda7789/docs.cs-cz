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
ms.openlocfilehash: d39ad45e143026f40ffcf1339e923837f9e812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195850"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="ecff6-102">IHostMemoryManager::VirtualProtect – metoda</span><span class="sxs-lookup"><span data-stu-id="ecff6-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="ecff6-103">Slouží jako logická obálka odpovídající funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="ecff6-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="ecff6-104">Implementace Win32 `VirtualProtect` mění ochranu v oblasti potvrzených stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="ecff6-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecff6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecff6-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecff6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecff6-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="ecff6-107">pro Ukazatel na základní adresu virtuální paměti, jejíž atributy ochrany mají být změněny.</span><span class="sxs-lookup"><span data-stu-id="ecff6-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="ecff6-108">pro Velikost oblasti paměťových stránek (v bajtech), která se má změnit.</span><span class="sxs-lookup"><span data-stu-id="ecff6-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="ecff6-109">pro Typ ochrany paměti, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="ecff6-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="ecff6-110">mimo Ukazatel na předchozí hodnotu ochrany paměti.</span><span class="sxs-lookup"><span data-stu-id="ecff6-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecff6-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ecff6-111">Return Value</span></span>  
  
|<span data-ttu-id="ecff6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecff6-112">HRESULT</span></span>|<span data-ttu-id="ecff6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ecff6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecff6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecff6-114">S_OK</span></span>|<span data-ttu-id="ecff6-115">`VirtualProtect` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ecff6-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="ecff6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecff6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecff6-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ecff6-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecff6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecff6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecff6-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ecff6-119">The call timed out.</span></span>|  
|<span data-ttu-id="ecff6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecff6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecff6-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ecff6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecff6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecff6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecff6-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="ecff6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecff6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecff6-124">E_FAIL</span></span>|<span data-ttu-id="ecff6-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="ecff6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecff6-126">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="ecff6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecff6-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecff6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecff6-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecff6-128">Remarks</span></span>  
 <span data-ttu-id="ecff6-129">Tato implementace `VirtualProtect` vrátí hodnotu HRESULT, zatímco implementace Win32 vrátí nenulovou hodnotu pro indikaci úspěchu a nulovou hodnotu pro indikaci selhání.</span><span class="sxs-lookup"><span data-stu-id="ecff6-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="ecff6-130">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="ecff6-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecff6-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecff6-131">Requirements</span></span>  
 <span data-ttu-id="ecff6-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecff6-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecff6-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecff6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecff6-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ecff6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecff6-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecff6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecff6-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecff6-136">See also</span></span>

- [<span data-ttu-id="ecff6-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecff6-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
