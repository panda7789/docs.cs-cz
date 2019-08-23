---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: bb9e1fc0b3ec62c824864a74efb64c34d2076e66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931290"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="fe900-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="fe900-101">\<mexHttpBinding></span></span>
<span data-ttu-id="fe900-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="fe900-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="fe900-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fe900-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fe900-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="fe900-104">\<bindings></span></span>  
<span data-ttu-id="fe900-105">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="fe900-105">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe900-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe900-106">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe900-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe900-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fe900-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe900-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe900-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe900-109">Attributes</span></span>  
  
|<span data-ttu-id="fe900-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe900-110">Attribute</span></span>|<span data-ttu-id="fe900-111">Popis</span><span class="sxs-lookup"><span data-stu-id="fe900-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="fe900-112"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="fe900-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="fe900-113">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fe900-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fe900-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fe900-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="fe900-115">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="fe900-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="fe900-116">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="fe900-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="fe900-117">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="fe900-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="fe900-118">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="fe900-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="fe900-119">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="fe900-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="fe900-120">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fe900-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="fe900-121"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="fe900-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="fe900-122">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fe900-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fe900-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fe900-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="fe900-124"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="fe900-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="fe900-125">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fe900-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fe900-126">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="fe900-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="fe900-127"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="fe900-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="fe900-128">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fe900-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fe900-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fe900-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe900-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe900-130">Child Elements</span></span>  
 <span data-ttu-id="fe900-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="fe900-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe900-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe900-132">Parent Elements</span></span>  
  
|<span data-ttu-id="fe900-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe900-133">Element</span></span>|<span data-ttu-id="fe900-134">Popis</span><span class="sxs-lookup"><span data-stu-id="fe900-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe900-135">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="fe900-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="fe900-136">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="fe900-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe900-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe900-137">Remarks</span></span>  
 <span data-ttu-id="fe900-138">Tato vazba je v podstatě `WSHttpBinding` vazba se zakázaným zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="fe900-138">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="fe900-139">Podporuje většinu požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="fe900-139">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe900-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe900-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="fe900-141">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fe900-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="fe900-142">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="fe900-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="fe900-143">Metadata</span><span class="sxs-lookup"><span data-stu-id="fe900-143">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="fe900-144">Vazby</span><span class="sxs-lookup"><span data-stu-id="fe900-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fe900-145">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="fe900-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fe900-146">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fe900-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fe900-147">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="fe900-147">\<binding></span></span>](../../../misc/binding.md)
