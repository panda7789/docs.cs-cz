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
# <a name="mexhttpbinding"></a><span data-ttu-id="00062-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="00062-101">\<mexHttpBinding></span></span>
<span data-ttu-id="00062-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span><span class="sxs-lookup"><span data-stu-id="00062-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="00062-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="00062-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="00062-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="00062-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="00062-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="00062-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="00062-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding>**</span><span class="sxs-lookup"><span data-stu-id="00062-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00062-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00062-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00062-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="00062-108">Attributes and Elements</span></span>  
 <span data-ttu-id="00062-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="00062-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00062-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="00062-110">Attributes</span></span>  
  
|<span data-ttu-id="00062-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="00062-111">Attribute</span></span>|<span data-ttu-id="00062-112">Popis</span><span class="sxs-lookup"><span data-stu-id="00062-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="00062-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="00062-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="00062-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="00062-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00062-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="00062-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="00062-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="00062-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="00062-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="00062-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="00062-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="00062-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="00062-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="00062-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="00062-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="00062-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="00062-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="00062-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00062-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="00062-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="00062-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="00062-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="00062-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="00062-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00062-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="00062-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="00062-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="00062-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="00062-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="00062-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00062-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="00062-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00062-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="00062-129">Child Elements</span></span>  
 <span data-ttu-id="00062-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="00062-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00062-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="00062-131">Parent Elements</span></span>  
  
|<span data-ttu-id="00062-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="00062-132">Element</span></span>|<span data-ttu-id="00062-133">Popis</span><span class="sxs-lookup"><span data-stu-id="00062-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00062-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="00062-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="00062-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="00062-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00062-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00062-136">Remarks</span></span>  
 <span data-ttu-id="00062-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span><span class="sxs-lookup"><span data-stu-id="00062-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="00062-138">It supports most metadata requests.</span><span class="sxs-lookup"><span data-stu-id="00062-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00062-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00062-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="00062-140">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="00062-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="00062-141">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="00062-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="00062-142">Metadata</span><span class="sxs-lookup"><span data-stu-id="00062-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="00062-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="00062-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="00062-144">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="00062-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="00062-145">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="00062-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="00062-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="00062-146">\<binding></span></span>](bindings.md)
