---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0b0d3c01a81f110f79f64d75aa2ab2ff2873fedd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755042"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="ac2bb-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="ac2bb-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="ac2bb-103">Zaregistruje mezipaměti pro tokeny relaci se službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac2bb-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="ac2bb-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ac2bb-104">\<system.identityModel></span></span>  
<span data-ttu-id="ac2bb-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ac2bb-105">\<identityConfiguration></span></span>  
<span data-ttu-id="ac2bb-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="ac2bb-106">\<caches></span></span>  
<span data-ttu-id="ac2bb-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="ac2bb-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac2bb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac2bb-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac2bb-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ac2bb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ac2bb-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ac2bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac2bb-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ac2bb-111">Attributes</span></span>  
  
|<span data-ttu-id="ac2bb-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ac2bb-112">Attribute</span></span>|<span data-ttu-id="ac2bb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ac2bb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac2bb-114">– typ</span><span class="sxs-lookup"><span data-stu-id="ac2bb-114">type</span></span>|<span data-ttu-id="ac2bb-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="ac2bb-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac2bb-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ac2bb-116">Child Elements</span></span>  
 <span data-ttu-id="ac2bb-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="ac2bb-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac2bb-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ac2bb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ac2bb-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ac2bb-119">Element</span></span>|<span data-ttu-id="ac2bb-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ac2bb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac2bb-121">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="ac2bb-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="ac2bb-122">Zaregistruje mezipamětí používaný službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac2bb-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ac2bb-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac2bb-123">Example</span></span>  
 <span data-ttu-id="ac2bb-124">Následující kód XML zobrazuje konfiguraci vlastní mezipaměti pro uchování relace tokeny zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="ac2bb-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="ac2bb-125">Konfigurace jsou převzaty z `ClaimsAwareWebFarm` ukázka.</span><span class="sxs-lookup"><span data-stu-id="ac2bb-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="ac2bb-126">Další informace o této ukázky najdete v tématu [Index ukázkový kód WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="ac2bb-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac2bb-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac2bb-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
