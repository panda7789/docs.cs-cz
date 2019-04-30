---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 9ac2b967e33571cbe0b4ad5ee81e13b009ffddd3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772460"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="d8e96-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="d8e96-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="d8e96-102">Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="d8e96-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="d8e96-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d8e96-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d8e96-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d8e96-104">\<bindings></span></span>  
<span data-ttu-id="d8e96-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="d8e96-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e96-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8e96-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8e96-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8e96-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d8e96-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8e96-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8e96-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8e96-109">Attributes</span></span>  
  
|<span data-ttu-id="d8e96-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="d8e96-110">Attribute</span></span>|<span data-ttu-id="d8e96-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d8e96-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d8e96-112">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="d8e96-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d8e96-113">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d8e96-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8e96-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d8e96-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="d8e96-115">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="d8e96-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d8e96-116">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="d8e96-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d8e96-117">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="d8e96-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="d8e96-118">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d8e96-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="d8e96-119">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="d8e96-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d8e96-120">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d8e96-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d8e96-121">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="d8e96-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d8e96-122">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d8e96-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8e96-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d8e96-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d8e96-124">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="d8e96-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d8e96-125">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d8e96-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8e96-126">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="d8e96-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d8e96-127">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="d8e96-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d8e96-128">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d8e96-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8e96-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d8e96-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8e96-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8e96-130">Child Elements</span></span>  
 <span data-ttu-id="d8e96-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="d8e96-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8e96-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8e96-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d8e96-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8e96-133">Element</span></span>|<span data-ttu-id="d8e96-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d8e96-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8e96-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d8e96-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="d8e96-136">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="d8e96-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8e96-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8e96-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="d8e96-138">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d8e96-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="d8e96-139">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d8e96-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="d8e96-140">Metadata</span><span class="sxs-lookup"><span data-stu-id="d8e96-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="d8e96-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="d8e96-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d8e96-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d8e96-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d8e96-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d8e96-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d8e96-144">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d8e96-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
