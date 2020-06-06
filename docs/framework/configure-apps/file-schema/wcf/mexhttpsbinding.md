---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430340"
---
# \<mexHttpsBinding>
<span data-ttu-id="12c72-101">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="12c72-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="12c72-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c72-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12c72-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12c72-103">Attributes and Elements</span></span>  
 <span data-ttu-id="12c72-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="12c72-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12c72-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="12c72-105">Attributes</span></span>  
  
|<span data-ttu-id="12c72-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="12c72-106">Attribute</span></span>|<span data-ttu-id="12c72-107">Popis</span><span class="sxs-lookup"><span data-stu-id="12c72-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="12c72-108"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="12c72-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="12c72-109">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="12c72-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="12c72-110">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="12c72-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="12c72-111">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="12c72-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="12c72-112">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="12c72-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="12c72-113">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="12c72-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="12c72-114">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="12c72-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="12c72-115"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="12c72-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="12c72-116">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="12c72-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="12c72-117">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="12c72-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="12c72-118"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="12c72-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="12c72-119">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="12c72-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="12c72-120">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="12c72-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="12c72-121"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="12c72-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="12c72-122">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="12c72-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="12c72-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="12c72-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12c72-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="12c72-124">Child Elements</span></span>  
 <span data-ttu-id="12c72-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="12c72-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12c72-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12c72-126">Parent Elements</span></span>  
  
|<span data-ttu-id="12c72-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="12c72-127">Element</span></span>|<span data-ttu-id="12c72-128">Description</span><span class="sxs-lookup"><span data-stu-id="12c72-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="12c72-129">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="12c72-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12c72-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12c72-130">Remarks</span></span>  
 <span data-ttu-id="12c72-131">Tato vazba je v podstatě `WSHttpBinding` vazba, která podporuje zabezpečení na úrovni přenosu pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="12c72-131">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="12c72-132">Další informace o konfiguraci a použití tohoto koncového bodu metadat naleznete v tématu [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: načítat metadata přes vazbu mimo MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)a ukázkový [Vlastní zabezpečený koncový bod metadat](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="12c72-132">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c72-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="12c72-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="12c72-134">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="12c72-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="12c72-135">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="12c72-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="12c72-136">Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="12c72-136">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="12c72-137">Postupy: Načítání metadat přes vazbu jiného typu než MEX</span><span class="sxs-lookup"><span data-stu-id="12c72-137">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="12c72-138">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="12c72-138">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="12c72-139">Metadata</span><span class="sxs-lookup"><span data-stu-id="12c72-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="12c72-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="12c72-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="12c72-141">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="12c72-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="12c72-142">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="12c72-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
