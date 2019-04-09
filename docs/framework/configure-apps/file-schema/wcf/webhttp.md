---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 795e61b9054d2ea9276970988018c50099bcbe17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129646"
---
# <a name="webhttp"></a><span data-ttu-id="1ffaa-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="1ffaa-101">\<webHttp></span></span>
<span data-ttu-id="1ffaa-102">Tento prvek určuje, <xref:System.ServiceModel.Description.WebHttpBehavior> koncového bodu prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="1ffaa-103">Toto chování při použití ve spojení s [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazbu, umožňuje programovacího modelu webové služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1ffaa-103">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="1ffaa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ffaa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ffaa-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1ffaa-105">\<behaviors></span></span>  
<span data-ttu-id="1ffaa-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1ffaa-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1ffaa-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1ffaa-107">\<behavior></span></span>  
<span data-ttu-id="1ffaa-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="1ffaa-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffaa-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ffaa-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ffaa-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ffaa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ffaa-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ffaa-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ffaa-112">Attributes</span></span>  
  
|<span data-ttu-id="1ffaa-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1ffaa-113">Attribute</span></span>|<span data-ttu-id="1ffaa-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1ffaa-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ffaa-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="1ffaa-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="1ffaa-116">Pokud je tato vlastnost nastavena na `true`, určuje nejvhodnější formát infrastruktura WCF.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="1ffaa-117">Automatický výběr formátu je zakázané ve výchozím nastavení pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="1ffaa-118">Automatický výběr formátu je možné povolit programově nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="1ffaa-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="1ffaa-119">defaultBodyStyle</span></span>|<span data-ttu-id="1ffaa-120">Určuje výchozí styl textu vrácených zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="1ffaa-121">Další informace najdete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="1ffaa-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="1ffaa-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="1ffaa-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="1ffaa-123">Určuje výchozí formát odchozích odpovědi pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="1ffaa-124">Další informace najdete v tématu [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="1ffaa-124">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="1ffaa-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="1ffaa-125">faultExceptionEnabled</span></span>|<span data-ttu-id="1ffaa-126">Získá nebo nastaví příznak určující, zda FaultException se vygeneruje, když vnitřní chybě serveru (stavový kód HTTP: 500) nastane.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="1ffaa-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="1ffaa-127">helpEnabled</span></span>|<span data-ttu-id="1ffaa-128">Získá nebo nastaví hodnotu, která určuje, zda je povoleno na stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ffaa-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ffaa-129">Child Elements</span></span>  
 <span data-ttu-id="1ffaa-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="1ffaa-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ffaa-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ffaa-131">Parent Elements</span></span>  
  
|<span data-ttu-id="1ffaa-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ffaa-132">Element</span></span>|<span data-ttu-id="1ffaa-133">Popis</span><span class="sxs-lookup"><span data-stu-id="1ffaa-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ffaa-134">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1ffaa-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1ffaa-135">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ffaa-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ffaa-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="1ffaa-137">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="1ffaa-137">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="1ffaa-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1ffaa-138">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
