---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6cca48cec486cfdbb9bca2eba48847c25c35abe9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="5e6a1-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="5e6a1-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="5e6a1-103">Určuje různé zjišťování nastavení pro koncový bod, například jeho možnosti rozpoznání, obory a vlastní rozšíření jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="5e6a1-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e6a1-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-105">\<behaviors></span></span>  
<span data-ttu-id="5e6a1-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5e6a1-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-107">\<behavior></span></span>  
<span data-ttu-id="5e6a1-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e6a1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e6a1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e6a1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e6a1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e6a1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e6a1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e6a1-112">Attributes</span></span>  
  
|<span data-ttu-id="5e6a1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5e6a1-113">Attribute</span></span>|<span data-ttu-id="5e6a1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5e6a1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e6a1-115">povoleno</span><span class="sxs-lookup"><span data-stu-id="5e6a1-115">enabled</span></span>|<span data-ttu-id="5e6a1-116">Logická hodnota, který určuje, jestli je povolené možnosti rozpoznání na tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-116">A Boolean value that that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="5e6a1-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e6a1-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5e6a1-118">Child Elements</span></span>  
  
|<span data-ttu-id="5e6a1-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e6a1-119">Element</span></span>|<span data-ttu-id="5e6a1-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5e6a1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e6a1-121">\<obory ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="5e6a1-122">Kolekce oboru identifikátory URI pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="5e6a1-123">Více než jednoho oboru identifikátory URI lze přidružit jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="5e6a1-124">[\<Rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [z \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="5e6a1-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="5e6a1-125">Kolekce elementů XML, která umožňuje zadat vlastní metadata publikována pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="5e6a1-126">\<typy ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-126">\<types></span></span>|<span data-ttu-id="5e6a1-127">Kolekce rozhraní pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e6a1-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5e6a1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5e6a1-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e6a1-129">Element</span></span>|<span data-ttu-id="5e6a1-130">Popis</span><span class="sxs-lookup"><span data-stu-id="5e6a1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e6a1-131">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5e6a1-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5e6a1-132">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="5e6a1-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e6a1-133">Remarks</span></span>  
 <span data-ttu-id="5e6a1-134">Při přidání do konfigurace chování pro koncový bod a s `enabled` atribut nastaven na `true`, tento element konfigurace umožňuje jeho možnosti rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="5e6a1-135">Kromě toho můžete použít [ \<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)podřízený element pro zadání vlastní rozsah identifikátory URI, které mohou být použity k filtrování koncové body služby během dotazu, a taky [ \<rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) podřízený element k určení vlastních metadat, která by měla být publikována spolu s metadaty standardní zjistitelný (EPR, ContractTypeName, BindingName, oboru a adrese ListenURI).</span><span class="sxs-lookup"><span data-stu-id="5e6a1-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="5e6a1-136">Tento element konfigurace je závislá na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element, který poskytuje možnosti rozpoznání úrovně řízení služby.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="5e6a1-137">To znamená, že tento element nastavení ignorují Pokud [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) se nenachází v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e6a1-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e6a1-138">Example</span></span>  
 <span data-ttu-id="5e6a1-139">Následující příklad konfigurace určuje filtrování obory a rozšíření metadata publikována pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5e6a1-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="5e6a1-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e6a1-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
