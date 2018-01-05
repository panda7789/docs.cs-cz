---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 9f4b87d6c620a07ee831888086bdab75a689875e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="2974d-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="2974d-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="2974d-103">Zaregistruje mezipaměti pro tokeny relaci se službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2974d-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="2974d-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="2974d-104">\<system.identityModel></span></span>  
<span data-ttu-id="2974d-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2974d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2974d-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="2974d-106">\<caches></span></span>  
<span data-ttu-id="2974d-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="2974d-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2974d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2974d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2974d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2974d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2974d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2974d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2974d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2974d-111">Attributes</span></span>  
  
|<span data-ttu-id="2974d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2974d-112">Attribute</span></span>|<span data-ttu-id="2974d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2974d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2974d-114">– typ</span><span class="sxs-lookup"><span data-stu-id="2974d-114">type</span></span>|<span data-ttu-id="2974d-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="2974d-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2974d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2974d-116">Child Elements</span></span>  
 <span data-ttu-id="2974d-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="2974d-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2974d-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2974d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2974d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2974d-119">Element</span></span>|<span data-ttu-id="2974d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2974d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2974d-121">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="2974d-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="2974d-122">Zaregistruje mezipamětí používaný službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2974d-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2974d-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="2974d-123">Example</span></span>  
 <span data-ttu-id="2974d-124">Následující kód XML zobrazuje konfiguraci vlastní mezipaměti pro uchování relace tokeny zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="2974d-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="2974d-125">Konfigurace jsou převzaty z `ClaimsAwareWebFarm` ukázka.</span><span class="sxs-lookup"><span data-stu-id="2974d-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="2974d-126">Další informace o této ukázky najdete v tématu [Index ukázkový kód WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="2974d-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2974d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2974d-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
