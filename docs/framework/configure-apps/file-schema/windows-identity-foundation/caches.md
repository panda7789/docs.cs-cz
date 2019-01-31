---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: b1d04280ef993297102d446ba5a7db54e8404dd8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285659"
---
# <a name="caches"></a><span data-ttu-id="25081-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="25081-101">\<caches></span></span>
<span data-ttu-id="25081-102">Zaregistruje mezipaměti používané pro tokeny relace a rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="25081-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="25081-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="25081-103">\<system.identityModel></span></span>  
<span data-ttu-id="25081-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="25081-104">\<identityConfiguration></span></span>  
<span data-ttu-id="25081-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="25081-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25081-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25081-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25081-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="25081-107">Attributes and Elements</span></span>  
 <span data-ttu-id="25081-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="25081-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25081-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="25081-109">Attributes</span></span>  
 <span data-ttu-id="25081-110">Žádná</span><span class="sxs-lookup"><span data-stu-id="25081-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25081-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="25081-111">Child Elements</span></span>  
  
|<span data-ttu-id="25081-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="25081-112">Element</span></span>|<span data-ttu-id="25081-113">Popis</span><span class="sxs-lookup"><span data-stu-id="25081-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25081-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="25081-114">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="25081-115">Registruje mezipaměti relace tokeny služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="25081-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="25081-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="25081-116">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="25081-117">Registruje mezipaměti opětovného přehrání tokenu služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="25081-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25081-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="25081-118">Parent Elements</span></span>  
  
|<span data-ttu-id="25081-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="25081-119">Element</span></span>|<span data-ttu-id="25081-120">Popis</span><span class="sxs-lookup"><span data-stu-id="25081-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25081-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="25081-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="25081-122">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="25081-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="25081-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="25081-123">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="25081-124">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="25081-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25081-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25081-125">Remarks</span></span>  
 <span data-ttu-id="25081-126">A `<caches>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="25081-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="25081-127">Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="25081-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="25081-128">`<caches>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="25081-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="25081-129">Jsou reprezentovány nakonfigurovanou mezipamětí <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídy.</span><span class="sxs-lookup"><span data-stu-id="25081-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25081-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="25081-130">Example</span></span>  
 <span data-ttu-id="25081-131">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro uchování relace tokenů zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="25081-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="25081-132">Konfigurace se přebírá ze `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="25081-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
