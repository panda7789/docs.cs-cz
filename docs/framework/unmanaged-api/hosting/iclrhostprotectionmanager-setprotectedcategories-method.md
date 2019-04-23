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
ms.openlocfilehash: 63b6e85b6abe20e9e1f0b00648a06a31735e63c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183622"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="76019-102">ICLRHostProtectionManager::SetProtectedCategories – metoda</span><span class="sxs-lookup"><span data-stu-id="76019-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="76019-103">Určuje, které kategorie spravované typy a členy by měl být blokovaný spouštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="76019-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76019-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76019-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76019-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76019-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="76019-106">[in] Kombinace [eapicategories –](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) hodnoty, která kategorie spravované typy a členy, které by měl být blokovaný spouštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="76019-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76019-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="76019-107">Return Value</span></span>  
  
|<span data-ttu-id="76019-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76019-108">HRESULT</span></span>|<span data-ttu-id="76019-109">Popis</span><span class="sxs-lookup"><span data-stu-id="76019-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76019-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="76019-110">S_OK</span></span>|<span data-ttu-id="76019-111">`SetProtectedCategories` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="76019-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="76019-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76019-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76019-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="76019-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76019-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76019-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76019-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="76019-115">The call timed out.</span></span>|  
|<span data-ttu-id="76019-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76019-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76019-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="76019-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76019-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76019-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76019-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="76019-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76019-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76019-120">E_FAIL</span></span>|<span data-ttu-id="76019-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="76019-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76019-122">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="76019-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76019-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76019-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76019-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76019-124">Remarks</span></span>  
 <span data-ttu-id="76019-125">Každý `EApiCategories` hodnota odkazuje na seznam spravované typy a členy.</span><span class="sxs-lookup"><span data-stu-id="76019-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="76019-126">`EApiCategories` Výčet a `SetProtectedCategories` přímo souvisí s metoda na spravovanou <xref:System.Security.Permissions.HostProtectionAttribute> třídu, která slouží k označení spravované typy a členy, které ukazují možnosti odpovídající kategorií popsaných ve `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="76019-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="76019-127">Další informace najdete v tématu <xref:System.Security.Permissions.HostProtectionAttribute> a <xref:System.Security.Permissions.HostProtectionResource> výčet, který přímo odpovídá `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="76019-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76019-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76019-128">Requirements</span></span>  
 <span data-ttu-id="76019-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76019-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76019-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76019-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76019-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76019-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76019-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76019-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76019-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76019-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="76019-134">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="76019-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="76019-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76019-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="76019-136">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76019-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
