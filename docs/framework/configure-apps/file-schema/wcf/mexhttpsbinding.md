---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430340"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="f582f-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="f582f-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="f582f-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f582f-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="f582f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f582f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f582f-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f582f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f582f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f582f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f582f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding>**</span><span class="sxs-lookup"><span data-stu-id="f582f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f582f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f582f-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f582f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f582f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f582f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f582f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f582f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f582f-110">Attributes</span></span>  
  
|<span data-ttu-id="f582f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f582f-111">Attribute</span></span>|<span data-ttu-id="f582f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f582f-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f582f-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="f582f-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f582f-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f582f-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f582f-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f582f-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="f582f-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="f582f-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f582f-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="f582f-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f582f-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="f582f-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f582f-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f582f-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f582f-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="f582f-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f582f-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f582f-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f582f-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f582f-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f582f-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="f582f-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f582f-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f582f-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f582f-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f582f-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f582f-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="f582f-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f582f-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f582f-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f582f-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f582f-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f582f-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f582f-129">Child Elements</span></span>  
 <span data-ttu-id="f582f-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="f582f-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f582f-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f582f-131">Parent Elements</span></span>  
  
|<span data-ttu-id="f582f-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="f582f-132">Element</span></span>|<span data-ttu-id="f582f-133">Popis</span><span class="sxs-lookup"><span data-stu-id="f582f-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f582f-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f582f-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f582f-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="f582f-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f582f-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f582f-136">Remarks</span></span>  
 <span data-ttu-id="f582f-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span><span class="sxs-lookup"><span data-stu-id="f582f-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="f582f-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="f582f-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f582f-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f582f-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="f582f-140">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f582f-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="f582f-141">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f582f-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="f582f-142">Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="f582f-142">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="f582f-143">Postupy: Načítání metadat přes vazbu jiného typu než MEX</span><span class="sxs-lookup"><span data-stu-id="f582f-143">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="f582f-144">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="f582f-144">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="f582f-145">Metadata</span><span class="sxs-lookup"><span data-stu-id="f582f-145">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="f582f-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="f582f-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f582f-147">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f582f-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f582f-148">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f582f-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f582f-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="f582f-149">\<binding></span></span>](bindings.md)
