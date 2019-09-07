---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: b26201064aad3a8a09d8604a9706fe3c149cbf58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400222"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="a970f-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a970f-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="a970f-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="a970f-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="a970f-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a970f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a970f-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a970f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a970f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a970f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a970f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="a970f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a970f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a970f-107">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a970f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a970f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a970f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a970f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a970f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a970f-110">Attributes</span></span>  
  
|<span data-ttu-id="a970f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a970f-111">Attribute</span></span>|<span data-ttu-id="a970f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a970f-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="a970f-113"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="a970f-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a970f-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a970f-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a970f-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a970f-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="a970f-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="a970f-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a970f-117">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="a970f-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a970f-118">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="a970f-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="a970f-119">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="a970f-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="a970f-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="a970f-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a970f-121">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a970f-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="a970f-122"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="a970f-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a970f-123">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a970f-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a970f-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a970f-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a970f-125"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="a970f-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a970f-126">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a970f-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a970f-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a970f-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a970f-128"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="a970f-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a970f-129">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a970f-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a970f-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a970f-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a970f-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a970f-131">Child Elements</span></span>  
 <span data-ttu-id="a970f-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="a970f-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a970f-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a970f-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a970f-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="a970f-134">Element</span></span>|<span data-ttu-id="a970f-135">Popis</span><span class="sxs-lookup"><span data-stu-id="a970f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a970f-136">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="a970f-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="a970f-137">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="a970f-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a970f-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a970f-138">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="a970f-139">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a970f-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="a970f-140">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a970f-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="a970f-141">Metadata</span><span class="sxs-lookup"><span data-stu-id="a970f-141">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="a970f-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="a970f-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a970f-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a970f-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a970f-144">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a970f-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a970f-145">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a970f-145">\<binding></span></span>](../../../misc/binding.md)
