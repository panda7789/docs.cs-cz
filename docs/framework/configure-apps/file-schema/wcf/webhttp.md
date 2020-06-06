---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399164"
---
# \<webHttp>
<span data-ttu-id="d4ad6-101">Tento prvek určuje <xref:System.ServiceModel.Description.WebHttpBehavior> u koncového bodu prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-101">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="d4ad6-102">Toto chování, při použití ve spojení se [\<webHttpBinding>](webhttpbinding.md) standardní vazbou, umožňuje model webového programování pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d4ad6-102">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="d4ad6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4ad6-103">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4ad6-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4ad6-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d4ad6-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4ad6-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4ad6-106">Attributes</span></span>  
  
|<span data-ttu-id="d4ad6-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4ad6-107">Attribute</span></span>|<span data-ttu-id="d4ad6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d4ad6-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4ad6-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="d4ad6-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="d4ad6-110">Pokud je tato vlastnost nastavena na hodnotu `true` , infrastruktura WCF určí nejvhodnější formát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-110">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="d4ad6-111">Automatický výběr formátu je ve výchozím nastavení zakázán pro účely zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-111">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="d4ad6-112">Automatický výběr formátu lze povolit prostřednictvím kódu programu nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-112">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="d4ad6-113">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="d4ad6-113">defaultBodyStyle</span></span>|<span data-ttu-id="d4ad6-114">Určuje výchozí styl textu vrácených zpráv.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-114">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="d4ad6-115">Další informace najdete v tématech <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="d4ad6-115">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d4ad6-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="d4ad6-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="d4ad6-117">Určuje výchozí formát odchozí odpovědi pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-117">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="d4ad6-118">Další informace najdete v tématu [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="d4ad6-118">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d4ad6-119">Třída FaultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="d4ad6-119">faultExceptionEnabled</span></span>|<span data-ttu-id="d4ad6-120">Získá nebo nastaví příznak určující, zda je FaultException generována v případě, že dojde k vnitřní chybě serveru (kód stavu HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="d4ad6-120">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="d4ad6-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="d4ad6-121">helpEnabled</span></span>|<span data-ttu-id="d4ad6-122">Získává nebo nastavuje hodnotu, která určuje, jestli je povolená stránka pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-122">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4ad6-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4ad6-123">Child Elements</span></span>  
 <span data-ttu-id="d4ad6-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4ad6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4ad6-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4ad6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d4ad6-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4ad6-126">Element</span></span>|<span data-ttu-id="d4ad6-127">Description</span><span class="sxs-lookup"><span data-stu-id="d4ad6-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d4ad6-128">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d4ad6-128">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4ad6-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4ad6-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="d4ad6-130">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="d4ad6-130">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
