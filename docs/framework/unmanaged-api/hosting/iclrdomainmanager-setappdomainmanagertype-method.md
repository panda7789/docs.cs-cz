---
title: ICLRDomainManager::SetAppDomainManagerType – metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea10f9b7d23d8ca6a94d05cac6e586b434c000d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435540"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="6234e-102">ICLRDomainManager::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="6234e-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="6234e-103">Určuje typ odvozený z <xref:System.AppDomainManager?displayProperty=nameWithType> třídu aplikace správce domény, který se použije k chybě při inicializaci výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6234e-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6234e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6234e-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6234e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6234e-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="6234e-106">[v] Zobrazovaný název sestavení, které obsahuje typ správce domény aplikace; například: "AdMgrExample, verze = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="6234e-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="6234e-107">[v] Název typu správce domény aplikace, včetně oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6234e-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="6234e-108">[v] Kombinace [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) hodnot výčtu, které poskytují informace o Správci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6234e-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6234e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6234e-109">Return Value</span></span>  
 <span data-ttu-id="6234e-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="6234e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6234e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6234e-111">HRESULT</span></span>|<span data-ttu-id="6234e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6234e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6234e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6234e-113">S_OK</span></span>|<span data-ttu-id="6234e-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="6234e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6234e-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6234e-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6234e-116">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6234e-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6234e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6234e-117">Remarks</span></span>  
 <span data-ttu-id="6234e-118">V současné době jediným definovaná hodnota `dwInitializeDomainFlags` je `eInitializeNewDomainFlags_NoSecurityChanges`, které informuje common language runtime (CLR), aby správce domény aplikace nezmění nastavení zabezpečení během provádění <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="6234e-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6234e-119">To umožňuje CLR za účelem optimalizace načítání sestavení, které mají podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA).</span><span class="sxs-lookup"><span data-stu-id="6234e-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="6234e-120">To může způsobit přináší značné vylepšení v čase spuštění Pokud přechodné uzavření této sady sestavení velká.</span><span class="sxs-lookup"><span data-stu-id="6234e-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6234e-121">Pokud hostitel Určuje `eInitializeNewDomainFlags_NoSecurityChanges` pro správce domény aplikace <xref:System.InvalidOperationException> je vyvolána, pokud je všechny pokusu upravit zabezpečení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6234e-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="6234e-122">Volání [iclrcontrol::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metoda je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="6234e-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6234e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6234e-123">Requirements</span></span>  
 <span data-ttu-id="6234e-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6234e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6234e-125">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6234e-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6234e-126">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6234e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6234e-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6234e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6234e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6234e-128">See Also</span></span>  
 [<span data-ttu-id="6234e-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="6234e-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="6234e-130">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6234e-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="6234e-131">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="6234e-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
