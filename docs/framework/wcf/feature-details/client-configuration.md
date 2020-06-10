---
title: Konfigurace klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 2d17438095e65ccf922061c03e406bab35b07c5d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593656"
---
# <a name="client-configuration"></a><span data-ttu-id="3e36f-102">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="3e36f-102">Client Configuration</span></span>
<span data-ttu-id="3e36f-103">Můžete použít konfiguraci klienta Windows Communication Foundation (WCF) k určení adresy, vazby, chování a kontraktu, vlastností "ABC" koncového bodu klienta, které klienti používají pro připojení ke koncovým bodům služby.</span><span class="sxs-lookup"><span data-stu-id="3e36f-103">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="3e36f-104">[\<client>](../../configure-apps/file-schema/wcf/client.md)Element má [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, jehož atributy se používají ke konfiguraci koncového bodu ABCs.</span><span class="sxs-lookup"><span data-stu-id="3e36f-104">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="3e36f-105">Tyto atributy jsou popsány v části [Konfigurace koncových bodů](#configuring-endpoints) .</span><span class="sxs-lookup"><span data-stu-id="3e36f-105">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="3e36f-106">[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)Element také obsahuje [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element, který se používá k určení nastavení pro import a export metadat, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) elementu, který obsahuje kolekci vlastních hlaviček adres, a [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elementu, který umožňuje ověřování koncového bodu jinými koncovými body výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e36f-106">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="3e36f-107">[\<headers>](../../configure-apps/file-schema/wcf/headers.md)Prvky a [\<identity>](../../configure-apps/file-schema/wcf/identity.md) jsou uvedeny <xref:System.ServiceModel.EndpointAddress> v části a jsou popsány v článku [adresy](endpoint-addresses.md) .</span><span class="sxs-lookup"><span data-stu-id="3e36f-107">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](endpoint-addresses.md) article.</span></span> <span data-ttu-id="3e36f-108">Odkazy na témata, která vysvětlují použití rozšíření metadat, jsou k dispozici v části [Konfigurace metadat](#configuring-metadata) .</span><span class="sxs-lookup"><span data-stu-id="3e36f-108">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="3e36f-109">Konfigurace koncových bodů</span><span class="sxs-lookup"><span data-stu-id="3e36f-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="3e36f-110">Konfigurace klienta je navržena tak, aby umožňovala klientovi určit jeden nebo více koncových bodů, každý s vlastním názvem, adresou a kontraktem, přičemž každý odkazuje na [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) prvky a v konfiguraci klienta, které se mají použít ke konfiguraci tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3e36f-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="3e36f-111">Konfigurační soubor klienta by měl mít název app. config, protože se jedná o název, který modul runtime WCF očekává.</span><span class="sxs-lookup"><span data-stu-id="3e36f-111">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="3e36f-112">Následující příklad ukazuje konfigurační soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="3e36f-112">The following example shows a client configuration file.</span></span>  
  
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
            <!-- Add another endpoint by adding another <endpoint> element. -->
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
          <!-- Configure this binding here. -->  
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
  
 <span data-ttu-id="3e36f-113">Volitelný `name` atribut jednoznačně identifikuje koncový bod pro daný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3e36f-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="3e36f-114">Používá je <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> k určení, který koncový bod v konfiguraci klienta je cílen a který musí být načten při vytvoření kanálu ke službě.</span><span class="sxs-lookup"><span data-stu-id="3e36f-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="3e36f-115">Zástupný znak konfigurace koncového bodu \* je k dispozici a označuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> metodu, kterou by měl načíst jakoukoli konfiguraci koncového bodu v souboru, pokud je k dispozici přesně jeden dostupný a jinak vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e36f-115">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="3e36f-116">Pokud je tento atribut vynechán, použije se jako výchozí koncový bod přidružený k zadanému typu kontraktu odpovídající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3e36f-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="3e36f-117">Výchozí hodnota `name` atributu je prázdný řetězec, který se shoduje s jiným názvem.</span><span class="sxs-lookup"><span data-stu-id="3e36f-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="3e36f-118">Každý koncový bod musí mít přidruženou adresu pro vyhledání a identifikaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3e36f-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="3e36f-119">`address`Atribut lze použít k zadání adresy URL, která poskytuje umístění koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3e36f-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="3e36f-120">Adresa koncového bodu služby se ale dá zadat i v kódu tak, že se vytvoří identifikátor URI (Uniform Resource Identifier) a přidá se k němu <xref:System.ServiceModel.ServiceHost> pomocí jedné z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="3e36f-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="3e36f-121">Další informace najdete v tématu [adresy](endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="3e36f-121">For more information, see [Addresses](endpoint-addresses.md).</span></span> <span data-ttu-id="3e36f-122">Jak je uvedeno v úvodu [\<headers>](../../configure-apps/file-schema/wcf/headers.md) , [\<identity>](../../configure-apps/file-schema/wcf/identity.md) jsou prvky a součástí <xref:System.ServiceModel.EndpointAddress> a jsou také popsány v tématu [adresy](endpoint-addresses.md) .</span><span class="sxs-lookup"><span data-stu-id="3e36f-122">As the introduction indicates, the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="3e36f-123">`binding`Atribut určuje typ vazby, který koncový bod očekává, že se má použít při připojování ke službě.</span><span class="sxs-lookup"><span data-stu-id="3e36f-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="3e36f-124">Typ musí mít registrovaný konfigurační oddíl, pokud na něj odkazuje.</span><span class="sxs-lookup"><span data-stu-id="3e36f-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="3e36f-125">V předchozím příkladu je to [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) oddíl, který indikuje, že koncový bod používá <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="3e36f-125">In the previous example, this is the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="3e36f-126">Může ale existovat více než jedna vazba daného typu, který může koncový bod použít.</span><span class="sxs-lookup"><span data-stu-id="3e36f-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="3e36f-127">Každá z nich má svůj vlastní [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) prvek v rámci elementu typu (Binding).</span><span class="sxs-lookup"><span data-stu-id="3e36f-127">Each of these has its own [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element within the (binding) type element.</span></span> <span data-ttu-id="3e36f-128">`bindingconfiguration`Atribut slouží k rozlišení mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="3e36f-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="3e36f-129">Jeho hodnota je porovnána s `name` atributem [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="3e36f-129">Its value is matched with the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span> <span data-ttu-id="3e36f-130">Další informace o tom, jak nakonfigurovat vazbu klienta pomocí konfigurace, najdete v tématu [Postupy: určení vazby klienta v konfiguraci](../how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="3e36f-130">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="3e36f-131">`behaviorConfiguration`Atribut slouží k určení, který [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) koncový bod má použít.</span><span class="sxs-lookup"><span data-stu-id="3e36f-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="3e36f-132">Jeho hodnota je porovnána s `name` atributem [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="3e36f-132">Its value is matched with the `name` attribute of the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="3e36f-133">Příklad použití konfigurace k určení chování klienta najdete v tématu [Konfigurace chování klienta](../configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="3e36f-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="3e36f-134">`contract`Atribut určuje, ve kterém kontraktu se koncový bod zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="3e36f-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="3e36f-135">Tato hodnota je mapována na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3e36f-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="3e36f-136">Výchozí hodnota je úplný název typu třídy, která implementuje službu.</span><span class="sxs-lookup"><span data-stu-id="3e36f-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="3e36f-137">Konfigurace metadat</span><span class="sxs-lookup"><span data-stu-id="3e36f-137">Configuring Metadata</span></span>  
 <span data-ttu-id="3e36f-138">[\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)Element se používá k určení nastavení, která se používají k registraci rozšíření pro import metadat.</span><span class="sxs-lookup"><span data-stu-id="3e36f-138">The [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="3e36f-139">Další informace o rozšíření systému metadat naleznete v tématu [rozšíření systému metadat](../extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="3e36f-139">For more information about extending the metadata system, see [Extending the Metadata System](../extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e36f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e36f-140">See also</span></span>

- [<span data-ttu-id="3e36f-141">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="3e36f-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="3e36f-142">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="3e36f-142">Configuring Client Behaviors</span></span>](../configuring-client-behaviors.md)
