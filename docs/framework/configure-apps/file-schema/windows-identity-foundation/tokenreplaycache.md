---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: dfa6c0d84582d55595f00f149adfdcaa9d554d6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271947"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="c10b9-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="c10b9-101">\<tokenReplayCache></span></span>
<span data-ttu-id="c10b9-102">Registruje mezipaměti opětovného přehrání tokenu služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c10b9-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="c10b9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c10b9-103">\<system.identityModel></span></span>  
<span data-ttu-id="c10b9-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c10b9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c10b9-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="c10b9-105">\<caches></span></span>  
<span data-ttu-id="c10b9-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="c10b9-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c10b9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c10b9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c10b9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c10b9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c10b9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c10b9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c10b9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c10b9-110">Attributes</span></span>  
  
|<span data-ttu-id="c10b9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c10b9-111">Attribute</span></span>|<span data-ttu-id="c10b9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c10b9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c10b9-113">– typ</span><span class="sxs-lookup"><span data-stu-id="c10b9-113">type</span></span>|<span data-ttu-id="c10b9-114">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="c10b9-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="c10b9-115">Další informace o tom, jak určit vlastní `type`, najdete v článku [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="c10b9-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="c10b9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c10b9-116">Child Elements</span></span>  
 <span data-ttu-id="c10b9-117">Žádná</span><span class="sxs-lookup"><span data-stu-id="c10b9-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c10b9-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c10b9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c10b9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c10b9-119">Element</span></span>|<span data-ttu-id="c10b9-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c10b9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c10b9-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="c10b9-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="c10b9-122">Zaregistruje mezipamětí používá službu nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c10b9-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c10b9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c10b9-123">Remarks</span></span>  
 <span data-ttu-id="c10b9-124">Mezipaměť opětovného přehrání tokenu slouží ke zjištění přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="c10b9-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="c10b9-125">Rozpoznání opětovného přehrání tokenu je povoleno podle [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, který také určuje, maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="c10b9-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c10b9-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="c10b9-126">Example</span></span>  
 <span data-ttu-id="c10b9-127">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro zjišťování přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="c10b9-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c10b9-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c10b9-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="c10b9-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="c10b9-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
