---
title: '&lt;webHttp&gt;'
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 9ba54dc1744751efe4efad04f829cccce1244e0d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145668"
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="d6b2e-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="d6b2e-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="d6b2e-103">Tento prvek určuje, <xref:System.ServiceModel.Description.WebHttpBehavior> koncového bodu prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="d6b2e-104">Toto chování při použití ve spojení s [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazbu, umožňuje programovacího modelu webové služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d6b2e-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="d6b2e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6b2e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6b2e-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d6b2e-106">\<behaviors></span></span>  
<span data-ttu-id="d6b2e-107">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d6b2e-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="d6b2e-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d6b2e-108">\<behavior></span></span>  
<span data-ttu-id="d6b2e-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="d6b2e-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b2e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b2e-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6b2e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6b2e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6b2e-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6b2e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6b2e-113">Attributes</span></span>  
  
|<span data-ttu-id="d6b2e-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6b2e-114">Attribute</span></span>|<span data-ttu-id="d6b2e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b2e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6b2e-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="d6b2e-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="d6b2e-117">Pokud je tato vlastnost nastavena na `true`, určuje nejvhodnější formát infrastruktura WCF.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="d6b2e-118">Automatický výběr formátu je zakázané ve výchozím nastavení pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="d6b2e-119">Automatický výběr formátu je možné povolit programově nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="d6b2e-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="d6b2e-120">defaultBodyStyle</span></span>|<span data-ttu-id="d6b2e-121">Určuje výchozí styl textu vrácených zpráv.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="d6b2e-122">Další informace najdete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="d6b2e-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d6b2e-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="d6b2e-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="d6b2e-124">Určuje výchozí formát odchozích odpovědi pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="d6b2e-125">Další informace najdete v tématu [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="d6b2e-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d6b2e-126">Třída faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="d6b2e-126">faultExceptionEnabled</span></span>|<span data-ttu-id="d6b2e-127">Získá nebo nastaví příznak určující, zda FaultException se vygeneruje, když vnitřní chybě serveru (stavový kód HTTP: 500) nastane.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="d6b2e-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="d6b2e-128">helpEnabled</span></span>|<span data-ttu-id="d6b2e-129">Získá nebo nastaví hodnotu, která určuje, zda je povoleno na stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6b2e-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b2e-130">Child Elements</span></span>  
 <span data-ttu-id="d6b2e-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6b2e-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6b2e-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b2e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d6b2e-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6b2e-133">Element</span></span>|<span data-ttu-id="d6b2e-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b2e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6b2e-135">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d6b2e-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d6b2e-136">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d6b2e-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6b2e-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6b2e-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="d6b2e-138">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="d6b2e-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="d6b2e-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d6b2e-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
