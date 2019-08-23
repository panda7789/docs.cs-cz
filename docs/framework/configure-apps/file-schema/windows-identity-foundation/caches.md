---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 5ad75ae18772d6e7c724f2cbf40c1e3083d5c345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941968"
---
# <a name="caches"></a><span data-ttu-id="cf6a4-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="cf6a4-101">\<caches></span></span>
<span data-ttu-id="cf6a4-102">Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="cf6a4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cf6a4-103">\<system.identityModel></span></span>  
<span data-ttu-id="cf6a4-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cf6a4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="cf6a4-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="cf6a4-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf6a4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf6a4-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf6a4-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cf6a4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cf6a4-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf6a4-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="cf6a4-109">Attributes</span></span>  
 <span data-ttu-id="cf6a4-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf6a4-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf6a4-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cf6a4-111">Child Elements</span></span>  
  
|<span data-ttu-id="cf6a4-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf6a4-112">Element</span></span>|<span data-ttu-id="cf6a4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cf6a4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf6a4-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="cf6a4-114">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="cf6a4-115">Registruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="cf6a4-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="cf6a4-116">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="cf6a4-117">Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf6a4-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cf6a4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cf6a4-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf6a4-119">Element</span></span>|<span data-ttu-id="cf6a4-120">Popis</span><span class="sxs-lookup"><span data-stu-id="cf6a4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf6a4-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cf6a4-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="cf6a4-122">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="cf6a4-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="cf6a4-123">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="cf6a4-124">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf6a4-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf6a4-125">Remarks</span></span>  
 <span data-ttu-id="cf6a4-126">Element lze zadat na úrovni služby `<identityConfiguration>` pod prvkem nebo na úrovni kolekce `<securityTokenHandlerConfiguration>` obslužné rutiny tokenu zabezpečení pod prvkem. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="cf6a4-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="cf6a4-127">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="cf6a4-128">Element je reprezentován <xref:System.IdentityModel.Configuration.IdentityModelCachesElement>třídou. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="cf6a4-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="cf6a4-129">Nakonfigurované mezipaměti jsou reprezentovány <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídou.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf6a4-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf6a4-130">Example</span></span>  
 <span data-ttu-id="cf6a4-131">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro tokeny zabezpečení relace (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="cf6a4-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="cf6a4-132">Konfigurace je pořízena z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="cf6a4-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
