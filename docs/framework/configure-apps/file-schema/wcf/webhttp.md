---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399164"
---
# <a name="webhttp"></a><span data-ttu-id="8a89f-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="8a89f-101">\<webHttp></span></span>
<span data-ttu-id="8a89f-102">Tento prvek určuje <xref:System.ServiceModel.Description.WebHttpBehavior> u koncového bodu prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8a89f-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="8a89f-103">Toto chování, při použití ve spojení s [ \<WebHttpBinding >](webhttpbinding.md) standardní vazbou, povoluje webový programovací model pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8a89f-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="8a89f-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8a89f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8a89f-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8a89f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8a89f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8a89f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8a89f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8a89f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="8a89f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8a89f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="8a89f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> protokolu WebHttp**</span><span class="sxs-lookup"><span data-stu-id="8a89f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a89f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a89f-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a89f-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8a89f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8a89f-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8a89f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a89f-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="8a89f-113">Attributes</span></span>  
  
|<span data-ttu-id="8a89f-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="8a89f-114">Attribute</span></span>|<span data-ttu-id="8a89f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="8a89f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a89f-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="8a89f-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="8a89f-117">Pokud je tato vlastnost nastavena na `true`hodnotu, infrastruktura WCF určí nejvhodnější formát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8a89f-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="8a89f-118">Automatický výběr formátu je ve výchozím nastavení zakázán pro účely zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="8a89f-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="8a89f-119">Automatický výběr formátu lze povolit prostřednictvím kódu programu nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8a89f-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="8a89f-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="8a89f-120">defaultBodyStyle</span></span>|<span data-ttu-id="8a89f-121">Určuje výchozí styl textu vrácených zpráv.</span><span class="sxs-lookup"><span data-stu-id="8a89f-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="8a89f-122">Další informace najdete v tématech <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="8a89f-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="8a89f-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="8a89f-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="8a89f-124">Určuje výchozí formát odchozí odpovědi pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="8a89f-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="8a89f-125">Další informace najdete v tématu [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="8a89f-125">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="8a89f-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="8a89f-126">faultExceptionEnabled</span></span>|<span data-ttu-id="8a89f-127">Získá nebo nastaví příznak určující, zda je FaultException generována při vnitřní chybě serveru (kód stavu HTTP: 500) dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="8a89f-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="8a89f-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="8a89f-128">helpEnabled</span></span>|<span data-ttu-id="8a89f-129">Získává nebo nastavuje hodnotu, která určuje, jestli je povolená stránka pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="8a89f-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a89f-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8a89f-130">Child Elements</span></span>  
 <span data-ttu-id="8a89f-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="8a89f-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a89f-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8a89f-132">Parent Elements</span></span>  
  
|<span data-ttu-id="8a89f-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="8a89f-133">Element</span></span>|<span data-ttu-id="8a89f-134">Popis</span><span class="sxs-lookup"><span data-stu-id="8a89f-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a89f-135">\<> chování</span><span class="sxs-lookup"><span data-stu-id="8a89f-135">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8a89f-136">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8a89f-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a89f-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a89f-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="8a89f-138">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="8a89f-138">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="8a89f-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8a89f-139">\<webHttpBinding></span></span>](webhttpbinding.md)
