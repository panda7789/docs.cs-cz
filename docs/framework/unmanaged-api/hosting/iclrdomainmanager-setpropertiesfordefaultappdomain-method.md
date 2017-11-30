---
title: "ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fabf42c16dc41e29ca3d14e00e76797fa8f2a9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="1bd15-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="1bd15-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="1bd15-103">Nastaví vlastnosti, které se použijí k chybě při inicializaci výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="1bd15-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bd15-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bd15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bd15-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="1bd15-106">[v] Počet položek v `pwszPropertyNames` a `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="1bd15-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="1bd15-107">[v] Pole názvy vlastností, nebo hodnota null, pokud nejsou k dispozici žádné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1bd15-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="1bd15-108">Název pouze vlastnosti, která je rozpoznáno tato metoda je v současné době "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="1bd15-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="1bd15-109">[v] Pole hodnot vlastností, nebo hodnota null, pokud nejsou k dispozici žádné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1bd15-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bd15-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1bd15-110">Return Value</span></span>  
 <span data-ttu-id="1bd15-111">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="1bd15-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1bd15-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bd15-112">HRESULT</span></span>|<span data-ttu-id="1bd15-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1bd15-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bd15-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bd15-114">S_OK</span></span>|<span data-ttu-id="1bd15-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="1bd15-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="1bd15-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="1bd15-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="1bd15-117">`pwszPropertyNames`obsahuje název vlastnosti, která nebyla rozpoznána touto metodou.</span><span class="sxs-lookup"><span data-stu-id="1bd15-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd15-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bd15-118">Remarks</span></span>  
 <span data-ttu-id="1bd15-119">Hodnota vlastnosti pro "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" je seznam sestavení, které mají podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA) s <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> příznak, který má být provedeno viditelné pro částečně důvěryhodné volající výchozí aplikace domény.</span><span class="sxs-lookup"><span data-stu-id="1bd15-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd15-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bd15-120">Requirements</span></span>  
 <span data-ttu-id="1bd15-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd15-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd15-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1bd15-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1bd15-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1bd15-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bd15-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd15-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd15-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bd15-125">See Also</span></span>  
 [<span data-ttu-id="1bd15-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="1bd15-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="1bd15-127">Iclrdomainmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1bd15-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
