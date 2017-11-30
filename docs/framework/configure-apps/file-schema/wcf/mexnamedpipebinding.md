---
title: '&lt;mexNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e786d2f18fca2b04e0a46536e539895890fc67d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmexnamedpipebindinggt"></a><span data-ttu-id="f9193-102">&lt;mexNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f9193-102">&lt;mexNamedPipeBinding&gt;</span></span>
<span data-ttu-id="f9193-103">Určuje nastavení pro vazba použitá k výměně zpráv WS-MetadataExchange (WS-MEX) přes pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="f9193-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="f9193-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f9193-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9193-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f9193-105">\<bindings></span></span>  
<span data-ttu-id="f9193-106">\<mexNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="f9193-106">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9193-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9193-107">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9193-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9193-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f9193-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9193-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9193-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9193-110">Attributes</span></span>  
  
|<span data-ttu-id="f9193-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f9193-111">Attribute</span></span>|<span data-ttu-id="f9193-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f9193-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f9193-113">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="f9193-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f9193-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9193-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9193-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f9193-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="f9193-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="f9193-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f9193-117">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f9193-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f9193-118">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="f9193-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="f9193-119">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f9193-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="f9193-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="f9193-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f9193-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f9193-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f9193-122">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="f9193-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f9193-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9193-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9193-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f9193-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f9193-125">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="f9193-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f9193-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9193-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9193-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f9193-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f9193-128">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="f9193-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f9193-129">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f9193-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f9193-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f9193-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9193-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9193-131">Child Elements</span></span>  
 <span data-ttu-id="f9193-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="f9193-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9193-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9193-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f9193-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9193-134">Element</span></span>|<span data-ttu-id="f9193-135">Popis</span><span class="sxs-lookup"><span data-stu-id="f9193-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9193-136">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f9193-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="f9193-137">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="f9193-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9193-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9193-138">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>  
 [<span data-ttu-id="f9193-139">Postupy: publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f9193-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="f9193-140">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f9193-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="f9193-141">Metadata</span><span class="sxs-lookup"><span data-stu-id="f9193-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="f9193-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="f9193-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f9193-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f9193-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f9193-144">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="f9193-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f9193-145">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f9193-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
