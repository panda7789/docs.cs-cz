---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646070"
---
# \<sessionSecurityTokenCache>
<span data-ttu-id="8fe4c-101">Registruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8fe4c-101">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="8fe4c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fe4c-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fe4c-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8fe4c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8fe4c-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8fe4c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fe4c-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="8fe4c-105">Attributes</span></span>  
  
|<span data-ttu-id="8fe4c-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="8fe4c-106">Attribute</span></span>|<span data-ttu-id="8fe4c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8fe4c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fe4c-108">typ</span><span class="sxs-lookup"><span data-stu-id="8fe4c-108">type</span></span>|<span data-ttu-id="8fe4c-109">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="8fe4c-109">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fe4c-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8fe4c-110">Child Elements</span></span>  
 <span data-ttu-id="8fe4c-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="8fe4c-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8fe4c-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8fe4c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8fe4c-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="8fe4c-113">Element</span></span>|<span data-ttu-id="8fe4c-114">Description</span><span class="sxs-lookup"><span data-stu-id="8fe4c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="8fe4c-115">Zaregistruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8fe4c-115">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8fe4c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fe4c-116">Example</span></span>  
 <span data-ttu-id="8fe4c-117">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro tokeny zabezpečení relace ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="8fe4c-117">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="8fe4c-118">Konfigurace je pořízena z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="8fe4c-118">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="8fe4c-119">Další informace o této ukázce naleznete v tématu [WIF Code Sample index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="8fe4c-119">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fe4c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fe4c-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
