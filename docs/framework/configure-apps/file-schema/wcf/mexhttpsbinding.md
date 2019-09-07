---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: d32db2180e06cba6662ed853ab1a259805680ea1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397826"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="4b5ad-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="4b5ad-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="4b5ad-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="4b5ad-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b5ad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4b5ad-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4b5ad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4b5ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4b5ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4b5ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="4b5ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5ad-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b5ad-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b5ad-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b5ad-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b5ad-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b5ad-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b5ad-110">Attributes</span></span>  
  
|<span data-ttu-id="4b5ad-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="4b5ad-111">Attribute</span></span>|<span data-ttu-id="4b5ad-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4b5ad-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4b5ad-113"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4b5ad-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b5ad-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="4b5ad-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4b5ad-117">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4b5ad-118">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="4b5ad-119">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="4b5ad-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4b5ad-121">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b5ad-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="4b5ad-122"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4b5ad-123">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b5ad-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4b5ad-125"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4b5ad-126">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b5ad-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="4b5ad-128"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4b5ad-129">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b5ad-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b5ad-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b5ad-131">Child Elements</span></span>  
 <span data-ttu-id="4b5ad-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="4b5ad-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b5ad-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b5ad-133">Parent Elements</span></span>  
  
|<span data-ttu-id="4b5ad-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b5ad-134">Element</span></span>|<span data-ttu-id="4b5ad-135">Popis</span><span class="sxs-lookup"><span data-stu-id="4b5ad-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b5ad-136">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="4b5ad-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="4b5ad-137">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b5ad-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b5ad-138">Remarks</span></span>  
 <span data-ttu-id="4b5ad-139">Tato vazba je v podstatě `WSHttpBinding` vazba, která podporuje zabezpečení na úrovni přenosu pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4b5ad-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="4b5ad-140">Další informace o konfiguraci a používání tohoto koncového bodu metadat najdete v [tématu How to: Konfigurace vlastní vazby](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)WS-Metadata Exchange, [jak: Načtěte metadata přes vazbu](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)mimo MEX a ukázka [vlastního zabezpečeného koncového bodu metadat](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="4b5ad-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5ad-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b5ad-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="4b5ad-142">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="4b5ad-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="4b5ad-143">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4b5ad-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="4b5ad-144">Postupy: Konfigurace vlastní vazby WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="4b5ad-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="4b5ad-145">Postupy: Načtení metadat přes vazbu, která není MEX</span><span class="sxs-lookup"><span data-stu-id="4b5ad-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="4b5ad-146">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="4b5ad-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="4b5ad-147">Metadata</span><span class="sxs-lookup"><span data-stu-id="4b5ad-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="4b5ad-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="4b5ad-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4b5ad-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4b5ad-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4b5ad-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4b5ad-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4b5ad-151">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="4b5ad-151">\<binding></span></span>](../../../misc/binding.md)
