---
title: Konfigurace klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 141b7f7fc04f98f267ce520544fb89451beac7b6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463869"
---
# <a name="client-configuration"></a><span data-ttu-id="369a8-102">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="369a8-102">Client Configuration</span></span>
<span data-ttu-id="369a8-103">Pomocí konfigurace klienta WCF (Windows Communication Foundation) můžete určit adresu, vazbu, chování a smlouvu, vlastnosti "ABC" koncového bodu klienta, který klienti používají k připojení ke koncovým bodům služby.</span><span class="sxs-lookup"><span data-stu-id="369a8-103">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="369a8-104">Prvek [ \<klienta>](../../configure-apps/file-schema/wcf/client.md) má [ \<koncový bod>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) prvek, jehož atributy se používají ke konfiguraci řadičů domény koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="369a8-104">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="369a8-105">Tyto atributy jsou popsány v [části Konfigurace koncových bodů.](#configuring-endpoints)</span><span class="sxs-lookup"><span data-stu-id="369a8-105">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="369a8-106">[ \<Koncový bod>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) prvek také obsahuje [ \<prvek>metadata,](../../configure-apps/file-schema/wcf/metadata.md) který se používá k určení nastavení pro import a export metadat, [ \<záhlaví>](../../configure-apps/file-schema/wcf/headers.md) prvek, který obsahuje kolekci vlastních adresních hlaviček, a prvek>[ \<identity,](../../configure-apps/file-schema/wcf/identity.md) který umožňuje ověřování koncového bodu jinými koncovými body, které si s ním vyměňují zprávy.</span><span class="sxs-lookup"><span data-stu-id="369a8-106">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="369a8-107">[ \<Záhlaví>](../../configure-apps/file-schema/wcf/headers.md) a [ \<prvky>identity](../../configure-apps/file-schema/wcf/identity.md) jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsány v článku [Adresy.](../../wcf/feature-details/endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="369a8-107">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../wcf/feature-details/endpoint-addresses.md) article.</span></span> <span data-ttu-id="369a8-108">Odkazy na témata, která vysvětlují použití rozšíření metadat, jsou uvedeny v části [Konfigurace metadat.](#configuring-metadata)</span><span class="sxs-lookup"><span data-stu-id="369a8-108">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="369a8-109">Konfigurace koncových bodů</span><span class="sxs-lookup"><span data-stu-id="369a8-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="369a8-110">Konfigurace klienta je navržena tak, aby klientovi umožnila zadat jeden nebo více koncových bodů, z nichž každý má svůj vlastní název, adresu a smlouvu, přičemž každá odkazující [ \<na vazby>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) a [ \<chování>prvky](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) v konfiguraci klienta, které mají být použity ke konfiguraci tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="369a8-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="369a8-111">Konfigurační soubor klienta by měl mít název "App.config", protože se jedná o název, který očekává běh WCF.</span><span class="sxs-lookup"><span data-stu-id="369a8-111">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="369a8-112">Následující příklad ukazuje konfigurační soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="369a8-112">The following example shows a client configuration file.</span></span>  
  
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
  
 <span data-ttu-id="369a8-113">Volitelný `name` atribut jednoznačně identifikuje koncový bod pro danou smlouvu.</span><span class="sxs-lookup"><span data-stu-id="369a8-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="369a8-114">Používá se <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> určit, který koncový bod v konfiguraci klienta je cílována a musí být načten při vytvoření kanálu do služby.</span><span class="sxs-lookup"><span data-stu-id="369a8-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="369a8-115">Název konfigurace koncového bodu\*se zástupnými symboly " je k dispozici a označuje metodu, <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> která by měla načíst libovolnou konfiguraci koncového bodu v souboru, za předpokladu, že je k dispozici přesně jedna a jinak vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="369a8-115">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="369a8-116">Pokud je tento atribut vynechán, odpovídající koncový bod se používá jako výchozí koncový bod přidružený k zadanému typu smlouvy.</span><span class="sxs-lookup"><span data-stu-id="369a8-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="369a8-117">Výchozí hodnota atributu `name` je prázdný řetězec, který odpovídá jako jakýkoli jiný název.</span><span class="sxs-lookup"><span data-stu-id="369a8-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="369a8-118">Každý koncový bod musí mít přidruženou adresu, aby bylo možné koncový bod vyhledat a identifikovat.</span><span class="sxs-lookup"><span data-stu-id="369a8-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="369a8-119">Atribut `address` lze zadat adresu URL, která poskytuje umístění koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="369a8-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="369a8-120">Ale adresu pro koncový bod služby lze také zadat v kódu vytvořením identifikátoru <xref:System.ServiceModel.ServiceHost> uniformní <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> prostředky (URI) a je přidán do pomocí jedné z metod.</span><span class="sxs-lookup"><span data-stu-id="369a8-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="369a8-121">Další informace naleznete [v tématu Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="369a8-121">For more information, see [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="369a8-122">Jak naznačuje úvod, [ \<záhlaví>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a <xref:System.ServiceModel.EndpointAddress> [ \<prvky>identity](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) jsou součástí a jsou také popsány v tématu [Adresy.](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="369a8-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="369a8-123">Atribut `binding` označuje typ vazby, kterou koncový bod očekává při připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="369a8-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="369a8-124">Typ musí mít registrovaný konfigurační oddíl, pokud má být odkazován.</span><span class="sxs-lookup"><span data-stu-id="369a8-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="369a8-125">V předchozím příkladu se jedná o <xref:System.ServiceModel.WSHttpBinding> [ \<oddíl wsHttpBinding>,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) který označuje, že koncový bod používá .</span><span class="sxs-lookup"><span data-stu-id="369a8-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="369a8-126">Ale může existovat více než jednu vazbu daného typu, který může koncový bod použít.</span><span class="sxs-lookup"><span data-stu-id="369a8-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="369a8-127">Každý z nich má vlastní [ \<vazby>](../../configure-apps/file-schema/wcf/bindings.md) prvek v rámci elementu typu (vazba).</span><span class="sxs-lookup"><span data-stu-id="369a8-127">Each of these has its own [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element within the (binding) type element.</span></span> <span data-ttu-id="369a8-128">Atribut `bindingconfiguration` se používá k rozlišení mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="369a8-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="369a8-129">Jeho hodnota je porovnána s atributem `name` [ \<prvku vazby>.](../../configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="369a8-129">Its value is matched with the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span> <span data-ttu-id="369a8-130">Další informace o konfiguraci vazby klienta pomocí konfigurace naleznete v [tématu How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="369a8-130">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="369a8-131">Atribut `behaviorConfiguration` se používá k určení [ \<chování,](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) které chování [ \<>koncového boduBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) koncový bod by měl použít.</span><span class="sxs-lookup"><span data-stu-id="369a8-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="369a8-132">Jeho hodnota je porovnána s atributem `name` [ \<prvku>chování.](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="369a8-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="369a8-133">Příklad použití konfigurace k určení chování klienta naleznete v [tématu Konfigurace chování klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="369a8-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="369a8-134">Atribut `contract` určuje, který kontrakt koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="369a8-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="369a8-135">Tato hodnota se <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> mapuje na <xref:System.ServiceModel.ServiceContractAttribute>rozhraní .</span><span class="sxs-lookup"><span data-stu-id="369a8-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="369a8-136">Výchozí hodnota je úplný název typu třídy, která implementuje službu.</span><span class="sxs-lookup"><span data-stu-id="369a8-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="369a8-137">Konfigurace metadat</span><span class="sxs-lookup"><span data-stu-id="369a8-137">Configuring Metadata</span></span>  
 <span data-ttu-id="369a8-138">Prvek [ \<>metadat](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) se používá k určení nastavení používaných k registraci rozšíření importu metadat.</span><span class="sxs-lookup"><span data-stu-id="369a8-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="369a8-139">Další informace o rozšíření systému metadat naleznete v [tématu Rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="369a8-139">For more information about extending the metadata system, see [Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369a8-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="369a8-140">See also</span></span>

- [<span data-ttu-id="369a8-141">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="369a8-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="369a8-142">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="369a8-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
