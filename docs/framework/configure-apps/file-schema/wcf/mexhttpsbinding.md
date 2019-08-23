---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 30d1aa27ce29b6aa4091c3e7be05746ad462102a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931269"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="3070a-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="3070a-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="3070a-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3070a-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="3070a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3070a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3070a-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="3070a-104">\<bindings></span></span>  
<span data-ttu-id="3070a-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="3070a-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3070a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3070a-106">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3070a-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3070a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3070a-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3070a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3070a-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="3070a-109">Attributes</span></span>  
  
|<span data-ttu-id="3070a-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="3070a-110">Attribute</span></span>|<span data-ttu-id="3070a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3070a-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="3070a-112"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="3070a-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3070a-113">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3070a-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3070a-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3070a-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="3070a-115">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="3070a-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3070a-116">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="3070a-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="3070a-117">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="3070a-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="3070a-118">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="3070a-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="3070a-119">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="3070a-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3070a-120">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3070a-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="3070a-121"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="3070a-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3070a-122">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3070a-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3070a-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3070a-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="3070a-124"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="3070a-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3070a-125">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3070a-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3070a-126">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="3070a-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="3070a-127"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="3070a-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3070a-128">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3070a-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3070a-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3070a-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3070a-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3070a-130">Child Elements</span></span>  
 <span data-ttu-id="3070a-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="3070a-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3070a-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3070a-132">Parent Elements</span></span>  
  
|<span data-ttu-id="3070a-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="3070a-133">Element</span></span>|<span data-ttu-id="3070a-134">Popis</span><span class="sxs-lookup"><span data-stu-id="3070a-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3070a-135">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="3070a-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="3070a-136">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="3070a-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3070a-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3070a-137">Remarks</span></span>  
 <span data-ttu-id="3070a-138">Tato vazba je v podstatě `WSHttpBinding` vazba, která podporuje zabezpečení na úrovni přenosu pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="3070a-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="3070a-139">Další informace o konfiguraci a používání tohoto koncového bodu metadat najdete v [tématu How to: Konfigurace vlastní vazby](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)WS-Metadata Exchange, [jak: Načtěte metadata přes vazbu](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)mimo MEX a ukázka [vlastního zabezpečeného koncového bodu metadat](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="3070a-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3070a-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3070a-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="3070a-141">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3070a-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="3070a-142">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3070a-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="3070a-143">Postupy: Konfigurace vlastní vazby WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="3070a-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="3070a-144">Postupy: Načtení metadat přes vazbu, která není MEX</span><span class="sxs-lookup"><span data-stu-id="3070a-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="3070a-145">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="3070a-145">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="3070a-146">Metadata</span><span class="sxs-lookup"><span data-stu-id="3070a-146">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="3070a-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="3070a-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3070a-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3070a-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3070a-149">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3070a-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3070a-150">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3070a-150">\<binding></span></span>](../../../misc/binding.md)
