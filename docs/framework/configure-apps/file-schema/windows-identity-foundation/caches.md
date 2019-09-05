---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252165"
---
# <a name="caches"></a><span data-ttu-id="64d6f-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="64d6f-101">\<caches></span></span>
<span data-ttu-id="64d6f-102">Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="64d6f-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
<span data-ttu-id="64d6f-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="64d6f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="64d6f-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="64d6f-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="64d6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="64d6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="64d6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ukládá do mezipaměti >**</span><span class="sxs-lookup"><span data-stu-id="64d6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d6f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64d6f-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64d6f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="64d6f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="64d6f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="64d6f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64d6f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="64d6f-110">Attributes</span></span>  
 <span data-ttu-id="64d6f-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="64d6f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64d6f-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="64d6f-112">Child Elements</span></span>  
  
|<span data-ttu-id="64d6f-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="64d6f-113">Element</span></span>|<span data-ttu-id="64d6f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="64d6f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64d6f-115">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="64d6f-115">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="64d6f-116">Registruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="64d6f-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="64d6f-117">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="64d6f-117">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="64d6f-118">Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.</span><span class="sxs-lookup"><span data-stu-id="64d6f-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64d6f-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="64d6f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="64d6f-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="64d6f-120">Element</span></span>|<span data-ttu-id="64d6f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="64d6f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64d6f-122">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="64d6f-122">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="64d6f-123">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="64d6f-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="64d6f-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="64d6f-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="64d6f-125">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="64d6f-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64d6f-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64d6f-126">Remarks</span></span>  
 <span data-ttu-id="64d6f-127">Element lze zadat na úrovni služby `<identityConfiguration>` pod prvkem nebo na úrovni kolekce `<securityTokenHandlerConfiguration>` obslužné rutiny tokenu zabezpečení pod prvkem. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="64d6f-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="64d6f-128">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="64d6f-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="64d6f-129">Element je reprezentován <xref:System.IdentityModel.Configuration.IdentityModelCachesElement>třídou. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="64d6f-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="64d6f-130">Nakonfigurované mezipaměti jsou reprezentovány <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídou.</span><span class="sxs-lookup"><span data-stu-id="64d6f-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64d6f-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="64d6f-131">Example</span></span>  
 <span data-ttu-id="64d6f-132">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro tokeny zabezpečení relace (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="64d6f-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="64d6f-133">Konfigurace je pořízena z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="64d6f-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
