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
ms.openlocfilehash: 89b3f9f248a445cc0568236d6a1df14269de4187
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615693"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="d1703-102">ICLRDomainManager::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="d1703-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="d1703-103">Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1703-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1703-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1703-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1703-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1703-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="d1703-106">pro Zobrazovaný název sestavení obsahujícího typ Správce aplikační domény; například: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="d1703-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="d1703-107">pro Název typu správce aplikační domény, včetně oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d1703-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="d1703-108">pro Kombinace hodnot výčtu [EInitializeNewDomainFlags –](einitializenewdomainflags-enumeration.md) , které poskytují informace o Správci aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="d1703-108">[in] A combination of [EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1703-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d1703-109">Return Value</span></span>  
 <span data-ttu-id="d1703-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="d1703-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d1703-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1703-111">HRESULT</span></span>|<span data-ttu-id="d1703-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d1703-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1703-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1703-113">S_OK</span></span>|<span data-ttu-id="d1703-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="d1703-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d1703-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1703-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1703-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d1703-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1703-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1703-117">Remarks</span></span>  
 <span data-ttu-id="d1703-118">V současné době je jediná definovaná hodnota pro `dwInitializeDomainFlags` je `eInitializeNewDomainFlags_NoSecurityChanges` , což znamená, že modul CLR (Common Language Runtime), který správce aplikační domény nemění nastavení zabezpečení při provádění <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d1703-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d1703-119">To umožňuje, aby CLR optimalizuje načítání sestavení, která mají podmíněný <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA).</span><span class="sxs-lookup"><span data-stu-id="d1703-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="d1703-120">To může mít za následek výrazné zlepšení doby spuštění, pokud je přenosná uzávěra této sady sestavení velká.</span><span class="sxs-lookup"><span data-stu-id="d1703-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1703-121">Pokud hostitel určí `eInitializeNewDomainFlags_NoSecurityChanges` pro správce aplikační domény, <xref:System.InvalidOperationException> je vyvolána, pokud je proveden libovolný pokus o změnu zabezpečení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1703-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="d1703-122">Volání metody [ICLRControl:: SetAppDomainManagerType –](iclrcontrol-setappdomainmanagertype-method.md)je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None` .</span><span class="sxs-lookup"><span data-stu-id="d1703-122">Calling the [ICLRControl::SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1703-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1703-123">Requirements</span></span>  
 <span data-ttu-id="d1703-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1703-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1703-125">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d1703-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d1703-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d1703-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1703-127">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1703-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1703-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1703-128">See also</span></span>

- [<span data-ttu-id="d1703-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="d1703-129">Hosting</span></span>](index.md)
- [<span data-ttu-id="d1703-130">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1703-130">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
- [<span data-ttu-id="d1703-131">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="d1703-131">EInitializeNewDomainFlags Enumeration</span></span>](einitializenewdomainflags-enumeration.md)
