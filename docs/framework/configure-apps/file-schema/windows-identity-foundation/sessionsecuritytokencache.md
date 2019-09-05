---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: e949b16f76f20191b84bbbbb6e8b019d913316f0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251833"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="e7269-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="e7269-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="e7269-102">Registruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e7269-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="e7269-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7269-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7269-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e7269-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e7269-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e7269-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e7269-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ukládá do mezipaměti >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="e7269-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="e7269-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionSecurityTokenCache >**</span><span class="sxs-lookup"><span data-stu-id="e7269-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7269-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7269-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7269-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e7269-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e7269-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e7269-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7269-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e7269-111">Attributes</span></span>  
  
|<span data-ttu-id="e7269-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e7269-112">Attribute</span></span>|<span data-ttu-id="e7269-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e7269-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7269-114">– typ</span><span class="sxs-lookup"><span data-stu-id="e7269-114">type</span></span>|<span data-ttu-id="e7269-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="e7269-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7269-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e7269-116">Child Elements</span></span>  
 <span data-ttu-id="e7269-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="e7269-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7269-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e7269-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e7269-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e7269-119">Element</span></span>|<span data-ttu-id="e7269-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e7269-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7269-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="e7269-121">\<caches></span></span>](caches.md)|<span data-ttu-id="e7269-122">Zaregistruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e7269-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7269-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7269-123">Example</span></span>  
 <span data-ttu-id="e7269-124">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro tokeny zabezpečení relace (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="e7269-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="e7269-125">Konfigurace je pořízena z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="e7269-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="e7269-126">Další informace o této ukázce naleznete v tématu [WIF Code Sample index](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="e7269-126">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7269-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7269-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
