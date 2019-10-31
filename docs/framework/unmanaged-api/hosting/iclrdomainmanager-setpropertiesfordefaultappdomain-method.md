---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: 37919be2d0ebd7d243615bc5845b0781ac13e574
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129315"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="acb05-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="acb05-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="acb05-103">Nastaví vlastnosti, které se použijí k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="acb05-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acb05-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acb05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="acb05-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="acb05-106">pro Počet položek v `pwszPropertyNames` a `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="acb05-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="acb05-107">pro Pole názvů vlastností nebo hodnotu null, pokud nejsou k dispozici žádné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="acb05-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="acb05-108">V současné době je jediným názvem vlastnosti, který je rozpoznáván touto metodou, "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="acb05-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="acb05-109">pro Pole hodnot vlastnosti nebo hodnotu null, pokud nejsou k dispozici žádné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="acb05-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acb05-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="acb05-110">Return Value</span></span>  
 <span data-ttu-id="acb05-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="acb05-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="acb05-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="acb05-112">HRESULT</span></span>|<span data-ttu-id="acb05-113">Popis</span><span class="sxs-lookup"><span data-stu-id="acb05-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="acb05-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="acb05-114">S_OK</span></span>|<span data-ttu-id="acb05-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="acb05-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="acb05-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="acb05-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="acb05-117">`pwszPropertyNames` obsahuje název vlastnosti, který tato metoda nerozpoznala.</span><span class="sxs-lookup"><span data-stu-id="acb05-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acb05-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acb05-118">Remarks</span></span>  
 <span data-ttu-id="acb05-119">Hodnota vlastnosti "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" je seznam sestavení, která mají atribut podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) s příznakem <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>, který má být viditelný pro částečně důvěryhodné volající ve výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="acb05-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb05-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acb05-120">Requirements</span></span>  
 <span data-ttu-id="acb05-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb05-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb05-122">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="acb05-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="acb05-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="acb05-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acb05-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb05-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb05-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acb05-125">See also</span></span>

- [<span data-ttu-id="acb05-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="acb05-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="acb05-127">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acb05-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
