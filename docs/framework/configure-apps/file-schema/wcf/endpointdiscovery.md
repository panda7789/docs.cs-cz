---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 125baba917a49135aaa426df2cfa1a4dbe8ac1e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119493"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="88540-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="88540-101">\<endpointDiscovery></span></span>
<span data-ttu-id="88540-102">Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.</span><span class="sxs-lookup"><span data-stu-id="88540-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="88540-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="88540-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="88540-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="88540-104">\<behaviors></span></span>  
<span data-ttu-id="88540-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="88540-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="88540-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="88540-106">\<behavior></span></span>  
<span data-ttu-id="88540-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="88540-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88540-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88540-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88540-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="88540-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88540-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="88540-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88540-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="88540-111">Attributes</span></span>  
  
|<span data-ttu-id="88540-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="88540-112">Attribute</span></span>|<span data-ttu-id="88540-113">Popis</span><span class="sxs-lookup"><span data-stu-id="88540-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88540-114">Povoleno</span><span class="sxs-lookup"><span data-stu-id="88540-114">enabled</span></span>|<span data-ttu-id="88540-115">Logická hodnota určující, zda je na tomto koncovém bodu povolena rozpoznatelnost.</span><span class="sxs-lookup"><span data-stu-id="88540-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="88540-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="88540-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88540-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="88540-117">Child Elements</span></span>  
  
|<span data-ttu-id="88540-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="88540-118">Element</span></span>|<span data-ttu-id="88540-119">Popis</span><span class="sxs-lookup"><span data-stu-id="88540-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88540-120">\<scopes></span><span class="sxs-lookup"><span data-stu-id="88540-120">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="88540-121">Kolekce oboru identifikátory URI pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="88540-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="88540-122">Více než jednoho oboru identifikátory URI lze přidružit jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="88540-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="88540-123">[\<Rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [z \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="88540-123">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="88540-124">Kolekce elementů XML, který vám umožní určit vlastních metadat pro publikování pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="88540-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="88540-125">\<typy ></span><span class="sxs-lookup"><span data-stu-id="88540-125">\<types></span></span>|<span data-ttu-id="88540-126">Kolekce rozhraní pro hledání.</span><span class="sxs-lookup"><span data-stu-id="88540-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88540-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="88540-127">Parent Elements</span></span>  
  
|<span data-ttu-id="88540-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="88540-128">Element</span></span>|<span data-ttu-id="88540-129">Popis</span><span class="sxs-lookup"><span data-stu-id="88540-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88540-130">\<behavior></span><span class="sxs-lookup"><span data-stu-id="88540-130">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="88540-131">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="88540-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="88540-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88540-132">Remarks</span></span>  
 <span data-ttu-id="88540-133">Když se přidá do konfigurace chování koncového bodu a s `enabled` atribut nastaven na `true`, tento prvek konfigurace umožňuje jeho rozpoznatelnost.</span><span class="sxs-lookup"><span data-stu-id="88540-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="88540-134">Kromě toho můžete použít [ \<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)podřízený prvek pro zadání vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu, stejně jako [ \<rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) podřízený prvek k určení vlastní metadata, která by se měly zveřejňovat spolu s standardní zjistitelné metadata (EPR, ContractTypeName, BindingName, oboru a ListenURI).</span><span class="sxs-lookup"><span data-stu-id="88540-134">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="88540-135">Tento prvek konfigurace je závislá na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element, který poskytuje řízení úrovně služeb z možnosti rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="88540-135">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="88540-136">To znamená, že tento element nastavení jsou ignorovány, pokud [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) není k dispozici v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="88540-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88540-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="88540-137">Example</span></span>  
 <span data-ttu-id="88540-138">Následující příklad konfigurace určuje filtrování obory a metadata rozšíření pro publikování pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="88540-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88540-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88540-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
