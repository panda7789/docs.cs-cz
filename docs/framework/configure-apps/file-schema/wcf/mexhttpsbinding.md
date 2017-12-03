---
title: '&lt;mexHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4990965e364765628174f9e8765663c7a7df70d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="cc7fe-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="cc7fe-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="cc7fe-103">Určuje nastavení pro vazba použitá k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="cc7fe-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cc7fe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc7fe-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cc7fe-105">\<bindings></span></span>  
<span data-ttu-id="cc7fe-106">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="cc7fe-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7fe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc7fe-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpsBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc7fe-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cc7fe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cc7fe-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc7fe-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="cc7fe-110">Attributes</span></span>  
  
|<span data-ttu-id="cc7fe-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="cc7fe-111">Attribute</span></span>|<span data-ttu-id="cc7fe-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cc7fe-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="cc7fe-113">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="cc7fe-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc7fe-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="cc7fe-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="cc7fe-117">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="cc7fe-118">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="cc7fe-119">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="cc7fe-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="cc7fe-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cc7fe-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="cc7fe-122">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="cc7fe-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc7fe-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="cc7fe-125">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="cc7fe-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc7fe-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="cc7fe-128">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="cc7fe-129">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cc7fe-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc7fe-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cc7fe-131">Child Elements</span></span>  
 <span data-ttu-id="cc7fe-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="cc7fe-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc7fe-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cc7fe-133">Parent Elements</span></span>  
  
|<span data-ttu-id="cc7fe-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc7fe-134">Element</span></span>|<span data-ttu-id="cc7fe-135">Popis</span><span class="sxs-lookup"><span data-stu-id="cc7fe-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc7fe-136">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cc7fe-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="cc7fe-137">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc7fe-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc7fe-138">Remarks</span></span>  
 <span data-ttu-id="cc7fe-139">Tato vazba je v podstatě `WSHttpBinding` vazby, která podporuje použití certifikátů zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="cc7fe-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="cc7fe-140">Další informace o konfiguraci a použití takových koncový bod metadat najdete v tématu [postupy: Konfigurace vazbu pro Exchange vlastní WS-Metadata](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [postupy: načtení metadat přes vazbu jiného typu-MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)a Ukázka [koncový bod metadat zabezpečení vlastní](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="cc7fe-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7fe-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc7fe-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="cc7fe-142">Postupy: publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="cc7fe-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="cc7fe-143">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="cc7fe-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="cc7fe-144">Postupy: Konfigurace vlastních metadat WS Exchange vazby</span><span class="sxs-lookup"><span data-stu-id="cc7fe-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="cc7fe-145">Postupy: načítání metadat přes vazbu jiného typu-MEX</span><span class="sxs-lookup"><span data-stu-id="cc7fe-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="cc7fe-146">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="cc7fe-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="cc7fe-147">Metadata</span><span class="sxs-lookup"><span data-stu-id="cc7fe-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="cc7fe-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="cc7fe-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cc7fe-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="cc7fe-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cc7fe-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="cc7fe-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cc7fe-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cc7fe-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
