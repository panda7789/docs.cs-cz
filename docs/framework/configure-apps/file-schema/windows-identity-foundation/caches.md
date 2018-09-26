---
title: '&lt;Mezipaměti&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: a91a389e53354e4f5b26e1510fc2f025300d65cc
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084238"
---
# <a name="ltcachesgt"></a><span data-ttu-id="37b87-102">&lt;Mezipaměti&gt;</span><span class="sxs-lookup"><span data-stu-id="37b87-102">&lt;caches&gt;</span></span>
<span data-ttu-id="37b87-103">Zaregistruje mezipaměti používané pro tokeny relace a rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="37b87-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="37b87-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="37b87-104">\<system.identityModel></span></span>  
<span data-ttu-id="37b87-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37b87-105">\<identityConfiguration></span></span>  
<span data-ttu-id="37b87-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="37b87-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37b87-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37b87-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37b87-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="37b87-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37b87-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="37b87-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37b87-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="37b87-110">Attributes</span></span>  
 <span data-ttu-id="37b87-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="37b87-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="37b87-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37b87-112">Child Elements</span></span>  
  
|<span data-ttu-id="37b87-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="37b87-113">Element</span></span>|<span data-ttu-id="37b87-114">Popis</span><span class="sxs-lookup"><span data-stu-id="37b87-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37b87-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="37b87-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="37b87-116">Registruje mezipaměti relace tokeny služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="37b87-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="37b87-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="37b87-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="37b87-118">Registruje mezipaměti opětovného přehrání tokenu služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="37b87-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37b87-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="37b87-119">Parent Elements</span></span>  
  
|<span data-ttu-id="37b87-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="37b87-120">Element</span></span>|<span data-ttu-id="37b87-121">Popis</span><span class="sxs-lookup"><span data-stu-id="37b87-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37b87-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37b87-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="37b87-123">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="37b87-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="37b87-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37b87-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="37b87-125">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="37b87-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37b87-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37b87-126">Remarks</span></span>  
 <span data-ttu-id="37b87-127">A `<caches>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="37b87-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="37b87-128">Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="37b87-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="37b87-129">`<caches>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="37b87-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="37b87-130">Jsou reprezentovány nakonfigurovanou mezipamětí <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídy.</span><span class="sxs-lookup"><span data-stu-id="37b87-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37b87-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="37b87-131">Example</span></span>  
 <span data-ttu-id="37b87-132">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro uchování relace tokenů zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="37b87-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="37b87-133">Konfigurace se přebírá ze `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="37b87-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
