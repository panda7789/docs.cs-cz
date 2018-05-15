---
title: '&lt;Mezipaměti&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a9766b826eb7a708b4b4e99b6bd984f9fc76812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcachesgt"></a><span data-ttu-id="25151-102">&lt;Mezipaměti&gt;</span><span class="sxs-lookup"><span data-stu-id="25151-102">&lt;caches&gt;</span></span>
<span data-ttu-id="25151-103">Zaregistruje mezipamětí použít pro tokeny relace a rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="25151-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="25151-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="25151-104">\<system.identityModel></span></span>  
<span data-ttu-id="25151-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="25151-105">\<identityConfiguration></span></span>  
<span data-ttu-id="25151-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="25151-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25151-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25151-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25151-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="25151-108">Attributes and Elements</span></span>  
 <span data-ttu-id="25151-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="25151-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25151-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="25151-110">Attributes</span></span>  
 <span data-ttu-id="25151-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="25151-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25151-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="25151-112">Child Elements</span></span>  
  
|<span data-ttu-id="25151-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="25151-113">Element</span></span>|<span data-ttu-id="25151-114">Popis</span><span class="sxs-lookup"><span data-stu-id="25151-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25151-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="25151-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="25151-116">Zaregistruje mezipaměti pro tokeny relaci se službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="25151-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="25151-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="25151-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="25151-118">Zaregistruje mezipaměti opětovného přehrání tokenu se službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="25151-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25151-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="25151-119">Parent Elements</span></span>  
  
|<span data-ttu-id="25151-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="25151-120">Element</span></span>|<span data-ttu-id="25151-121">Popis</span><span class="sxs-lookup"><span data-stu-id="25151-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25151-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="25151-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="25151-123">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="25151-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="25151-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="25151-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="25151-125">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="25151-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25151-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25151-126">Remarks</span></span>  
 <span data-ttu-id="25151-127">A `<caches>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="25151-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="25151-128">Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="25151-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="25151-129">`<caches>` Element je reprezentována <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="25151-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="25151-130">Nakonfigurovanou mezipamětí jsou reprezentované pomocí <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídy.</span><span class="sxs-lookup"><span data-stu-id="25151-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25151-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="25151-131">Example</span></span>  
 <span data-ttu-id="25151-132">Následující kód XML zobrazuje konfiguraci vlastní mezipaměti pro uchování relace tokeny zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="25151-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="25151-133">Konfigurace jsou převzaty z `ClaimsAwareWebFarm` ukázka.</span><span class="sxs-lookup"><span data-stu-id="25151-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
