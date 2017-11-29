---
title: "ICLRDomainManager::SetAppDomainManagerType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17c99d21155d8f985ea455e171067855edcafedc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="68c00-102">ICLRDomainManager::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="68c00-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="68c00-103">Určuje typ odvozený z <xref:System.AppDomainManager?displayProperty=nameWithType> třídu aplikace správce domény, který se použije k chybě při inicializaci výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="68c00-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68c00-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68c00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68c00-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="68c00-106">[v] Zobrazovaný název sestavení, které obsahuje typ správce domény aplikace; například: "AdMgrExample, verze = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="68c00-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="68c00-107">[v] Název typu správce domény aplikace, včetně oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="68c00-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="68c00-108">[v] Kombinace [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) hodnot výčtu, které poskytují informace o Správci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="68c00-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68c00-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="68c00-109">Return Value</span></span>  
 <span data-ttu-id="68c00-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="68c00-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="68c00-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68c00-111">HRESULT</span></span>|<span data-ttu-id="68c00-112">Popis</span><span class="sxs-lookup"><span data-stu-id="68c00-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68c00-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="68c00-113">S_OK</span></span>|<span data-ttu-id="68c00-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="68c00-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="68c00-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68c00-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68c00-116">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="68c00-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68c00-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68c00-117">Remarks</span></span>  
 <span data-ttu-id="68c00-118">V současné době jediným definovaná hodnota `dwInitializeDomainFlags` je `eInitializeNewDomainFlags_NoSecurityChanges`, které informuje common language runtime (CLR), aby správce domény aplikace nezmění nastavení zabezpečení během provádění <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="68c00-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="68c00-119">To umožňuje CLR za účelem optimalizace načítání sestavení, které mají podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA).</span><span class="sxs-lookup"><span data-stu-id="68c00-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="68c00-120">To může způsobit přináší značné vylepšení v čase spuštění Pokud přechodné uzavření této sady sestavení velká.</span><span class="sxs-lookup"><span data-stu-id="68c00-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68c00-121">Pokud hostitel Určuje `eInitializeNewDomainFlags_NoSecurityChanges` pro správce domény aplikace <xref:System.InvalidOperationException> je vyvolána, pokud je všechny pokusu upravit zabezpečení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="68c00-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="68c00-122">Volání [iclrcontrol::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metoda je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="68c00-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68c00-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68c00-123">Requirements</span></span>  
 <span data-ttu-id="68c00-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68c00-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68c00-125">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="68c00-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68c00-126">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68c00-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68c00-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68c00-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c00-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="68c00-128">See Also</span></span>  
 [<span data-ttu-id="68c00-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="68c00-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="68c00-130">Iclrdomainmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68c00-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="68c00-131">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="68c00-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
