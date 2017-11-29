---
title: '&lt;mexHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e8e9a13553e8b7463f7bb7f66c1a38dc1d4ac36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmexhttpbindinggt"></a><span data-ttu-id="5f12b-102">&lt;mexHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5f12b-102">&lt;mexHttpBinding&gt;</span></span>
<span data-ttu-id="5f12b-103">Určuje nastavení pro vazba použitá k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="5f12b-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="5f12b-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5f12b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5f12b-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5f12b-105">\<bindings></span></span>  
<span data-ttu-id="5f12b-106">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5f12b-106">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f12b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f12b-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f12b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5f12b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5f12b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5f12b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f12b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5f12b-110">Attributes</span></span>  
  
|<span data-ttu-id="5f12b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5f12b-111">Attribute</span></span>|<span data-ttu-id="5f12b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5f12b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="5f12b-113">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="5f12b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5f12b-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f12b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f12b-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5f12b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="5f12b-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="5f12b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5f12b-117">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="5f12b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5f12b-118">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="5f12b-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="5f12b-119">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5f12b-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="5f12b-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="5f12b-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5f12b-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5f12b-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="5f12b-122">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="5f12b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5f12b-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f12b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f12b-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5f12b-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5f12b-125">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="5f12b-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5f12b-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f12b-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f12b-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="5f12b-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="5f12b-128">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="5f12b-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5f12b-129">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f12b-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f12b-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5f12b-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f12b-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5f12b-131">Child Elements</span></span>  
 <span data-ttu-id="5f12b-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="5f12b-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f12b-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5f12b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="5f12b-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="5f12b-134">Element</span></span>|<span data-ttu-id="5f12b-135">Popis</span><span class="sxs-lookup"><span data-stu-id="5f12b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f12b-136">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5f12b-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="5f12b-137">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="5f12b-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f12b-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f12b-138">Remarks</span></span>  
 <span data-ttu-id="5f12b-139">Tato vazba je v podstatě `WSHttpBinding` s zabezpečení zakázán.</span><span class="sxs-lookup"><span data-stu-id="5f12b-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="5f12b-140">Podporuje většinu požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="5f12b-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f12b-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f12b-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpBindingElement>  
 [<span data-ttu-id="5f12b-142">Postupy: publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5f12b-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="5f12b-143">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5f12b-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="5f12b-144">Metadata</span><span class="sxs-lookup"><span data-stu-id="5f12b-144">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="5f12b-145">Vazby</span><span class="sxs-lookup"><span data-stu-id="5f12b-145">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5f12b-146">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5f12b-146">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5f12b-147">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="5f12b-147">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5f12b-148">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="5f12b-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
