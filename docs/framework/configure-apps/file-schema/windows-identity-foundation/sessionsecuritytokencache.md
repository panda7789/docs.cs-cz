---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 5c68fe618f965f364a3716c3bc65de5e165b12ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207796"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="7c0be-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="7c0be-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="7c0be-102">Registruje mezipaměti relace tokeny služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c0be-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="7c0be-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7c0be-103">\<system.identityModel></span></span>  
<span data-ttu-id="7c0be-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c0be-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7c0be-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="7c0be-105">\<caches></span></span>  
<span data-ttu-id="7c0be-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="7c0be-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c0be-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c0be-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c0be-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c0be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7c0be-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7c0be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c0be-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c0be-110">Attributes</span></span>  
  
|<span data-ttu-id="7c0be-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7c0be-111">Attribute</span></span>|<span data-ttu-id="7c0be-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7c0be-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c0be-113"> – typ</span><span class="sxs-lookup"><span data-stu-id="7c0be-113">type</span></span>|<span data-ttu-id="7c0be-114">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="7c0be-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c0be-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c0be-115">Child Elements</span></span>  
 <span data-ttu-id="7c0be-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="7c0be-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c0be-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c0be-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7c0be-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c0be-118">Element</span></span>|<span data-ttu-id="7c0be-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7c0be-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c0be-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="7c0be-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="7c0be-121">Zaregistruje mezipamětí používá službu nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c0be-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7c0be-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c0be-122">Example</span></span>  
 <span data-ttu-id="7c0be-123">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro uchování relace tokenů zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="7c0be-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="7c0be-124">Konfigurace se přebírá ze `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="7c0be-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="7c0be-125">Další informace o této ukázce najdete v tématu [Index ukázkového kódu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="7c0be-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c0be-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c0be-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
