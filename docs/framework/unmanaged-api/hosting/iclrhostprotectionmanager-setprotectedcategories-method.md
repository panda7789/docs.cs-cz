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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6c93566d0909f1dbef46862760d47ede478d51a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434535"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="548a9-102">ICLRHostProtectionManager::SetProtectedCategories – metoda</span><span class="sxs-lookup"><span data-stu-id="548a9-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="548a9-103">Určuje, které kategorie spravované typy a členy by se zablokovat ve spuštění v částečně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="548a9-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="548a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="548a9-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="548a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="548a9-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="548a9-106">[v] Kombinace [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) hodnoty, označující kategorie, které spravované typy a členy by se zablokovat ve spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="548a9-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="548a9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="548a9-107">Return Value</span></span>  
  
|<span data-ttu-id="548a9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="548a9-108">HRESULT</span></span>|<span data-ttu-id="548a9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="548a9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="548a9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="548a9-110">S_OK</span></span>|<span data-ttu-id="548a9-111">`SetProtectedCategories` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="548a9-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="548a9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="548a9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="548a9-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="548a9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="548a9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="548a9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="548a9-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="548a9-115">The call timed out.</span></span>|  
|<span data-ttu-id="548a9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="548a9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="548a9-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="548a9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="548a9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="548a9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="548a9-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="548a9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="548a9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="548a9-120">E_FAIL</span></span>|<span data-ttu-id="548a9-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="548a9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="548a9-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="548a9-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="548a9-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="548a9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="548a9-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="548a9-124">Remarks</span></span>  
 <span data-ttu-id="548a9-125">Každý `EApiCategories` hodnota se odkazuje na seznam spravované typy a členy.</span><span class="sxs-lookup"><span data-stu-id="548a9-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="548a9-126">`EApiCategories` Výčet a `SetProtectedCategories` přímo souvisí s metoda na spravovaný <xref:System.Security.Permissions.HostProtectionAttribute> třídy, která slouží k označení spravované typy a členy, které zveřejňují možnosti odpovídající kategorie popsaného `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="548a9-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="548a9-127">Další informace najdete v tématu <xref:System.Security.Permissions.HostProtectionAttribute> a <xref:System.Security.Permissions.HostProtectionResource> výčtu, který přímo odpovídá `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="548a9-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="548a9-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="548a9-128">Requirements</span></span>  
 <span data-ttu-id="548a9-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="548a9-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="548a9-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="548a9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="548a9-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="548a9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="548a9-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="548a9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548a9-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="548a9-133">See Also</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [<span data-ttu-id="548a9-134">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="548a9-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="548a9-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="548a9-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="548a9-136">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="548a9-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
