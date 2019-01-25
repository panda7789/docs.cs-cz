---
title: '&lt;webHttp&gt;'
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: b52259af5e05de5bf5dd42a2cd0bf4b01f3e46f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597551"
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="ee907-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="ee907-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="ee907-103">Tento prvek určuje, <xref:System.ServiceModel.Description.WebHttpBehavior> koncového bodu prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ee907-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="ee907-104">Toto chování při použití ve spojení s [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazbu, umožňuje programovacího modelu webové služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ee907-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="ee907-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ee907-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee907-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ee907-106">\<behaviors></span></span>  
<span data-ttu-id="ee907-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ee907-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="ee907-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ee907-108">\<behavior></span></span>  
<span data-ttu-id="ee907-109">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="ee907-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee907-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee907-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee907-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ee907-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ee907-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ee907-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee907-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="ee907-113">Attributes</span></span>  
  
|<span data-ttu-id="ee907-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="ee907-114">Attribute</span></span>|<span data-ttu-id="ee907-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ee907-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee907-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="ee907-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="ee907-117">Pokud je tato vlastnost nastavena na `true`, určuje nejvhodnější formát infrastruktura WCF.</span><span class="sxs-lookup"><span data-stu-id="ee907-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="ee907-118">Automatický výběr formátu je zakázané ve výchozím nastavení pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="ee907-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="ee907-119">Automatický výběr formátu je možné povolit programově nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ee907-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="ee907-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="ee907-120">defaultBodyStyle</span></span>|<span data-ttu-id="ee907-121">Určuje výchozí styl textu vrácených zpráv.</span><span class="sxs-lookup"><span data-stu-id="ee907-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="ee907-122">Další informace najdete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="ee907-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="ee907-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="ee907-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="ee907-124">Určuje výchozí formát odchozích odpovědi pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="ee907-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="ee907-125">Další informace najdete v tématu [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="ee907-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="ee907-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="ee907-126">faultExceptionEnabled</span></span>|<span data-ttu-id="ee907-127">Získá nebo nastaví příznak určující, zda FaultException se vygeneruje, když vnitřní chybě serveru (stavový kód HTTP: 500) nastane.</span><span class="sxs-lookup"><span data-stu-id="ee907-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="ee907-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="ee907-128">helpEnabled</span></span>|<span data-ttu-id="ee907-129">Získá nebo nastaví hodnotu, která určuje, zda je povoleno na stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="ee907-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee907-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ee907-130">Child Elements</span></span>  
 <span data-ttu-id="ee907-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="ee907-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee907-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ee907-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ee907-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="ee907-133">Element</span></span>|<span data-ttu-id="ee907-134">Popis</span><span class="sxs-lookup"><span data-stu-id="ee907-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee907-135">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ee907-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ee907-136">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ee907-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee907-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee907-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="ee907-138">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="ee907-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="ee907-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ee907-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
