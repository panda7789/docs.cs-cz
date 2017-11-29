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
ms.openlocfilehash: e43e79416ddb8862cbc6e52d9d449a02b123af83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="b732c-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="b732c-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="b732c-103">Zaregistruje mezipaměti opětovného přehrání tokenu se službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b732c-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="b732c-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b732c-104">\<system.identityModel></span></span>  
<span data-ttu-id="b732c-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b732c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b732c-106">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="b732c-106">\<caches></span></span>  
<span data-ttu-id="b732c-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="b732c-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b732c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b732c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b732c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b732c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b732c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b732c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b732c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b732c-111">Attributes</span></span>  
  
|<span data-ttu-id="b732c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b732c-112">Attribute</span></span>|<span data-ttu-id="b732c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b732c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b732c-114">– typ</span><span class="sxs-lookup"><span data-stu-id="b732c-114">type</span></span>|<span data-ttu-id="b732c-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="b732c-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="b732c-116">Další informace o tom, jak zadat vlastní `type`, najdete v části [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="b732c-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="b732c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b732c-117">Child Elements</span></span>  
 <span data-ttu-id="b732c-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="b732c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b732c-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b732c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b732c-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b732c-120">Element</span></span>|<span data-ttu-id="b732c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b732c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b732c-122">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="b732c-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="b732c-123">Zaregistruje mezipamětí používaný službou nebo kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b732c-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b732c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b732c-124">Remarks</span></span>  
 <span data-ttu-id="b732c-125">Mezipaměť opětovného přehrání tokenu slouží ke zjištění přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="b732c-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="b732c-126">Rozpoznání opětovného přehrání tokenu je povoleno podle [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, který určuje také maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="b732c-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b732c-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="b732c-127">Example</span></span>  
 <span data-ttu-id="b732c-128">Následující kód XML zobrazuje konfiguraci vlastní mezipaměti pro zjišťování přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="b732c-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b732c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b732c-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="b732c-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="b732c-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
