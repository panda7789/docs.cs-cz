---
title: '&lt;mexHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: e39a4e1e6b1b2346f3a6e0ca36d91d3719009be1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151914"
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="eba0e-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="eba0e-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="eba0e-103">Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eba0e-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="eba0e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eba0e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="eba0e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="eba0e-105">\<bindings></span></span>  
<span data-ttu-id="eba0e-106">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="eba0e-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba0e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eba0e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eba0e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eba0e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eba0e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eba0e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eba0e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="eba0e-110">Attributes</span></span>  
  
|<span data-ttu-id="eba0e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="eba0e-111">Attribute</span></span>|<span data-ttu-id="eba0e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="eba0e-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="eba0e-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="eba0e-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="eba0e-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eba0e-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eba0e-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="eba0e-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="eba0e-116">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="eba0e-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="eba0e-117">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="eba0e-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="eba0e-118">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="eba0e-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="eba0e-119">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="eba0e-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="eba0e-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="eba0e-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="eba0e-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="eba0e-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="eba0e-122">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="eba0e-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="eba0e-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eba0e-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eba0e-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="eba0e-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="eba0e-125">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="eba0e-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="eba0e-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eba0e-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eba0e-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="eba0e-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="eba0e-128">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="eba0e-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="eba0e-129">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="eba0e-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="eba0e-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="eba0e-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eba0e-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eba0e-131">Child Elements</span></span>  
 <span data-ttu-id="eba0e-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="eba0e-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eba0e-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eba0e-133">Parent Elements</span></span>  
  
|<span data-ttu-id="eba0e-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="eba0e-134">Element</span></span>|<span data-ttu-id="eba0e-135">Popis</span><span class="sxs-lookup"><span data-stu-id="eba0e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eba0e-136">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="eba0e-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="eba0e-137">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="eba0e-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba0e-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eba0e-138">Remarks</span></span>  
 <span data-ttu-id="eba0e-139">Tato vazba je v podstatě `WSHttpBinding` vazby, která podporuje zabezpečení na úrovni přenosu pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="eba0e-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="eba0e-140">Další informace o konfiguraci a používání těchto koncových bodů metadat najdete v tématu [jak: Konfigurace vlastního protokolu WS-Metadata Exchange vazby](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [jak: Načítání metadat přes vazbu jiného typu než MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)a ukázku [koncový bod metadat zabezpečení vlastní](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="eba0e-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba0e-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="eba0e-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="eba0e-142">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="eba0e-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="eba0e-143">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="eba0e-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="eba0e-144">Postupy: Konfigurace vlastního protokolu WS-Metadata Exchange vazby</span><span class="sxs-lookup"><span data-stu-id="eba0e-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="eba0e-145">Postupy: Načítání metadat přes vazbu jiného typu než MEX</span><span class="sxs-lookup"><span data-stu-id="eba0e-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="eba0e-146">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="eba0e-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="eba0e-147">Metadata</span><span class="sxs-lookup"><span data-stu-id="eba0e-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="eba0e-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="eba0e-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="eba0e-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="eba0e-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="eba0e-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="eba0e-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="eba0e-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="eba0e-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
