---
title: '&lt;mexHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 37b8ef1c842e1b9082ebcf0f2996b74cafc5c133
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510690"
---
# <a name="ltmexhttpbindinggt"></a><span data-ttu-id="42d16-102">&lt;mexHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="42d16-102">&lt;mexHttpBinding&gt;</span></span>
<span data-ttu-id="42d16-103">Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="42d16-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="42d16-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="42d16-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="42d16-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="42d16-105">\<bindings></span></span>  
<span data-ttu-id="42d16-106">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="42d16-106">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42d16-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42d16-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42d16-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42d16-108">Attributes and Elements</span></span>  
 <span data-ttu-id="42d16-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="42d16-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42d16-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="42d16-110">Attributes</span></span>  
  
|<span data-ttu-id="42d16-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="42d16-111">Attribute</span></span>|<span data-ttu-id="42d16-112">Popis</span><span class="sxs-lookup"><span data-stu-id="42d16-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="42d16-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="42d16-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="42d16-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42d16-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42d16-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="42d16-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="42d16-116">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="42d16-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="42d16-117">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="42d16-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="42d16-118">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="42d16-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="42d16-119">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="42d16-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="42d16-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="42d16-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="42d16-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="42d16-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="42d16-122">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="42d16-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="42d16-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42d16-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42d16-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="42d16-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="42d16-125">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="42d16-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="42d16-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42d16-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42d16-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="42d16-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="42d16-128">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="42d16-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="42d16-129">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42d16-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42d16-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="42d16-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42d16-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42d16-131">Child Elements</span></span>  
 <span data-ttu-id="42d16-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="42d16-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42d16-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42d16-133">Parent Elements</span></span>  
  
|<span data-ttu-id="42d16-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="42d16-134">Element</span></span>|<span data-ttu-id="42d16-135">Popis</span><span class="sxs-lookup"><span data-stu-id="42d16-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42d16-136">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="42d16-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="42d16-137">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="42d16-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42d16-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42d16-138">Remarks</span></span>  
 <span data-ttu-id="42d16-139">Tato vazba je v podstatě `WSHttpBinding` vazby se zabezpečením na zakázáno.</span><span class="sxs-lookup"><span data-stu-id="42d16-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="42d16-140">Podporuje většina žádostí o metadata.</span><span class="sxs-lookup"><span data-stu-id="42d16-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d16-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="42d16-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpBindingElement>  
 [<span data-ttu-id="42d16-142">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="42d16-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="42d16-143">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="42d16-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="42d16-144">Metadata</span><span class="sxs-lookup"><span data-stu-id="42d16-144">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="42d16-145">Vazby</span><span class="sxs-lookup"><span data-stu-id="42d16-145">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="42d16-146">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="42d16-146">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="42d16-147">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="42d16-147">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="42d16-148">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="42d16-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
