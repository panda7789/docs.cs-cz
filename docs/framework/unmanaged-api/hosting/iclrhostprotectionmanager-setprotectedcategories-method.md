---
title: ICLRHostProtectionManager::SetProtectedCategories – metoda
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: e3f2429462b4454e87690d98ad9fb446574add91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141035"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="44fbb-102">ICLRHostProtectionManager::SetProtectedCategories – metoda</span><span class="sxs-lookup"><span data-stu-id="44fbb-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="44fbb-103">Určuje, které kategorie spravovaných typů a členů by měly být zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="44fbb-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44fbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44fbb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44fbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44fbb-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="44fbb-106">pro Kombinace hodnot [EApiCategories –](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) , která označuje, které kategorie spravovaných typů a členů by měly být zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="44fbb-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44fbb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44fbb-107">Return Value</span></span>  
  
|<span data-ttu-id="44fbb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44fbb-108">HRESULT</span></span>|<span data-ttu-id="44fbb-109">Popis</span><span class="sxs-lookup"><span data-stu-id="44fbb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44fbb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="44fbb-110">S_OK</span></span>|<span data-ttu-id="44fbb-111">`SetProtectedCategories` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="44fbb-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="44fbb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44fbb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44fbb-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="44fbb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44fbb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44fbb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44fbb-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="44fbb-115">The call timed out.</span></span>|  
|<span data-ttu-id="44fbb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44fbb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44fbb-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="44fbb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44fbb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44fbb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44fbb-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="44fbb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44fbb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44fbb-120">E_FAIL</span></span>|<span data-ttu-id="44fbb-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="44fbb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44fbb-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="44fbb-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44fbb-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44fbb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44fbb-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44fbb-124">Remarks</span></span>  
 <span data-ttu-id="44fbb-125">Každá hodnota `EApiCategories` odkazuje na seznam spravovaných typů a členů.</span><span class="sxs-lookup"><span data-stu-id="44fbb-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="44fbb-126">Výčet `EApiCategories` a metoda `SetProtectedCategories` přímo souvisí se spravovanou třídou <xref:System.Security.Permissions.HostProtectionAttribute>, která se používá k označení spravovaných typů a členů, které zpřístupňují funkce odpovídající kategoriím popsaným v `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="44fbb-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="44fbb-127">Další informace naleznete v tématu <xref:System.Security.Permissions.HostProtectionAttribute> a <xref:System.Security.Permissions.HostProtectionResource> výčet, který přímo odpovídá `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="44fbb-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44fbb-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44fbb-128">Requirements</span></span>  
 <span data-ttu-id="44fbb-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44fbb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44fbb-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44fbb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44fbb-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="44fbb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44fbb-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44fbb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44fbb-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44fbb-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="44fbb-134">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="44fbb-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="44fbb-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44fbb-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="44fbb-136">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44fbb-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
