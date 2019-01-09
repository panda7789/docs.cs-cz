---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 58bab9aef2e20d762c303e8b698214125531a136
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150913"
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="3fe6a-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="3fe6a-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="3fe6a-103">Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="3fe6a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3fe6a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3fe6a-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3fe6a-105">\<behaviors></span></span>  
<span data-ttu-id="3fe6a-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3fe6a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="3fe6a-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3fe6a-107">\<behavior></span></span>  
<span data-ttu-id="3fe6a-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="3fe6a-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe6a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fe6a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fe6a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3fe6a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3fe6a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fe6a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3fe6a-112">Attributes</span></span>  
  
|<span data-ttu-id="3fe6a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3fe6a-113">Attribute</span></span>|<span data-ttu-id="3fe6a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3fe6a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3fe6a-115">Povoleno</span><span class="sxs-lookup"><span data-stu-id="3fe6a-115">enabled</span></span>|<span data-ttu-id="3fe6a-116">Logická hodnota určující, zda je na tomto koncovém bodu povolena rozpoznatelnost.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="3fe6a-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3fe6a-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3fe6a-118">Child Elements</span></span>  
  
|<span data-ttu-id="3fe6a-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="3fe6a-119">Element</span></span>|<span data-ttu-id="3fe6a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="3fe6a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fe6a-121">\<obory ></span><span class="sxs-lookup"><span data-stu-id="3fe6a-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="3fe6a-122">Kolekce oboru identifikátory URI pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="3fe6a-123">Více než jednoho oboru identifikátory URI lze přidružit jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="3fe6a-124">[\<Rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [z \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="3fe6a-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="3fe6a-125">Kolekce elementů XML, který vám umožní určit vlastních metadat pro publikování pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="3fe6a-126">\<typy ></span><span class="sxs-lookup"><span data-stu-id="3fe6a-126">\<types></span></span>|<span data-ttu-id="3fe6a-127">Kolekce rozhraní pro hledání.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3fe6a-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3fe6a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3fe6a-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="3fe6a-129">Element</span></span>|<span data-ttu-id="3fe6a-130">Popis</span><span class="sxs-lookup"><span data-stu-id="3fe6a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fe6a-131">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3fe6a-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3fe6a-132">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="3fe6a-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fe6a-133">Remarks</span></span>  
 <span data-ttu-id="3fe6a-134">Když se přidá do konfigurace chování koncového bodu a s `enabled` atribut nastaven na `true`, tento prvek konfigurace umožňuje jeho rozpoznatelnost.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="3fe6a-135">Kromě toho můžete použít [ \<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)podřízený prvek pro zadání vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu, stejně jako [ \<rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) podřízený prvek k určení vlastní metadata, která by se měly zveřejňovat spolu s standardní zjistitelné metadata (EPR, ContractTypeName, BindingName, oboru a ListenURI).</span><span class="sxs-lookup"><span data-stu-id="3fe6a-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="3fe6a-136">Tento prvek konfigurace je závislá na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element, který poskytuje řízení úrovně služeb z možnosti rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="3fe6a-137">To znamená, že tento element nastavení jsou ignorovány, pokud [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) není k dispozici v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fe6a-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fe6a-138">Example</span></span>  
 <span data-ttu-id="3fe6a-139">Následující příklad konfigurace určuje filtrování obory a metadata rozšíření pro publikování pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3fe6a-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3fe6a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fe6a-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
