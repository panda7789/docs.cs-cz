---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 4e96c28ac9b372092d06538d24d165dde6c5fe48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203129"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="571be-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="571be-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="571be-102">Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="571be-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="571be-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="571be-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="571be-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="571be-104">\<bindings></span></span>  
<span data-ttu-id="571be-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="571be-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="571be-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="571be-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="571be-107">Attributes and Elements</span></span>  
 <span data-ttu-id="571be-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="571be-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="571be-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="571be-109">Attributes</span></span>  
  
|<span data-ttu-id="571be-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="571be-110">Attribute</span></span>|<span data-ttu-id="571be-111">Popis</span><span class="sxs-lookup"><span data-stu-id="571be-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="571be-112">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="571be-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="571be-113">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="571be-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="571be-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="571be-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="571be-115">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="571be-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="571be-116">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="571be-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="571be-117">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="571be-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="571be-118">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="571be-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="571be-119">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="571be-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="571be-120">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="571be-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="571be-121">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="571be-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="571be-122">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="571be-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="571be-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="571be-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="571be-124">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="571be-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="571be-125">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="571be-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="571be-126">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="571be-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="571be-127">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="571be-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="571be-128">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="571be-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="571be-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="571be-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="571be-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="571be-130">Child Elements</span></span>  
 <span data-ttu-id="571be-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="571be-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="571be-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="571be-132">Parent Elements</span></span>  
  
|<span data-ttu-id="571be-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="571be-133">Element</span></span>|<span data-ttu-id="571be-134">Popis</span><span class="sxs-lookup"><span data-stu-id="571be-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="571be-135">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="571be-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="571be-136">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="571be-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="571be-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="571be-137">Remarks</span></span>  
 <span data-ttu-id="571be-138">Tato vazba je v podstatě `WSHttpBinding` vazby, která podporuje zabezpečení na úrovni přenosu pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="571be-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="571be-139">Další informace o konfiguraci a používání těchto koncových bodů metadat najdete v tématu [jak: Konfigurace vlastního protokolu WS-Metadata Exchange vazby](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [jak: Načítání metadat přes vazbu jiného typu než MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)a ukázku [koncový bod metadat zabezpečení vlastní](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="571be-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571be-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="571be-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="571be-141">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="571be-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="571be-142">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="571be-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="571be-143">Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="571be-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="571be-144">Postupy: Načítání metadat přes vazbu jiného typu než MEX</span><span class="sxs-lookup"><span data-stu-id="571be-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="571be-145">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="571be-145">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="571be-146">Metadata</span><span class="sxs-lookup"><span data-stu-id="571be-146">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="571be-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="571be-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="571be-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="571be-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="571be-149">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="571be-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="571be-150">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="571be-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
