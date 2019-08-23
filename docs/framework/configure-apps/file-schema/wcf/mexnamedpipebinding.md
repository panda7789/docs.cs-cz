---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 0d0904c02e31def1b5264bec9f61eac0c9a8e964
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931234"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="d33eb-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="d33eb-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="d33eb-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="d33eb-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="d33eb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d33eb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d33eb-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="d33eb-104">\<bindings></span></span>  
<span data-ttu-id="d33eb-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="d33eb-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d33eb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d33eb-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d33eb-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d33eb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d33eb-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d33eb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d33eb-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="d33eb-109">Attributes</span></span>  
  
|<span data-ttu-id="d33eb-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="d33eb-110">Attribute</span></span>|<span data-ttu-id="d33eb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d33eb-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d33eb-112"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="d33eb-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d33eb-113">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d33eb-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d33eb-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d33eb-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="d33eb-115">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="d33eb-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d33eb-116">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="d33eb-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d33eb-117">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="d33eb-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="d33eb-118">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d33eb-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="d33eb-119">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="d33eb-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d33eb-120">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d33eb-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d33eb-121"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="d33eb-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d33eb-122">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d33eb-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d33eb-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d33eb-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d33eb-124"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="d33eb-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d33eb-125">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d33eb-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d33eb-126">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="d33eb-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d33eb-127"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="d33eb-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d33eb-128">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d33eb-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d33eb-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d33eb-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d33eb-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d33eb-130">Child Elements</span></span>  
 <span data-ttu-id="d33eb-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="d33eb-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d33eb-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d33eb-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d33eb-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d33eb-133">Element</span></span>|<span data-ttu-id="d33eb-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d33eb-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d33eb-135">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="d33eb-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="d33eb-136">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="d33eb-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d33eb-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d33eb-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="d33eb-138">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d33eb-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="d33eb-139">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d33eb-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="d33eb-140">Metadata</span><span class="sxs-lookup"><span data-stu-id="d33eb-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="d33eb-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="d33eb-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d33eb-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d33eb-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d33eb-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d33eb-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d33eb-144">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="d33eb-144">\<binding></span></span>](../../../misc/binding.md)
