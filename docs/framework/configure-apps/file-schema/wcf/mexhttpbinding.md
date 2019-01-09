---
title: '&lt;mexHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: c60fcf5071d52d30c1b6b99a19640a0fdc1265f8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148653"
---
# <a name="ltmexhttpbindinggt"></a><span data-ttu-id="840c8-102">&lt;mexHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="840c8-102">&lt;mexHttpBinding&gt;</span></span>
<span data-ttu-id="840c8-103">Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="840c8-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="840c8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="840c8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="840c8-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="840c8-105">\<bindings></span></span>  
<span data-ttu-id="840c8-106">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="840c8-106">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="840c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="840c8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="840c8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="840c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="840c8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="840c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="840c8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="840c8-110">Attributes</span></span>  
  
|<span data-ttu-id="840c8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="840c8-111">Attribute</span></span>|<span data-ttu-id="840c8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="840c8-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="840c8-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="840c8-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="840c8-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="840c8-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="840c8-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="840c8-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="840c8-116">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="840c8-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="840c8-117">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="840c8-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="840c8-118">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="840c8-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="840c8-119">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="840c8-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="840c8-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="840c8-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="840c8-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="840c8-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="840c8-122">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="840c8-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="840c8-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="840c8-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="840c8-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="840c8-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="840c8-125">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="840c8-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="840c8-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="840c8-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="840c8-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="840c8-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="840c8-128">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="840c8-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="840c8-129">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="840c8-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="840c8-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="840c8-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="840c8-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="840c8-131">Child Elements</span></span>  
 <span data-ttu-id="840c8-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="840c8-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="840c8-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="840c8-133">Parent Elements</span></span>  
  
|<span data-ttu-id="840c8-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="840c8-134">Element</span></span>|<span data-ttu-id="840c8-135">Popis</span><span class="sxs-lookup"><span data-stu-id="840c8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="840c8-136">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="840c8-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="840c8-137">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="840c8-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="840c8-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="840c8-138">Remarks</span></span>  
 <span data-ttu-id="840c8-139">Tato vazba je v podstatě `WSHttpBinding` vazby se zabezpečením na zakázáno.</span><span class="sxs-lookup"><span data-stu-id="840c8-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="840c8-140">Podporuje většina žádostí o metadata.</span><span class="sxs-lookup"><span data-stu-id="840c8-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="840c8-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="840c8-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpBindingElement>  
 [<span data-ttu-id="840c8-142">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="840c8-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="840c8-143">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="840c8-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="840c8-144">Metadata</span><span class="sxs-lookup"><span data-stu-id="840c8-144">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="840c8-145">Vazby</span><span class="sxs-lookup"><span data-stu-id="840c8-145">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="840c8-146">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="840c8-146">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="840c8-147">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="840c8-147">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="840c8-148">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="840c8-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
