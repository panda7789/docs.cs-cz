---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398019"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="beecd-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="beecd-101">\<endpointDiscovery></span></span>
<span data-ttu-id="beecd-102">Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="beecd-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="beecd-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="beecd-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="beecd-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="beecd-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="beecd-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="beecd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="beecd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="beecd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="beecd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="beecd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="beecd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="beecd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beecd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beecd-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beecd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="beecd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="beecd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="beecd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beecd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="beecd-112">Attributes</span></span>  
  
|<span data-ttu-id="beecd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="beecd-113">Attribute</span></span>|<span data-ttu-id="beecd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="beecd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="beecd-115">enabled</span><span class="sxs-lookup"><span data-stu-id="beecd-115">enabled</span></span>|<span data-ttu-id="beecd-116">Logická hodnota, která určuje, zda je na tomto koncovém bodu povolena zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="beecd-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="beecd-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="beecd-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="beecd-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="beecd-118">Child Elements</span></span>  
  
|<span data-ttu-id="beecd-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="beecd-119">Element</span></span>|<span data-ttu-id="beecd-120">Popis</span><span class="sxs-lookup"><span data-stu-id="beecd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beecd-121">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="beecd-121">\<scopes></span></span>](scopes.md)|<span data-ttu-id="beecd-122">Kolekce identifikátorů URI oboru pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="beecd-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="beecd-123">K jednomu koncovému bodu lze přidružit více než jeden identifikátor URI oboru.</span><span class="sxs-lookup"><span data-stu-id="beecd-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="beecd-124">rozšíření > [z \<> endpointDiscovery] [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="beecd-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="beecd-125">Kolekce elementů XML, které umožňují zadat vlastní metadata, která budou publikována pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="beecd-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="beecd-126">\<> typů</span><span class="sxs-lookup"><span data-stu-id="beecd-126">\<types></span></span>|<span data-ttu-id="beecd-127">Kolekce rozhraní, která se mají vyhledat</span><span class="sxs-lookup"><span data-stu-id="beecd-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="beecd-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="beecd-128">Parent Elements</span></span>  
  
|<span data-ttu-id="beecd-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="beecd-129">Element</span></span>|<span data-ttu-id="beecd-130">Popis</span><span class="sxs-lookup"><span data-stu-id="beecd-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beecd-131">\<> chování</span><span class="sxs-lookup"><span data-stu-id="beecd-131">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="beecd-132">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="beecd-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="beecd-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="beecd-133">Remarks</span></span>  
 <span data-ttu-id="beecd-134">Po přidání do konfigurace chování koncového bodu a s `enabled` atributem nastaveným na `true`může tento prvek konfigurace povolit svou zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="beecd-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="beecd-135">Kromě toho můžete použít [ \<rozsahy >](scopes.md)podřízených element k určení identifikátorů URI vlastního rozsahu, které lze použít k filtrování koncových bodů služby během dotazu a také [ \<rozšíření >](extensions.md) podřízený element k určení vlastního metadata, která se mají publikovat společně se standardními zjistitelnými metadaty (EPR, ContractTypeName, Binding, Scope a ListenURI).</span><span class="sxs-lookup"><span data-stu-id="beecd-135">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="beecd-136">Tento prvek konfigurace je závislý na [ \<prvku serviceDiscovery >](servicediscovery.md) , který poskytuje kontrolu úrovně služeb pro zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="beecd-136">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="beecd-137">To znamená, že nastavení tohoto prvku budou ignorována, pokud [ \<serviceDiscovery >](servicediscovery.md) není v konfiguraci k dispozici.</span><span class="sxs-lookup"><span data-stu-id="beecd-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beecd-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="beecd-138">Example</span></span>  
 <span data-ttu-id="beecd-139">Následující příklad konfigurace určuje rozsahy filtrování a metadata rozšíření, která se mají publikovat pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="beecd-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="beecd-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="beecd-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
