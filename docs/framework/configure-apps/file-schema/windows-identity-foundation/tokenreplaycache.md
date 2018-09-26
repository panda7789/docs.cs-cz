---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: d21a819f789b5be4bdf7ebf57b37a072e1d213ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206215"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="6bb37-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="6bb37-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="6bb37-103">Registruje mezipaměti opětovného přehrání tokenu služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6bb37-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="6bb37-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6bb37-104">\<system.identityModel></span></span>  
<span data-ttu-id="6bb37-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6bb37-105">\<identityConfiguration></span></span>  
<span data-ttu-id="6bb37-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="6bb37-106">\<caches></span></span>  
<span data-ttu-id="6bb37-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="6bb37-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb37-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bb37-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bb37-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6bb37-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6bb37-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6bb37-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bb37-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6bb37-111">Attributes</span></span>  
  
|<span data-ttu-id="6bb37-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6bb37-112">Attribute</span></span>|<span data-ttu-id="6bb37-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6bb37-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6bb37-114">– typ</span><span class="sxs-lookup"><span data-stu-id="6bb37-114">type</span></span>|<span data-ttu-id="6bb37-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="6bb37-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="6bb37-116">Další informace o tom, jak určit vlastní `type`, najdete v článku [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="6bb37-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="6bb37-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6bb37-117">Child Elements</span></span>  
 <span data-ttu-id="6bb37-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="6bb37-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6bb37-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6bb37-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6bb37-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="6bb37-120">Element</span></span>|<span data-ttu-id="6bb37-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6bb37-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bb37-122">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="6bb37-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="6bb37-123">Zaregistruje mezipamětí používá službu nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6bb37-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bb37-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bb37-124">Remarks</span></span>  
 <span data-ttu-id="6bb37-125">Mezipaměť opětovného přehrání tokenu slouží ke zjištění přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="6bb37-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="6bb37-126">Rozpoznání opětovného přehrání tokenu je povoleno podle [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, který také určuje, maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="6bb37-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb37-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bb37-127">Example</span></span>  
 <span data-ttu-id="6bb37-128">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro zjišťování přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="6bb37-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bb37-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bb37-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="6bb37-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="6bb37-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
