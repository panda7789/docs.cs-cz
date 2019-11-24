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
# <a name="mexnamedpipebinding"></a><span data-ttu-id="8084b-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="8084b-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="8084b-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span><span class="sxs-lookup"><span data-stu-id="8084b-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="8084b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8084b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8084b-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8084b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8084b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8084b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8084b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding>**</span><span class="sxs-lookup"><span data-stu-id="8084b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8084b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8084b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8084b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8084b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8084b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8084b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8084b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8084b-110">Attributes</span></span>  
  
|<span data-ttu-id="8084b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8084b-111">Attribute</span></span>|<span data-ttu-id="8084b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8084b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="8084b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8084b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="8084b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8084b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8084b-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8084b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="8084b-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="8084b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="8084b-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="8084b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8084b-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="8084b-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8084b-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8084b-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="8084b-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8084b-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8084b-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8084b-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8084b-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8084b-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="8084b-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8084b-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8084b-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8084b-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8084b-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="8084b-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="8084b-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="8084b-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8084b-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8084b-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8084b-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8084b-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8084b-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8084b-129">Child Elements</span></span>  
 <span data-ttu-id="8084b-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="8084b-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8084b-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8084b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="8084b-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="8084b-132">Element</span></span>|<span data-ttu-id="8084b-133">Popis</span><span class="sxs-lookup"><span data-stu-id="8084b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8084b-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8084b-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="8084b-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="8084b-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8084b-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8084b-136">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="8084b-137">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8084b-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="8084b-138">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="8084b-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="8084b-139">Metadata</span><span class="sxs-lookup"><span data-stu-id="8084b-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="8084b-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="8084b-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8084b-141">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="8084b-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8084b-142">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8084b-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8084b-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="8084b-143">\<binding></span></span>](bindings.md)
