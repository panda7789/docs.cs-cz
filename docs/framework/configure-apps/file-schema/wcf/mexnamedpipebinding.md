---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 41f5b19f5067d9ac7faa2c7329dd07dd9d48e9b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430870"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="91568-101">\<mexNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="91568-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="91568-102">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="91568-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="91568-103">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91568-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91568-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="91568-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="91568-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="91568-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="91568-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="91568-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91568-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91568-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91568-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="91568-108">Attributes and Elements</span></span>  
 <span data-ttu-id="91568-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="91568-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91568-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="91568-110">Attributes</span></span>  
  
|<span data-ttu-id="91568-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="91568-111">Attribute</span></span>|<span data-ttu-id="91568-112">Popis</span><span class="sxs-lookup"><span data-stu-id="91568-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="91568-113">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="91568-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="91568-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="91568-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="91568-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="91568-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="91568-116">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="91568-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="91568-117">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="91568-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="91568-118">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="91568-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="91568-119">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="91568-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="91568-120">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="91568-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="91568-121">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="91568-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="91568-122">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="91568-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="91568-123">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="91568-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="91568-124">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="91568-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="91568-125">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="91568-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="91568-126">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="91568-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="91568-127">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="91568-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="91568-128">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="91568-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91568-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="91568-129">Child Elements</span></span>  
 <span data-ttu-id="91568-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="91568-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91568-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="91568-131">Parent Elements</span></span>  
  
|<span data-ttu-id="91568-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="91568-132">Element</span></span>|<span data-ttu-id="91568-133">Popis</span><span class="sxs-lookup"><span data-stu-id="91568-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91568-134">vazby \<></span><span class="sxs-lookup"><span data-stu-id="91568-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="91568-135">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="91568-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91568-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91568-136">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="91568-137">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="91568-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="91568-138">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="91568-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="91568-139">Metadata</span><span class="sxs-lookup"><span data-stu-id="91568-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="91568-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="91568-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="91568-141">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="91568-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="91568-142">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="91568-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="91568-143">vazba \<></span><span class="sxs-lookup"><span data-stu-id="91568-143">\<binding></span></span>](bindings.md)
