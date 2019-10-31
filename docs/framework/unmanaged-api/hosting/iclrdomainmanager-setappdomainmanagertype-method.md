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
ms.openlocfilehash: 5c61e2e1208cec0bda1492964a8d02bd71f5a1c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129321"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="27569-102">ICLRDomainManager::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="27569-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="27569-103">Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="27569-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27569-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27569-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27569-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27569-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="27569-106">pro Zobrazovaný název sestavení obsahujícího typ Správce aplikační domény; například: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="27569-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="27569-107">pro Název typu správce aplikační domény, včetně oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="27569-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="27569-108">pro Kombinace hodnot výčtu [EInitializeNewDomainFlags –](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) , které poskytují informace o Správci aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="27569-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27569-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="27569-109">Return Value</span></span>  
 <span data-ttu-id="27569-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="27569-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="27569-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27569-111">HRESULT</span></span>|<span data-ttu-id="27569-112">Popis</span><span class="sxs-lookup"><span data-stu-id="27569-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27569-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="27569-113">S_OK</span></span>|<span data-ttu-id="27569-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="27569-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="27569-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="27569-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="27569-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="27569-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27569-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27569-117">Remarks</span></span>  
 <span data-ttu-id="27569-118">V současné době je jediná definovaná hodnota pro `dwInitializeDomainFlags` `eInitializeNewDomainFlags_NoSecurityChanges`, která určuje modul CLR (Common Language Runtime), který správce aplikační domény nemění nastavení zabezpečení během provádění metody <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27569-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="27569-119">To umožňuje, aby CLR optimalizuje načítání sestavení, která mají atribut podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA).</span><span class="sxs-lookup"><span data-stu-id="27569-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="27569-120">To může mít za následek výrazné zlepšení doby spuštění, pokud je přenosná uzávěra této sady sestavení velká.</span><span class="sxs-lookup"><span data-stu-id="27569-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="27569-121">Pokud hostitel určí `eInitializeNewDomainFlags_NoSecurityChanges` pro správce aplikačních domén, je vyvolána <xref:System.InvalidOperationException>, pokud se provede libovolný pokus o změnu zabezpečení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="27569-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="27569-122">Volání metody [ICLRControl:: SetAppDomainManagerType –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="27569-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27569-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27569-123">Requirements</span></span>  
 <span data-ttu-id="27569-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27569-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27569-125">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="27569-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="27569-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27569-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27569-127">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27569-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27569-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27569-128">See also</span></span>

- [<span data-ttu-id="27569-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="27569-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="27569-130">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27569-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="27569-131">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="27569-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
