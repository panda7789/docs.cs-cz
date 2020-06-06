---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398019"
---
# \<endpointDiscovery>
<span data-ttu-id="c2a4a-101">Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-101">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="c2a4a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2a4a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2a4a-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2a4a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c2a4a-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2a4a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2a4a-105">Attributes</span></span>  
  
|<span data-ttu-id="c2a4a-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2a4a-106">Attribute</span></span>|<span data-ttu-id="c2a4a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c2a4a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2a4a-108">enabled</span><span class="sxs-lookup"><span data-stu-id="c2a4a-108">enabled</span></span>|<span data-ttu-id="c2a4a-109">Logická hodnota, která určuje, zda je na tomto koncovém bodu povolena zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-109">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="c2a4a-110">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-110">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2a4a-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2a4a-111">Child Elements</span></span>  
  
|<span data-ttu-id="c2a4a-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2a4a-112">Element</span></span>|<span data-ttu-id="c2a4a-113">Description</span><span class="sxs-lookup"><span data-stu-id="c2a4a-113">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="c2a4a-114">Kolekce identifikátorů URI oboru pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-114">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="c2a4a-115">K jednomu koncovému bodu lze přidružit více než jeden identifikátor URI oboru.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-115">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="c2a4a-116">[\<extensions>](extensions.md)[z \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="c2a4a-116">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="c2a4a-117">Kolekce elementů XML, které umožňují zadat vlastní metadata, která budou publikována pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-117">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="c2a4a-118">Kolekce rozhraní, která se mají vyhledat</span><span class="sxs-lookup"><span data-stu-id="c2a4a-118">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2a4a-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2a4a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c2a4a-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2a4a-120">Element</span></span>|<span data-ttu-id="c2a4a-121">Description</span><span class="sxs-lookup"><span data-stu-id="c2a4a-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c2a4a-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-122">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="c2a4a-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2a4a-123">Remarks</span></span>  
 <span data-ttu-id="c2a4a-124">Po přidání do konfigurace chování koncového bodu a s `enabled` atributem nastaveným na `true` může tento prvek konfigurace povolit svou zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-124">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="c2a4a-125">Kromě toho můžete použít [\<scopes>](scopes.md) podřízený element k určení identifikátorů URI vlastního rozsahu, které lze použít k filtrování koncových bodů služby během dotazu a také [\<extensions>](extensions.md) podřízeného prvku pro určení vlastních metadat, která mají být publikována společně se standardními zjistitelnými metadaty (EPR, ContractTypeName, Binding, Scope a ListenUri).</span><span class="sxs-lookup"><span data-stu-id="c2a4a-125">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="c2a4a-126">Tento prvek konfigurace je závislý na [\<serviceDiscovery>](servicediscovery.md) prvku, který poskytuje kontrolu úrovně služeb pro zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-126">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="c2a4a-127">To znamená, že nastavení tohoto elementu budou ignorována, pokud [\<serviceDiscovery>](servicediscovery.md) není v konfiguraci k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-127">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2a4a-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2a4a-128">Example</span></span>  
 <span data-ttu-id="c2a4a-129">Následující příklad konfigurace určuje rozsahy filtrování a metadata rozšíření, která se mají publikovat pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c2a4a-129">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2a4a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2a4a-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
