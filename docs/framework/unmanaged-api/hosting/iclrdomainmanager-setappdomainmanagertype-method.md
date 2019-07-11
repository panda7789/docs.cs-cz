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
ms.openlocfilehash: 28feddffff7dc5dba1860b3d2d1327a17bd08190
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772949"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="ae382-102">ICLRDomainManager::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="ae382-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="ae382-103">Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídu správce domény aplikace, který se použije k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae382-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae382-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae382-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae382-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae382-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="ae382-106">[in] Zobrazovaný název sestavení obsahující typ správce domény aplikace; Příklad: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="ae382-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="ae382-107">[in] Název typu pro správce domény aplikace, včetně oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ae382-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="ae382-108">[in] Kombinace [einitializenewdomainflags –](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) hodnot výčtu, která poskytují informace o Správci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae382-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae382-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ae382-109">Return Value</span></span>  
 <span data-ttu-id="ae382-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="ae382-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ae382-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae382-111">HRESULT</span></span>|<span data-ttu-id="ae382-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ae382-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae382-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae382-113">S_OK</span></span>|<span data-ttu-id="ae382-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ae382-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ae382-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae382-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae382-116">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ae382-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae382-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae382-117">Remarks</span></span>  
 <span data-ttu-id="ae382-118">V současné době pouze hodnota definovaná pro `dwInitializeDomainFlags` je `eInitializeNewDomainFlags_NoSecurityChanges`, který říká common language runtime (CLR), správce domény aplikace nebude během provádění měnit nastavení zabezpečení <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ae382-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae382-119">To umožňuje modulu CLR pro optimalizaci načítání sestavení, která mají podmíněnou <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA).</span><span class="sxs-lookup"><span data-stu-id="ae382-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="ae382-120">Pokud je velká přechodné uzavření tuto sadu sestavení, to může vést výrazné zlepšení času spuštění.</span><span class="sxs-lookup"><span data-stu-id="ae382-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae382-121">Pokud hostitele Určuje `eInitializeNewDomainFlags_NoSecurityChanges` pro správce domény aplikace <xref:System.InvalidOperationException> je vyvolána, pokud žádné pokusu o změny zabezpečení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae382-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="ae382-122">Volání [iclrcontrol::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metoda je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="ae382-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae382-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae382-123">Requirements</span></span>  
 <span data-ttu-id="ae382-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae382-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae382-125">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ae382-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ae382-126">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae382-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae382-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae382-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae382-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae382-128">See also</span></span>

- [<span data-ttu-id="ae382-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="ae382-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="ae382-130">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae382-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="ae382-131">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="ae382-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
