---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8a8145bbfcb3eefb06d159d834232d94166fa6dd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736717"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="c2a42-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c2a42-101">\<mexHttpBinding></span></span>
<span data-ttu-id="c2a42-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="c2a42-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="c2a42-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c2a42-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2a42-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c2a42-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c2a42-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c2a42-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c2a42-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="c2a42-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a42-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2a42-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2a42-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2a42-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c2a42-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2a42-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2a42-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2a42-110">Attributes</span></span>  
  
|<span data-ttu-id="c2a42-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2a42-111">Attribute</span></span>|<span data-ttu-id="c2a42-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c2a42-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="c2a42-113">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="c2a42-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c2a42-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c2a42-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c2a42-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c2a42-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="c2a42-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="c2a42-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c2a42-117">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="c2a42-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c2a42-118">Každá vazba má atribut `name` a `namespace`, který ji společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="c2a42-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="c2a42-119">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="c2a42-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="c2a42-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="c2a42-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c2a42-121">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c2a42-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="c2a42-122">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="c2a42-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c2a42-123">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c2a42-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c2a42-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c2a42-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="c2a42-125">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="c2a42-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c2a42-126">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c2a42-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c2a42-127">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="c2a42-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="c2a42-128">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="c2a42-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c2a42-129">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c2a42-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c2a42-130">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c2a42-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2a42-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2a42-131">Child Elements</span></span>  
 <span data-ttu-id="c2a42-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2a42-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2a42-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2a42-133">Parent Elements</span></span>  
  
|<span data-ttu-id="c2a42-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2a42-134">Element</span></span>|<span data-ttu-id="c2a42-135">Popis</span><span class="sxs-lookup"><span data-stu-id="c2a42-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2a42-136">vazby\<</span><span class="sxs-lookup"><span data-stu-id="c2a42-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="c2a42-137">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="c2a42-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2a42-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2a42-138">Remarks</span></span>  
 <span data-ttu-id="c2a42-139">Tato vazba je v podstatě `WSHttpBinding` vazbou se zakázaným zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="c2a42-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="c2a42-140">Podporuje většinu požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="c2a42-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a42-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2a42-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="c2a42-142">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c2a42-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="c2a42-143">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c2a42-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="c2a42-144">Metadata</span><span class="sxs-lookup"><span data-stu-id="c2a42-144">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="c2a42-145">Vazby</span><span class="sxs-lookup"><span data-stu-id="c2a42-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c2a42-146">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="c2a42-146">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c2a42-147">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c2a42-147">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c2a42-148">vazba \<</span><span class="sxs-lookup"><span data-stu-id="c2a42-148">\<binding></span></span>](bindings.md)
