---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f388369d4dc2e590473ad98189ade70b77551b10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="97df2-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="97df2-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="97df2-103">Zaregistruje mezipaměti opětovného přehrání tokenu se službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="97df2-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="97df2-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="97df2-104">\<system.identityModel></span></span>  
<span data-ttu-id="97df2-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="97df2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="97df2-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="97df2-106">\<caches></span></span>  
<span data-ttu-id="97df2-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="97df2-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97df2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97df2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97df2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="97df2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="97df2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="97df2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97df2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="97df2-111">Attributes</span></span>  
  
|<span data-ttu-id="97df2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="97df2-112">Attribute</span></span>|<span data-ttu-id="97df2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="97df2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97df2-114">– typ</span><span class="sxs-lookup"><span data-stu-id="97df2-114">type</span></span>|<span data-ttu-id="97df2-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="97df2-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="97df2-116">Další informace o tom, jak zadat vlastní `type`, najdete v části [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="97df2-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="97df2-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="97df2-117">Child Elements</span></span>  
 <span data-ttu-id="97df2-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="97df2-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97df2-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="97df2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="97df2-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="97df2-120">Element</span></span>|<span data-ttu-id="97df2-121">Popis</span><span class="sxs-lookup"><span data-stu-id="97df2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97df2-122">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="97df2-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="97df2-123">Zaregistruje mezipamětí používaný službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="97df2-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97df2-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97df2-124">Remarks</span></span>  
 <span data-ttu-id="97df2-125">Mezipaměť opětovného přehrání tokenu slouží ke zjištění přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="97df2-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="97df2-126">Rozpoznání opětovného přehrání tokenu je povoleno podle [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, který určuje také maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="97df2-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97df2-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="97df2-127">Example</span></span>  
 <span data-ttu-id="97df2-128">Následující kód XML zobrazuje konfiguraci vlastní mezipaměti pro zjišťování přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="97df2-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97df2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="97df2-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="97df2-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="97df2-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
