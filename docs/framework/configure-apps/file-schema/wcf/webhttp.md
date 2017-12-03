---
title: '&lt;webHttp&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b5388a680816bca6051525f5130308a3c7c2dc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="83c16-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="83c16-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="83c16-103">Určuje tento element <xref:System.ServiceModel.Description.WebHttpBehavior> v koncovém bodě prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="83c16-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="83c16-104">Toto chování, pokud se používá ve spojení s [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazby umožňuje programovací model webových pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="83c16-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>  
  
 <span data-ttu-id="83c16-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="83c16-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="83c16-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="83c16-106">\<behaviors></span></span>  
<span data-ttu-id="83c16-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="83c16-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="83c16-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="83c16-108">\<behavior></span></span>  
<span data-ttu-id="83c16-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="83c16-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c16-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83c16-110">Syntax</span></span>  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83c16-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="83c16-111">Attributes and Elements</span></span>  
 <span data-ttu-id="83c16-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="83c16-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83c16-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="83c16-113">Attributes</span></span>  
  
|<span data-ttu-id="83c16-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="83c16-114">Attribute</span></span>|<span data-ttu-id="83c16-115">Popis</span><span class="sxs-lookup"><span data-stu-id="83c16-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83c16-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="83c16-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="83c16-117">Pokud je tato vlastnost nastavená na `true`, určuje nejlepší formát pro infrastrukturu WCF.</span><span class="sxs-lookup"><span data-stu-id="83c16-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="83c16-118">Automatický výběr formátu ve výchozím nastavení vypnutá pro zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="83c16-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="83c16-119">Automatický výběr formátu lze povolit prostřednictvím kódu programu, nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="83c16-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="83c16-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="83c16-120">defaultBodyStyle</span></span>|<span data-ttu-id="83c16-121">Určuje výchozí styl textu vrácené zprávy.</span><span class="sxs-lookup"><span data-stu-id="83c16-121">Specifies the default body style of returned messages.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="83c16-122"><xref:System.ServiceModel.Web.WebMessageBodyStyle> a [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="83c16-122"> <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="83c16-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="83c16-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="83c16-124">Určuje výchozí formát odchozí odpovědi pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="83c16-124">Specifies the default outgoing response format for messages.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="83c16-125">[WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="83c16-125"> [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="83c16-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="83c16-126">faultExceptionEnabled</span></span>|<span data-ttu-id="83c16-127">Získá nebo nastaví příznak, který určuje, zda FaultException se vygeneruje, když se o vnitřní chybu serveru (kód stavu HTTP: 500) dojde k.</span><span class="sxs-lookup"><span data-stu-id="83c16-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="83c16-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="83c16-128">helpEnabled</span></span>|<span data-ttu-id="83c16-129">Získá nebo nastaví hodnotu, která určuje, zda je povoleno na stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="83c16-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83c16-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="83c16-130">Child Elements</span></span>  
 <span data-ttu-id="83c16-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="83c16-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83c16-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="83c16-132">Parent Elements</span></span>  
  
|<span data-ttu-id="83c16-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="83c16-133">Element</span></span>|<span data-ttu-id="83c16-134">Popis</span><span class="sxs-lookup"><span data-stu-id="83c16-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83c16-135">\<chování ></span><span class="sxs-lookup"><span data-stu-id="83c16-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="83c16-136">Určuje sadu chování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="83c16-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83c16-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="83c16-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="83c16-138">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="83c16-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="83c16-139">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="83c16-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
