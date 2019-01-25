---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 4611d529c1854ee456585ad3f7aac339ff771bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556441"
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="28e7c-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="28e7c-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="28e7c-103">Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.</span><span class="sxs-lookup"><span data-stu-id="28e7c-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="28e7c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28e7c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28e7c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="28e7c-105">\<behaviors></span></span>  
<span data-ttu-id="28e7c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="28e7c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="28e7c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="28e7c-107">\<behavior></span></span>  
<span data-ttu-id="28e7c-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="28e7c-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e7c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28e7c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28e7c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28e7c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="28e7c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28e7c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28e7c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="28e7c-112">Attributes</span></span>  
  
|<span data-ttu-id="28e7c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="28e7c-113">Attribute</span></span>|<span data-ttu-id="28e7c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="28e7c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28e7c-115">Povoleno</span><span class="sxs-lookup"><span data-stu-id="28e7c-115">enabled</span></span>|<span data-ttu-id="28e7c-116">Logická hodnota určující, zda je na tomto koncovém bodu povolena rozpoznatelnost.</span><span class="sxs-lookup"><span data-stu-id="28e7c-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="28e7c-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="28e7c-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28e7c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="28e7c-118">Child Elements</span></span>  
  
|<span data-ttu-id="28e7c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="28e7c-119">Element</span></span>|<span data-ttu-id="28e7c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="28e7c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28e7c-121">\<scopes></span><span class="sxs-lookup"><span data-stu-id="28e7c-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="28e7c-122">Kolekce oboru identifikátory URI pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="28e7c-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="28e7c-123">Více než jednoho oboru identifikátory URI lze přidružit jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="28e7c-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="28e7c-124">[\<Rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [z \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="28e7c-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="28e7c-125">Kolekce elementů XML, který vám umožní určit vlastních metadat pro publikování pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="28e7c-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="28e7c-126">\<typy ></span><span class="sxs-lookup"><span data-stu-id="28e7c-126">\<types></span></span>|<span data-ttu-id="28e7c-127">Kolekce rozhraní pro hledání.</span><span class="sxs-lookup"><span data-stu-id="28e7c-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28e7c-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="28e7c-128">Parent Elements</span></span>  
  
|<span data-ttu-id="28e7c-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="28e7c-129">Element</span></span>|<span data-ttu-id="28e7c-130">Popis</span><span class="sxs-lookup"><span data-stu-id="28e7c-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28e7c-131">\<behavior></span><span class="sxs-lookup"><span data-stu-id="28e7c-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="28e7c-132">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="28e7c-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="28e7c-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28e7c-133">Remarks</span></span>  
 <span data-ttu-id="28e7c-134">Když se přidá do konfigurace chování koncového bodu a s `enabled` atribut nastaven na `true`, tento prvek konfigurace umožňuje jeho rozpoznatelnost.</span><span class="sxs-lookup"><span data-stu-id="28e7c-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="28e7c-135">Kromě toho můžete použít [ \<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)podřízený prvek pro zadání vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu, stejně jako [ \<rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) podřízený prvek k určení vlastní metadata, která by se měly zveřejňovat spolu s standardní zjistitelné metadata (EPR, ContractTypeName, BindingName, oboru a ListenURI).</span><span class="sxs-lookup"><span data-stu-id="28e7c-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="28e7c-136">Tento prvek konfigurace je závislá na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element, který poskytuje řízení úrovně služeb z možnosti rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="28e7c-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="28e7c-137">To znamená, že tento element nastavení jsou ignorovány, pokud [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) není k dispozici v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="28e7c-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28e7c-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="28e7c-138">Example</span></span>  
 <span data-ttu-id="28e7c-139">Následující příklad konfigurace určuje filtrování obory a metadata rozšíření pro publikování pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="28e7c-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28e7c-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28e7c-140">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
