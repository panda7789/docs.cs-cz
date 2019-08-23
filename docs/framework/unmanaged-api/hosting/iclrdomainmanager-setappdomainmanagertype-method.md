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
ms.openlocfilehash: 9b142f1a05036eddf44c69d8b7da95091dc8f445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963092"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="05736-102">ICLRDomainManager::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="05736-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="05736-103">Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="05736-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05736-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05736-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05736-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05736-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="05736-106">pro Zobrazovaný název sestavení obsahujícího typ Správce aplikační domény; například: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="05736-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="05736-107">pro Název typu správce aplikační domény, včetně oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="05736-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="05736-108">pro Kombinace hodnot výčtu [EInitializeNewDomainFlags –](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) , které poskytují informace o Správci aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="05736-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05736-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05736-109">Return Value</span></span>  
 <span data-ttu-id="05736-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="05736-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="05736-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05736-111">HRESULT</span></span>|<span data-ttu-id="05736-112">Popis</span><span class="sxs-lookup"><span data-stu-id="05736-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05736-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="05736-113">S_OK</span></span>|<span data-ttu-id="05736-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="05736-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="05736-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05736-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05736-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="05736-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05736-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05736-117">Remarks</span></span>  
 <span data-ttu-id="05736-118">V současné době je jediná definovaná hodnota `dwInitializeDomainFlags` pro `eInitializeNewDomainFlags_NoSecurityChanges`je, což znamená, že modul CLR (Common Language Runtime), který správce aplikační domény nemění nastavení zabezpečení <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> při provádění metody.</span><span class="sxs-lookup"><span data-stu-id="05736-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="05736-119">To umožňuje, aby CLR optimalizuje načítání sestavení, která mají podmíněný <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA).</span><span class="sxs-lookup"><span data-stu-id="05736-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="05736-120">To může mít za následek výrazné zlepšení doby spuštění, pokud je přenosná uzávěra této sady sestavení velká.</span><span class="sxs-lookup"><span data-stu-id="05736-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="05736-121">Pokud hostitel určí `eInitializeNewDomainFlags_NoSecurityChanges` pro správce aplikační domény <xref:System.InvalidOperationException> , je vyvolána, pokud je proveden libovolný pokus o změnu zabezpečení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="05736-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="05736-122">Volání metody [ICLRControl:: SetAppDomainManagerType –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="05736-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05736-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05736-123">Requirements</span></span>  
 <span data-ttu-id="05736-124">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05736-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05736-125">**Hlaviček** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="05736-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="05736-126">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="05736-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05736-127">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05736-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05736-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05736-128">See also</span></span>

- [<span data-ttu-id="05736-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="05736-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="05736-130">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05736-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="05736-131">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="05736-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
