---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646070"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="6c0b3-101">\<>></span><span class="sxs-lookup"><span data-stu-id="6c0b3-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="6c0b3-102">Zaregistruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6c0b3-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="6c0b3-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c0b3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6c0b3-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="6c0b3-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="6c0b3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="6c0b3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="6c0b3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>mezipamětí**](caches.md)</span><span class="sxs-lookup"><span data-stu-id="6c0b3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="6c0b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>**</span><span class="sxs-lookup"><span data-stu-id="6c0b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0b3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c0b3-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c0b3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6c0b3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6c0b3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6c0b3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c0b3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6c0b3-111">Attributes</span></span>  
  
|<span data-ttu-id="6c0b3-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6c0b3-112">Attribute</span></span>|<span data-ttu-id="6c0b3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6c0b3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c0b3-114">type</span><span class="sxs-lookup"><span data-stu-id="6c0b3-114">type</span></span>|<span data-ttu-id="6c0b3-115">Typ, který je <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> odvozen z třídy.</span><span class="sxs-lookup"><span data-stu-id="6c0b3-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c0b3-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6c0b3-116">Child Elements</span></span>  
 <span data-ttu-id="6c0b3-117">Žádná</span><span class="sxs-lookup"><span data-stu-id="6c0b3-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c0b3-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6c0b3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6c0b3-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c0b3-119">Element</span></span>|<span data-ttu-id="6c0b3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="6c0b3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c0b3-121">\<>mezipamětí</span><span class="sxs-lookup"><span data-stu-id="6c0b3-121">\<caches></span></span>](caches.md)|<span data-ttu-id="6c0b3-122">Registruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6c0b3-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c0b3-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c0b3-123">Example</span></span>  
 <span data-ttu-id="6c0b3-124">Následující jazyk XML zobrazuje konfiguraci vlastní mezipaměti pro<xref:System.IdentityModel.Tokens.SessionSecurityToken>držení tokenů zabezpečení relace ( .</span><span class="sxs-lookup"><span data-stu-id="6c0b3-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="6c0b3-125">Konfigurace je převzata `ClaimsAwareWebFarm` ze vzorku.</span><span class="sxs-lookup"><span data-stu-id="6c0b3-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="6c0b3-126">Další informace o této ukázce naleznete v [tématu WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="6c0b3-126">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c0b3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c0b3-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
