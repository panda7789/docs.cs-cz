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
ms.openlocfilehash: 5cf6f942add3d090cf830e71a545b9f4d4f69f00
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703172"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="d6088-102">ICLRHostProtectionManager::SetProtectedCategories – metoda</span><span class="sxs-lookup"><span data-stu-id="d6088-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="d6088-103">Určuje, které kategorie spravovaných typů a členů by měly být zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="d6088-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6088-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6088-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6088-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6088-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="d6088-106">pro Kombinace hodnot [EApiCategories –](eapicategories-enumeration.md) , která označuje, které kategorie spravovaných typů a členů by měly být zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="d6088-106">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6088-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6088-107">Return Value</span></span>  
  
|<span data-ttu-id="d6088-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6088-108">HRESULT</span></span>|<span data-ttu-id="d6088-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d6088-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6088-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6088-110">S_OK</span></span>|<span data-ttu-id="d6088-111">`SetProtectedCategories`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d6088-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="d6088-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6088-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6088-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d6088-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6088-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6088-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6088-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d6088-115">The call timed out.</span></span>|  
|<span data-ttu-id="d6088-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6088-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6088-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d6088-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6088-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6088-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6088-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d6088-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6088-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6088-120">E_FAIL</span></span>|<span data-ttu-id="d6088-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d6088-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6088-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="d6088-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6088-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d6088-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6088-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6088-124">Remarks</span></span>  
 <span data-ttu-id="d6088-125">Každá `EApiCategories` hodnota odkazuje na seznam spravovaných typů a členů.</span><span class="sxs-lookup"><span data-stu-id="d6088-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="d6088-126">`EApiCategories`Výčet a `SetProtectedCategories` Metoda přímo souvisí se spravovanou <xref:System.Security.Permissions.HostProtectionAttribute> třídou, která se používá k označení spravovaných typů a členů, které zpřístupňují možnosti odpovídající kategoriím popsaným v `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="d6088-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="d6088-127">Další informace naleznete v tématu <xref:System.Security.Permissions.HostProtectionAttribute> a <xref:System.Security.Permissions.HostProtectionResource> výčet, který přímo odpovídá `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="d6088-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6088-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6088-128">Requirements</span></span>  
 <span data-ttu-id="d6088-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6088-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6088-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6088-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6088-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6088-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6088-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6088-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6088-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6088-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="d6088-134">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="d6088-134">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="d6088-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6088-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d6088-136">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6088-136">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
