---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 9be3bf980c3756678d26d8652271113d4daaba43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943715"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="7c0cc-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="7c0cc-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="7c0cc-102">Registruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="7c0cc-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7c0cc-103">\<system.identityModel></span></span>  
<span data-ttu-id="7c0cc-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c0cc-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7c0cc-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="7c0cc-105">\<caches></span></span>  
<span data-ttu-id="7c0cc-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="7c0cc-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c0cc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c0cc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c0cc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c0cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7c0cc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c0cc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c0cc-110">Attributes</span></span>  
  
|<span data-ttu-id="7c0cc-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7c0cc-111">Attribute</span></span>|<span data-ttu-id="7c0cc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7c0cc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c0cc-113">– typ</span><span class="sxs-lookup"><span data-stu-id="7c0cc-113">type</span></span>|<span data-ttu-id="7c0cc-114">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c0cc-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c0cc-115">Child Elements</span></span>  
 <span data-ttu-id="7c0cc-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="7c0cc-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c0cc-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c0cc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7c0cc-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c0cc-118">Element</span></span>|<span data-ttu-id="7c0cc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7c0cc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c0cc-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="7c0cc-120">\<caches></span></span>](caches.md)|<span data-ttu-id="7c0cc-121">Zaregistruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7c0cc-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c0cc-122">Example</span></span>  
 <span data-ttu-id="7c0cc-123">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro tokeny zabezpečení relace (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="7c0cc-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="7c0cc-124">Konfigurace je pořízena z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="7c0cc-125">Další informace o této ukázce naleznete v tématu [WIF Code Sample index](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="7c0cc-125">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c0cc-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c0cc-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
