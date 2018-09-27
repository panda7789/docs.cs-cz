---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: b812673ac1c015adde357d3c0707d85643aad3e9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401367"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="af247-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="af247-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="af247-103">Registruje mezipaměti relace tokeny služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="af247-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="af247-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="af247-104">\<system.identityModel></span></span>  
<span data-ttu-id="af247-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="af247-105">\<identityConfiguration></span></span>  
<span data-ttu-id="af247-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="af247-106">\<caches></span></span>  
<span data-ttu-id="af247-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="af247-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af247-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af247-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af247-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="af247-109">Attributes and Elements</span></span>  
 <span data-ttu-id="af247-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="af247-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af247-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="af247-111">Attributes</span></span>  
  
|<span data-ttu-id="af247-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="af247-112">Attribute</span></span>|<span data-ttu-id="af247-113">Popis</span><span class="sxs-lookup"><span data-stu-id="af247-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af247-114">– typ</span><span class="sxs-lookup"><span data-stu-id="af247-114">type</span></span>|<span data-ttu-id="af247-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="af247-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af247-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="af247-116">Child Elements</span></span>  
 <span data-ttu-id="af247-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="af247-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af247-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="af247-118">Parent Elements</span></span>  
  
|<span data-ttu-id="af247-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="af247-119">Element</span></span>|<span data-ttu-id="af247-120">Popis</span><span class="sxs-lookup"><span data-stu-id="af247-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af247-121">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="af247-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="af247-122">Zaregistruje mezipamětí používá službu nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="af247-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af247-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="af247-123">Example</span></span>  
 <span data-ttu-id="af247-124">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro uchování relace tokenů zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="af247-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="af247-125">Konfigurace se přebírá ze `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="af247-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="af247-126">Další informace o této ukázce najdete v tématu [Index ukázkového kódu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="af247-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af247-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="af247-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
