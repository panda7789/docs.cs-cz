---
title: Konfigurace klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: b9975c6caeedc94bf4a7773e71a95eb0d8c7aed2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144687"
---
# <a name="client-configuration"></a><span data-ttu-id="b2ded-102">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="b2ded-102">Client Configuration</span></span>
<span data-ttu-id="b2ded-103">Konfigurace klienta Windows Communication Foundation (WCF) můžete použít k určení adresy, vazby, chování a kontrakt, vlastnosti "ABC" koncový bod klienta, který klienti používají k připojení ke koncovým bodům služby.</span><span class="sxs-lookup"><span data-stu-id="b2ded-103">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="b2ded-104">[ \<Klienta >](../../configure-apps/file-schema/wcf/client.md) element má [ \<koncový bod >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu, jejichž atributy se používají ke konfiguraci koncového bodu základních informací.</span><span class="sxs-lookup"><span data-stu-id="b2ded-104">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="b2ded-105">Tyto atributy jsou popsány v [konfigurace koncových bodů](#configuring-endpoints) oddílu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-105">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="b2ded-106">[ \<Koncový bod >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) také obsahuje element [ \<metadat >](../../configure-apps/file-schema/wcf/metadata.md) element, který se používá k určení nastavení pro import a Export metadat, [ \<záhlaví >](../../configure-apps/file-schema/wcf/headers.md) element, který obsahuje kolekce záhlaví adres vlastní, a [ \<identity >](../../configure-apps/file-schema/wcf/identity.md) element, který umožňuje ověřování z koncového bodu jiné koncové body Výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="b2ded-106">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="b2ded-107">[ \<Záhlaví >](../../configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../configure-apps/file-schema/wcf/identity.md) prvky jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsány v [adresy](../../wcf/feature-details/endpoint-addresses.md) článku.</span><span class="sxs-lookup"><span data-stu-id="b2ded-107">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../wcf/feature-details/endpoint-addresses.md) article.</span></span> <span data-ttu-id="b2ded-108">Odkazy na témata, která popisují použití metadata rozšíření jsou k dispozici v [konfigurace metadat](#configuring-metadata) oddílu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-108">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="b2ded-109">Konfigurace koncových bodů</span><span class="sxs-lookup"><span data-stu-id="b2ded-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="b2ded-110">Konfigurace klienta je navržena k umožnění klienta určit jeden nebo další koncové body, každý s vlastními názvy adres a smlouvy se každá odkazující na [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) a [ \< chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) prvky v konfiguraci klienta, který se má použít ke konfiguraci tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="b2ded-111">Konfigurační soubor klienta by měl s názvem "App.config", protože jde o název, který očekává, že modul runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="b2ded-111">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="b2ded-112">Následující příklad ukazuje klienta konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="b2ded-112">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b2ded-113">Volitelný `name` atribut jednoznačně identifikuje koncový bod pro daný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="b2ded-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="b2ded-114">Používá se <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> , nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> k určení, který koncový bod v konfiguraci klienta je cílem a musí být načten, když se vytvoří kanál ke službě.</span><span class="sxs-lookup"><span data-stu-id="b2ded-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="b2ded-115">Zástupný název konfigurace koncového bodu "\*" je k dispozici a pozná, <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> , že ho předpokladu, že existuje přesně jeden k dispozici a jinak by se měly načíst všechny konfigurace koncového bodu v souboru, metoda vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="b2ded-115">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="b2ded-116">Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod přidružený k typu zadaného kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="b2ded-117">Výchozí hodnota `name` atribut je prázdný řetězec, což je nalezena shoda s jako jakýkoli jiný název.</span><span class="sxs-lookup"><span data-stu-id="b2ded-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="b2ded-118">Každý koncový bod musí mít adresu přidruženo k vyhledání a identifikaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="b2ded-119">`address` Atribut lze použít k určení adresy URL, která poskytuje umístění koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="b2ded-120">Ale adresu koncového bodu služby můžete také zadat v kódu tak, že vytvoříte identifikátor URI (Uniform Resource) a je přidán <xref:System.ServiceModel.ServiceHost> pomocí jedné z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b2ded-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="b2ded-121">Další informace najdete v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="b2ded-121">For more information, see [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="b2ded-122">Protože po zavedení naznačuje, [ \<záhlaví >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) prvky jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou také popsány v [ Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="b2ded-123">`binding` Atribut určuje typ vazby koncového bodu očekává, že mají používat při připojování ke službě.</span><span class="sxs-lookup"><span data-stu-id="b2ded-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="b2ded-124">Typ musí mít registrované konfigurační oddíl, pokud má odkazovat.</span><span class="sxs-lookup"><span data-stu-id="b2ded-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="b2ded-125">V předchozím příkladu je to [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) části, která označuje, že koncový bod používá <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b2ded-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="b2ded-126">Nicméně mohou existovat více než jednu vazbu daného typu, který můžete použít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b2ded-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="b2ded-127">Každý z nich má vlastní [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu v typu elementu (vazby).</span><span class="sxs-lookup"><span data-stu-id="b2ded-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="b2ded-128">`bindingconfiguration` Atribut se používá k rozlišení mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="b2ded-129">Její hodnota je nalezena shoda s `name` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> <span data-ttu-id="b2ded-130">Další informace o tom, jak nakonfigurovat klienta vazby pomocí konfigurace, najdete v článku [jak: Zadání klientské vazby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b2ded-130">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="b2ded-131">`behaviorConfiguration` Atribut se používá k určení [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) koncový bod by měl používat.</span><span class="sxs-lookup"><span data-stu-id="b2ded-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="b2ded-132">Její hodnota je nalezena shoda s `name` atribut [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b2ded-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="b2ded-133">Příklad použití konfigurace k určení chování klienta najdete v tématu [konfigurace chování klientů](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="b2ded-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="b2ded-134">`contract` Atribut určuje kontrakt, který vystavuje koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b2ded-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="b2ded-135">Tato hodnota se mapuje <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> z <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b2ded-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="b2ded-136">Výchozí hodnota je název úplný typ třídy, která implementuje služby.</span><span class="sxs-lookup"><span data-stu-id="b2ded-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="b2ded-137">Konfigurace metadat</span><span class="sxs-lookup"><span data-stu-id="b2ded-137">Configuring Metadata</span></span>  
 <span data-ttu-id="b2ded-138">[ \<Metadat >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element slouží k určení nastavení použije k registraci metadat import rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b2ded-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="b2ded-139">Další informace o rozšíření systému metadat najdete v tématu [rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="b2ded-139">For more information about extending the metadata system, see [Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ded-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2ded-140">See also</span></span>

- [<span data-ttu-id="b2ded-141">Koncové body: Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="b2ded-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="b2ded-142">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="b2ded-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
