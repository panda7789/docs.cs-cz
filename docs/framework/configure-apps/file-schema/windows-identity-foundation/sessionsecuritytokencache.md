---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 697c20d1f526cb376c2430f0006349f7d8f9b2f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257938"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="c94c0-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="c94c0-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="c94c0-102">Registruje mezipaměti relace tokeny služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c94c0-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="c94c0-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c94c0-103">\<system.identityModel></span></span>  
<span data-ttu-id="c94c0-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c94c0-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c94c0-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="c94c0-105">\<caches></span></span>  
<span data-ttu-id="c94c0-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="c94c0-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94c0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c94c0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c94c0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c94c0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c94c0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c94c0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c94c0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c94c0-110">Attributes</span></span>  
  
|<span data-ttu-id="c94c0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c94c0-111">Attribute</span></span>|<span data-ttu-id="c94c0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c94c0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c94c0-113">– typ</span><span class="sxs-lookup"><span data-stu-id="c94c0-113">type</span></span>|<span data-ttu-id="c94c0-114">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="c94c0-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c94c0-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c94c0-115">Child Elements</span></span>  
 <span data-ttu-id="c94c0-116">Žádná</span><span class="sxs-lookup"><span data-stu-id="c94c0-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c94c0-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c94c0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c94c0-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="c94c0-118">Element</span></span>|<span data-ttu-id="c94c0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c94c0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c94c0-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="c94c0-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="c94c0-121">Zaregistruje mezipamětí používá službu nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c94c0-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c94c0-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c94c0-122">Example</span></span>  
 <span data-ttu-id="c94c0-123">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro uchování relace tokenů zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="c94c0-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="c94c0-124">Konfigurace se přebírá ze `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="c94c0-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="c94c0-125">Další informace o této ukázce najdete v tématu [Index ukázkového kódu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="c94c0-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c94c0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c94c0-126">See also</span></span>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
