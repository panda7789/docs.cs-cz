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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd7c835cdc4b53c753d714216d1745eb0b80c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772929"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="7d405-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="7d405-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="7d405-103">Nastaví vlastnosti, které bude sloužit k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d405-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d405-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d405-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d405-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d405-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="7d405-106">[in] Počet položek v `pwszPropertyNames` a `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="7d405-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="7d405-107">[in] Pole názvy vlastností, nebo hodnota null, pokud nejsou žádné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d405-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="7d405-108">V současné době je vlastnost jen pro název, který je rozpoznán touto metodou "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="7d405-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="7d405-109">[in] Pole hodnoty vlastností, nebo hodnota null, pokud nejsou žádné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d405-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d405-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d405-110">Return Value</span></span>  
 <span data-ttu-id="7d405-111">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="7d405-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7d405-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d405-112">HRESULT</span></span>|<span data-ttu-id="7d405-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7d405-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d405-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d405-114">S_OK</span></span>|<span data-ttu-id="7d405-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="7d405-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="7d405-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="7d405-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="7d405-117">`pwszPropertyNames` obsahuje název vlastnosti, která nebyla rozpoznána touto metodou.</span><span class="sxs-lookup"><span data-stu-id="7d405-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d405-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d405-118">Remarks</span></span>  
 <span data-ttu-id="7d405-119">Hodnota vlastnosti pro "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" je seznam sestavení, které mají podmíněnou <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA) s <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> příznak, který má být provedeno viditelné pro částečně důvěryhodné volající výchozí aplikace domény.</span><span class="sxs-lookup"><span data-stu-id="7d405-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d405-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d405-120">Requirements</span></span>  
 <span data-ttu-id="7d405-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d405-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d405-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7d405-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d405-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d405-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d405-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d405-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d405-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d405-125">See also</span></span>

- [<span data-ttu-id="7d405-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="7d405-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="7d405-127">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d405-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
