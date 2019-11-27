---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430918"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="953cc-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="953cc-101">\<mexHttpBinding></span></span>
<span data-ttu-id="953cc-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="953cc-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="953cc-103">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="953cc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="953cc-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="953cc-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="953cc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="953cc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="953cc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="953cc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="953cc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="953cc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="953cc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="953cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="953cc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="953cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="953cc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="953cc-110">Attributes</span></span>  
  
|<span data-ttu-id="953cc-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="953cc-111">Attribute</span></span>|<span data-ttu-id="953cc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="953cc-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="953cc-113">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="953cc-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="953cc-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="953cc-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="953cc-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="953cc-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="953cc-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="953cc-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="953cc-117">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="953cc-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="953cc-118">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="953cc-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="953cc-119">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="953cc-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="953cc-120">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="953cc-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="953cc-121">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="953cc-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="953cc-122">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="953cc-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="953cc-123">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="953cc-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="953cc-124">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="953cc-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="953cc-125">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="953cc-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="953cc-126">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="953cc-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="953cc-127">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="953cc-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="953cc-128">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="953cc-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="953cc-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="953cc-129">Child Elements</span></span>  
 <span data-ttu-id="953cc-130">Žádné.</span><span class="sxs-lookup"><span data-stu-id="953cc-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="953cc-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="953cc-131">Parent Elements</span></span>  
  
|<span data-ttu-id="953cc-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="953cc-132">Element</span></span>|<span data-ttu-id="953cc-133">Popis</span><span class="sxs-lookup"><span data-stu-id="953cc-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="953cc-134">vazby \<></span><span class="sxs-lookup"><span data-stu-id="953cc-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="953cc-135">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="953cc-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="953cc-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="953cc-136">Remarks</span></span>  
 <span data-ttu-id="953cc-137">Tato vazba je v podstatě `WSHttpBinding` vazbou se zakázaným zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="953cc-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="953cc-138">Podporuje většinu požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="953cc-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="953cc-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="953cc-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="953cc-140">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="953cc-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="953cc-141">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="953cc-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="953cc-142">Metadata</span><span class="sxs-lookup"><span data-stu-id="953cc-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="953cc-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="953cc-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="953cc-144">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="953cc-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="953cc-145">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="953cc-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="953cc-146">vazba \<></span><span class="sxs-lookup"><span data-stu-id="953cc-146">\<binding></span></span>](bindings.md)
