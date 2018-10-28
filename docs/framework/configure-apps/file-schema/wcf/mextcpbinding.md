---
title: '&lt;mexTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: dbe9e6c3b7a515ee4b5bb147f973423df0f175ea
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187696"
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="39bb3-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="39bb3-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="39bb3-103">Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="39bb3-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="39bb3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39bb3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39bb3-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="39bb3-105">\<bindings></span></span>  
<span data-ttu-id="39bb3-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="39bb3-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bb3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39bb3-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39bb3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39bb3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39bb3-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39bb3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39bb3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="39bb3-110">Attributes</span></span>  
  
|<span data-ttu-id="39bb3-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="39bb3-111">Attribute</span></span>|<span data-ttu-id="39bb3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="39bb3-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="39bb3-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="39bb3-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="39bb3-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39bb3-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39bb3-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39bb3-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="39bb3-116">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="39bb3-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="39bb3-117">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="39bb3-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="39bb3-118">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="39bb3-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="39bb3-119">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="39bb3-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="39bb3-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="39bb3-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="39bb3-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="39bb3-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="39bb3-122">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="39bb3-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="39bb3-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39bb3-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39bb3-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39bb3-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="39bb3-125">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="39bb3-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="39bb3-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39bb3-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39bb3-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="39bb3-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="39bb3-128">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="39bb3-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="39bb3-129">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39bb3-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39bb3-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39bb3-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39bb3-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39bb3-131">Child Elements</span></span>  
 <span data-ttu-id="39bb3-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="39bb3-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39bb3-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39bb3-133">Parent Elements</span></span>  
  
|<span data-ttu-id="39bb3-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="39bb3-134">Element</span></span>|<span data-ttu-id="39bb3-135">Popis</span><span class="sxs-lookup"><span data-stu-id="39bb3-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39bb3-136">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="39bb3-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="39bb3-137">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="39bb3-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39bb3-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="39bb3-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="39bb3-139">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="39bb3-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="39bb3-140">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="39bb3-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="39bb3-141">Metadata</span><span class="sxs-lookup"><span data-stu-id="39bb3-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="39bb3-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="39bb3-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="39bb3-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="39bb3-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="39bb3-144">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="39bb3-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="39bb3-145">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="39bb3-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
