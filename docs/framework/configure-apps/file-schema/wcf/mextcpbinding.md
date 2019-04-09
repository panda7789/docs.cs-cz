---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 9e76d65a27e7732d1d62c4ba25afac76d73be167
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078886"
---
# <a name="mextcpbinding"></a><span data-ttu-id="f02b3-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f02b3-101">\<mexTcpBinding></span></span>
<span data-ttu-id="f02b3-102">Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="f02b3-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="f02b3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f02b3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f02b3-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f02b3-104">\<bindings></span></span>  
<span data-ttu-id="f02b3-105">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f02b3-105">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f02b3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f02b3-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f02b3-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f02b3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f02b3-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f02b3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f02b3-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="f02b3-109">Attributes</span></span>  
  
|<span data-ttu-id="f02b3-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="f02b3-110">Attribute</span></span>|<span data-ttu-id="f02b3-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f02b3-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f02b3-112">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="f02b3-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f02b3-113">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f02b3-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f02b3-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f02b3-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="f02b3-115">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="f02b3-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f02b3-116">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f02b3-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f02b3-117">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="f02b3-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="f02b3-118">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f02b3-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="f02b3-119">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="f02b3-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f02b3-120">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f02b3-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f02b3-121">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="f02b3-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f02b3-122">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f02b3-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f02b3-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f02b3-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f02b3-124">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="f02b3-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f02b3-125">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f02b3-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f02b3-126">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f02b3-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f02b3-127">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="f02b3-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f02b3-128">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f02b3-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f02b3-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f02b3-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f02b3-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f02b3-130">Child Elements</span></span>  
 <span data-ttu-id="f02b3-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="f02b3-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f02b3-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f02b3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f02b3-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="f02b3-133">Element</span></span>|<span data-ttu-id="f02b3-134">Popis</span><span class="sxs-lookup"><span data-stu-id="f02b3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f02b3-135">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f02b3-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="f02b3-136">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="f02b3-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f02b3-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f02b3-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="f02b3-138">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f02b3-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="f02b3-139">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f02b3-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="f02b3-140">Metadata</span><span class="sxs-lookup"><span data-stu-id="f02b3-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="f02b3-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="f02b3-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f02b3-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f02b3-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f02b3-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f02b3-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f02b3-144">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="f02b3-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
