---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430918"
---
# \<mexHttpBinding>
<span data-ttu-id="3be98-101">Určuje nastavení pro vazbu, která se používá pro výměnu zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="3be98-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="3be98-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3be98-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3be98-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3be98-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3be98-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3be98-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3be98-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="3be98-105">Attributes</span></span>  
  
|<span data-ttu-id="3be98-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="3be98-106">Attribute</span></span>|<span data-ttu-id="3be98-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3be98-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="3be98-108"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="3be98-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3be98-109">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3be98-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3be98-110">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3be98-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="3be98-111">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="3be98-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3be98-112">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="3be98-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="3be98-113">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="3be98-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3be98-114">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3be98-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="3be98-115"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="3be98-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3be98-116">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3be98-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3be98-117">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3be98-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="3be98-118"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="3be98-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3be98-119">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3be98-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3be98-120">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="3be98-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="3be98-121"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="3be98-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3be98-122">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3be98-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3be98-123">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3be98-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3be98-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3be98-124">Child Elements</span></span>  
 <span data-ttu-id="3be98-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="3be98-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3be98-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3be98-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3be98-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="3be98-127">Element</span></span>|<span data-ttu-id="3be98-128">Description</span><span class="sxs-lookup"><span data-stu-id="3be98-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="3be98-129">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="3be98-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3be98-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3be98-130">Remarks</span></span>  
 <span data-ttu-id="3be98-131">Tato vazba je v podstatě `WSHttpBinding` vazba se zakázaným zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="3be98-131">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="3be98-132">Podporuje většinu požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="3be98-132">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be98-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="3be98-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="3be98-134">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3be98-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="3be98-135">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3be98-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="3be98-136">Metadata</span><span class="sxs-lookup"><span data-stu-id="3be98-136">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="3be98-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="3be98-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3be98-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3be98-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3be98-139">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3be98-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
