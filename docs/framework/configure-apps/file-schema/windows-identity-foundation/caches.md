---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252165"
---
# \<caches>
<span data-ttu-id="3cea1-101">Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="3cea1-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="3cea1-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cea1-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cea1-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3cea1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3cea1-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3cea1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cea1-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="3cea1-105">Attributes</span></span>  
 <span data-ttu-id="3cea1-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="3cea1-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3cea1-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3cea1-107">Child Elements</span></span>  
  
|<span data-ttu-id="3cea1-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="3cea1-108">Element</span></span>|<span data-ttu-id="3cea1-109">Description</span><span class="sxs-lookup"><span data-stu-id="3cea1-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="3cea1-110">Registruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3cea1-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="3cea1-111">Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.</span><span class="sxs-lookup"><span data-stu-id="3cea1-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3cea1-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3cea1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3cea1-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="3cea1-113">Element</span></span>|<span data-ttu-id="3cea1-114">Description</span><span class="sxs-lookup"><span data-stu-id="3cea1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="3cea1-115">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="3cea1-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="3cea1-116">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3cea1-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cea1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cea1-117">Remarks</span></span>  
 <span data-ttu-id="3cea1-118">`<caches>`Element lze zadat na úrovni služby pod `<identityConfiguration>` prvkem nebo na úrovni kolekce obslužné rutiny tokenu zabezpečení pod `<securityTokenHandlerConfiguration>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="3cea1-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="3cea1-119">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="3cea1-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="3cea1-120">`<caches>`Element je reprezentován <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="3cea1-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="3cea1-121">Nakonfigurované mezipaměti jsou reprezentovány <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídou.</span><span class="sxs-lookup"><span data-stu-id="3cea1-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cea1-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cea1-122">Example</span></span>  
 <span data-ttu-id="3cea1-123">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro tokeny zabezpečení relace ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="3cea1-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="3cea1-124">Konfigurace je pořízena z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="3cea1-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
