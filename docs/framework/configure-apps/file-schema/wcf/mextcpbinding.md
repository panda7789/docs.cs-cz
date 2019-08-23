---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 491597da508487c3988b284c84411123d434fe72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932532"
---
# <a name="mextcpbinding"></a><span data-ttu-id="ecac2-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="ecac2-101">\<mexTcpBinding></span></span>
<span data-ttu-id="ecac2-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="ecac2-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="ecac2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ecac2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ecac2-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="ecac2-104">\<bindings></span></span>  
<span data-ttu-id="ecac2-105">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="ecac2-105">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecac2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecac2-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecac2-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ecac2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ecac2-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ecac2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecac2-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="ecac2-109">Attributes</span></span>  
  
|<span data-ttu-id="ecac2-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="ecac2-110">Attribute</span></span>|<span data-ttu-id="ecac2-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ecac2-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="ecac2-112"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="ecac2-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="ecac2-113">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ecac2-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ecac2-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ecac2-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="ecac2-115">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="ecac2-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="ecac2-116">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="ecac2-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ecac2-117">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="ecac2-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="ecac2-118">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="ecac2-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="ecac2-119">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="ecac2-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ecac2-120">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ecac2-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ecac2-121"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="ecac2-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ecac2-122">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ecac2-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ecac2-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ecac2-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ecac2-124"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="ecac2-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ecac2-125">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ecac2-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ecac2-126">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="ecac2-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ecac2-127"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="ecac2-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ecac2-128">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ecac2-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ecac2-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ecac2-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecac2-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ecac2-130">Child Elements</span></span>  
 <span data-ttu-id="ecac2-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="ecac2-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecac2-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ecac2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ecac2-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="ecac2-133">Element</span></span>|<span data-ttu-id="ecac2-134">Popis</span><span class="sxs-lookup"><span data-stu-id="ecac2-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecac2-135">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="ecac2-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="ecac2-136">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="ecac2-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecac2-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecac2-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="ecac2-138">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ecac2-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="ecac2-139">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="ecac2-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="ecac2-140">Metadata</span><span class="sxs-lookup"><span data-stu-id="ecac2-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="ecac2-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="ecac2-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ecac2-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="ecac2-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ecac2-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ecac2-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ecac2-144">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="ecac2-144">\<binding></span></span>](../../../misc/binding.md)
