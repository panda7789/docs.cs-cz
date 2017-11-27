---
title: "ICorRuntimeHost::CreateDomainEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 042befa2dd96ad9f6e6dd3069ba2c4aabcd146fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="8580d-102">ICorRuntimeHost::CreateDomainEx – metoda</span><span class="sxs-lookup"><span data-stu-id="8580d-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="8580d-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="8580d-103">Creates an application domain.</span></span> <span data-ttu-id="8580d-104">Volající obdrží ukazatele rozhraní, typu <xref:System._AppDomain>, do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8580d-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8580d-105">Tato metoda umožňuje volajícímu předat instanci iappdomainsetup – Chcete-li konfigurovat další funkce vrácený <xref:System._AppDomain> instance.</span><span class="sxs-lookup"><span data-stu-id="8580d-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8580d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8580d-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8580d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8580d-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="8580d-108">[v] Volitelný parametr dávat popisný název domény.</span><span class="sxs-lookup"><span data-stu-id="8580d-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="8580d-109">Tento popisný název zobrazený ve uživatelského rozhraní, jako je například ladicí programy k identifikaci domény.</span><span class="sxs-lookup"><span data-stu-id="8580d-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="8580d-110">[v] Ukazatele volitelné rozhraní typu `IAppDomainSetup`, získaných voláním [icorruntimehost::createdomainsetup –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8580d-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="8580d-111">[v] Volitelné pole ukazatele na `IIdentity` instancí, které představují důkaz namapovat prostřednictvím zásad zabezpečení pro vytvoření sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="8580d-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="8580d-112">`IIdentity` Objektu je možné získat volání [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8580d-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="8580d-113">[out] Ukazatele rozhraní typu <xref:System._AppDomain> na instanci <xref:System.AppDomain?displayProperty=nameWithType> který lze použít k podrobnějšímu řízení domény.</span><span class="sxs-lookup"><span data-stu-id="8580d-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8580d-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8580d-114">Return Value</span></span>  
  
|<span data-ttu-id="8580d-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8580d-115">HRESULT</span></span>|<span data-ttu-id="8580d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="8580d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8580d-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="8580d-117">S_OK</span></span>|<span data-ttu-id="8580d-118">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8580d-118">The operation was successful.</span></span>|  
|<span data-ttu-id="8580d-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8580d-119">S_FALSE</span></span>|<span data-ttu-id="8580d-120">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="8580d-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8580d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8580d-121">E_FAIL</span></span>|<span data-ttu-id="8580d-122">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="8580d-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8580d-123">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="8580d-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8580d-124">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8580d-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8580d-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8580d-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8580d-126">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8580d-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8580d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8580d-127">Remarks</span></span>  
 <span data-ttu-id="8580d-128">`CreateDomainEx`rozšiřuje možnosti [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) tím, že volající předávat `IAppDomainSetup` instance s hodnoty vlastností pro konfigurace domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8580d-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8580d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8580d-129">Requirements</span></span>  
 <span data-ttu-id="8580d-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8580d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8580d-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8580d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8580d-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8580d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8580d-133">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8580d-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8580d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="8580d-134">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="8580d-135">CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="8580d-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [<span data-ttu-id="8580d-136">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8580d-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
