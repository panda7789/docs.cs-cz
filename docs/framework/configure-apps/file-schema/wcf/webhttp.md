---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940494"
---
# <a name="webhttp"></a><span data-ttu-id="40fab-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="40fab-101">\<webHttp></span></span>
<span data-ttu-id="40fab-102">Tento prvek určuje <xref:System.ServiceModel.Description.WebHttpBehavior> u koncového bodu prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="40fab-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="40fab-103">Toto chování, při použití ve spojení s [ \<WebHttpBinding >](webhttpbinding.md) standardní vazbou, povoluje webový programovací model pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="40fab-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="40fab-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40fab-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40fab-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="40fab-105">\<behaviors></span></span>  
<span data-ttu-id="40fab-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="40fab-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="40fab-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="40fab-107">\<behavior></span></span>  
<span data-ttu-id="40fab-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="40fab-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40fab-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40fab-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40fab-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40fab-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40fab-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40fab-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40fab-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="40fab-112">Attributes</span></span>  
  
|<span data-ttu-id="40fab-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="40fab-113">Attribute</span></span>|<span data-ttu-id="40fab-114">Popis</span><span class="sxs-lookup"><span data-stu-id="40fab-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40fab-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="40fab-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="40fab-116">Pokud je tato vlastnost nastavena na `true`hodnotu, infrastruktura WCF určí nejvhodnější formát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="40fab-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="40fab-117">Automatický výběr formátu je ve výchozím nastavení zakázán pro účely zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="40fab-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="40fab-118">Automatický výběr formátu lze povolit prostřednictvím kódu programu nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="40fab-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="40fab-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="40fab-119">defaultBodyStyle</span></span>|<span data-ttu-id="40fab-120">Určuje výchozí styl textu vrácených zpráv.</span><span class="sxs-lookup"><span data-stu-id="40fab-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="40fab-121">Další informace najdete v tématech <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="40fab-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="40fab-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="40fab-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="40fab-123">Určuje výchozí formát odchozí odpovědi pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="40fab-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="40fab-124">Další informace najdete v tématu [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="40fab-124">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="40fab-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="40fab-125">faultExceptionEnabled</span></span>|<span data-ttu-id="40fab-126">Získá nebo nastaví příznak určující, zda je FaultException generována při vnitřní chybě serveru (kód stavu HTTP: 500) dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="40fab-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="40fab-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="40fab-127">helpEnabled</span></span>|<span data-ttu-id="40fab-128">Získává nebo nastavuje hodnotu, která určuje, jestli je povolená stránka pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="40fab-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40fab-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40fab-129">Child Elements</span></span>  
 <span data-ttu-id="40fab-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="40fab-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40fab-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40fab-131">Parent Elements</span></span>  
  
|<span data-ttu-id="40fab-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="40fab-132">Element</span></span>|<span data-ttu-id="40fab-133">Popis</span><span class="sxs-lookup"><span data-stu-id="40fab-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40fab-134">\<> chování</span><span class="sxs-lookup"><span data-stu-id="40fab-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="40fab-135">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="40fab-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40fab-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40fab-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="40fab-137">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="40fab-137">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="40fab-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="40fab-138">\<webHttpBinding></span></span>](webhttpbinding.md)
