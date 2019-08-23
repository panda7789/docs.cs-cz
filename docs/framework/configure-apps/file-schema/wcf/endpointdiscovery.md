---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919052"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="02f55-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="02f55-101">\<endpointDiscovery></span></span>
<span data-ttu-id="02f55-102">Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="02f55-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="02f55-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="02f55-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="02f55-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="02f55-104">\<behaviors></span></span>  
<span data-ttu-id="02f55-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="02f55-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="02f55-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="02f55-106">\<behavior></span></span>  
<span data-ttu-id="02f55-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="02f55-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f55-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02f55-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02f55-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="02f55-109">Attributes and Elements</span></span>  
 <span data-ttu-id="02f55-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="02f55-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02f55-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="02f55-111">Attributes</span></span>  
  
|<span data-ttu-id="02f55-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="02f55-112">Attribute</span></span>|<span data-ttu-id="02f55-113">Popis</span><span class="sxs-lookup"><span data-stu-id="02f55-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02f55-114">enabled</span><span class="sxs-lookup"><span data-stu-id="02f55-114">enabled</span></span>|<span data-ttu-id="02f55-115">Logická hodnota, která určuje, zda je na tomto koncovém bodu povolena zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="02f55-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="02f55-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="02f55-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02f55-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="02f55-117">Child Elements</span></span>  
  
|<span data-ttu-id="02f55-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="02f55-118">Element</span></span>|<span data-ttu-id="02f55-119">Popis</span><span class="sxs-lookup"><span data-stu-id="02f55-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02f55-120">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="02f55-120">\<scopes></span></span>](scopes.md)|<span data-ttu-id="02f55-121">Kolekce identifikátorů URI oboru pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02f55-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="02f55-122">K jednomu koncovému bodu lze přidružit více než jeden identifikátor URI oboru.</span><span class="sxs-lookup"><span data-stu-id="02f55-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="02f55-123">rozšíření > [z \<> endpointDiscovery] [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="02f55-123">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="02f55-124">Kolekce elementů XML, které umožňují zadat vlastní metadata, která budou publikována pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02f55-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="02f55-125">\<> typů</span><span class="sxs-lookup"><span data-stu-id="02f55-125">\<types></span></span>|<span data-ttu-id="02f55-126">Kolekce rozhraní, která se mají vyhledat</span><span class="sxs-lookup"><span data-stu-id="02f55-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02f55-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="02f55-127">Parent Elements</span></span>  
  
|<span data-ttu-id="02f55-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="02f55-128">Element</span></span>|<span data-ttu-id="02f55-129">Popis</span><span class="sxs-lookup"><span data-stu-id="02f55-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02f55-130">\<> chování</span><span class="sxs-lookup"><span data-stu-id="02f55-130">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="02f55-131">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="02f55-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="02f55-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02f55-132">Remarks</span></span>  
 <span data-ttu-id="02f55-133">Po přidání do konfigurace chování koncového bodu a s `enabled` atributem nastaveným na `true`může tento prvek konfigurace povolit svou zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="02f55-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="02f55-134">Kromě toho můžete použít [ \<rozsahy >](scopes.md)podřízených element k určení identifikátorů URI vlastního rozsahu, které lze použít k filtrování koncových bodů služby během dotazu a také [ \<rozšíření >](extensions.md) podřízený element k určení vlastního metadata, která se mají publikovat společně se standardními zjistitelnými metadaty (EPR, ContractTypeName, Binding, Scope a ListenURI).</span><span class="sxs-lookup"><span data-stu-id="02f55-134">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="02f55-135">Tento prvek konfigurace je závislý na [ \<prvku serviceDiscovery >](servicediscovery.md) , který poskytuje kontrolu úrovně služeb pro zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="02f55-135">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="02f55-136">To znamená, že nastavení tohoto prvku budou ignorována, pokud [ \<serviceDiscovery >](servicediscovery.md) není v konfiguraci k dispozici.</span><span class="sxs-lookup"><span data-stu-id="02f55-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02f55-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="02f55-137">Example</span></span>  
 <span data-ttu-id="02f55-138">Následující příklad konfigurace určuje rozsahy filtrování a metadata rozšíření, která se mají publikovat pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02f55-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02f55-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02f55-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
