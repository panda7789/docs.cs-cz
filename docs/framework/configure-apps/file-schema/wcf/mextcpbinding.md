---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430302"
---
# <a name="mextcpbinding"></a><span data-ttu-id="5f027-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="5f027-101">\<mexTcpBinding></span></span>
<span data-ttu-id="5f027-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span><span class="sxs-lookup"><span data-stu-id="5f027-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
<span data-ttu-id="5f027-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5f027-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5f027-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5f027-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5f027-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5f027-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5f027-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexTcpBinding>**</span><span class="sxs-lookup"><span data-stu-id="5f027-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f027-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f027-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f027-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5f027-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5f027-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5f027-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f027-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5f027-110">Attributes</span></span>  
  
|<span data-ttu-id="5f027-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5f027-111">Attribute</span></span>|<span data-ttu-id="5f027-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5f027-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="5f027-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="5f027-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5f027-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f027-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f027-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5f027-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="5f027-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="5f027-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5f027-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="5f027-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5f027-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="5f027-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5f027-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5f027-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="5f027-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="5f027-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5f027-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f027-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f027-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5f027-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5f027-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="5f027-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5f027-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f027-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f027-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="5f027-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="5f027-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="5f027-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5f027-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5f027-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5f027-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5f027-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f027-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5f027-129">Child Elements</span></span>  
 <span data-ttu-id="5f027-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="5f027-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f027-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5f027-131">Parent Elements</span></span>  
  
|<span data-ttu-id="5f027-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="5f027-132">Element</span></span>|<span data-ttu-id="5f027-133">Popis</span><span class="sxs-lookup"><span data-stu-id="5f027-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f027-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="5f027-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="5f027-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="5f027-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f027-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f027-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="5f027-137">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5f027-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="5f027-138">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5f027-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="5f027-139">Metadata</span><span class="sxs-lookup"><span data-stu-id="5f027-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="5f027-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="5f027-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5f027-141">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5f027-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5f027-142">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5f027-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5f027-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="5f027-143">\<binding></span></span>](bindings.md)
