---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: d77809ae87a28995b3f37848e19ebddd24942f22
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397759"
---
# <a name="mextcpbinding"></a><span data-ttu-id="78992-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="78992-101">\<mexTcpBinding></span></span>
<span data-ttu-id="78992-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="78992-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
<span data-ttu-id="78992-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="78992-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="78992-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="78992-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="78992-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="78992-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="78992-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="78992-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78992-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78992-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78992-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78992-108">Attributes and Elements</span></span>  
 <span data-ttu-id="78992-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78992-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78992-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="78992-110">Attributes</span></span>  
  
|<span data-ttu-id="78992-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="78992-111">Attribute</span></span>|<span data-ttu-id="78992-112">Popis</span><span class="sxs-lookup"><span data-stu-id="78992-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="78992-113"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="78992-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="78992-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="78992-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78992-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="78992-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="78992-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="78992-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="78992-117">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="78992-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="78992-118">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="78992-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="78992-119">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="78992-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="78992-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="78992-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="78992-121">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="78992-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="78992-122"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="78992-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="78992-123">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="78992-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78992-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="78992-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="78992-125"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="78992-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="78992-126">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="78992-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78992-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="78992-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="78992-128"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="78992-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="78992-129">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="78992-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="78992-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="78992-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78992-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78992-131">Child Elements</span></span>  
 <span data-ttu-id="78992-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="78992-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78992-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78992-133">Parent Elements</span></span>  
  
|<span data-ttu-id="78992-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="78992-134">Element</span></span>|<span data-ttu-id="78992-135">Popis</span><span class="sxs-lookup"><span data-stu-id="78992-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78992-136">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="78992-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="78992-137">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="78992-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78992-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78992-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="78992-139">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="78992-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="78992-140">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="78992-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="78992-141">Metadata</span><span class="sxs-lookup"><span data-stu-id="78992-141">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="78992-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="78992-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="78992-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="78992-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="78992-144">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="78992-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="78992-145">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="78992-145">\<binding></span></span>](../../../misc/binding.md)
