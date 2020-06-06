---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430302"
---
# \<mexTcpBinding>
<span data-ttu-id="bb912-101">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="bb912-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="bb912-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb912-102">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb912-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bb912-103">Attributes and Elements</span></span>  
 <span data-ttu-id="bb912-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bb912-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb912-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="bb912-105">Attributes</span></span>  
  
|<span data-ttu-id="bb912-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="bb912-106">Attribute</span></span>|<span data-ttu-id="bb912-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bb912-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bb912-108"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="bb912-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bb912-109">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bb912-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb912-110">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bb912-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bb912-111">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="bb912-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bb912-112">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="bb912-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bb912-113">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="bb912-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bb912-114">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bb912-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bb912-115"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="bb912-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bb912-116">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bb912-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb912-117">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bb912-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bb912-118"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="bb912-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bb912-119">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bb912-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb912-120">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bb912-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bb912-121"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="bb912-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bb912-122">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bb912-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb912-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bb912-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb912-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bb912-124">Child Elements</span></span>  
 <span data-ttu-id="bb912-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="bb912-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb912-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bb912-126">Parent Elements</span></span>  
  
|<span data-ttu-id="bb912-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb912-127">Element</span></span>|<span data-ttu-id="bb912-128">Description</span><span class="sxs-lookup"><span data-stu-id="bb912-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="bb912-129">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="bb912-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb912-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb912-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="bb912-131">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="bb912-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bb912-132">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="bb912-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bb912-133">Metadata</span><span class="sxs-lookup"><span data-stu-id="bb912-133">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bb912-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="bb912-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bb912-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="bb912-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bb912-136">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bb912-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
