---
title: Konfigurace klienta
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c2c0d17c7274cc9fdaf1b5080950ddb4f69f539a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="client-configuration"></a><span data-ttu-id="57334-102">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="57334-102">Client Configuration</span></span>
<span data-ttu-id="57334-103">Můžete použít [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] konfigurace klienta a zadejte adresy, vazby chování, smlouvy, "ABC" vlastnosti klienta koncového bodu, který používají klienti k připojení ke koncovým bodům služby.</span><span class="sxs-lookup"><span data-stu-id="57334-103">You can use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="57334-104">[ \<Klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element má [ \<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element, jehož atributy se používají ke konfiguraci koncového bodu základních informací.</span><span class="sxs-lookup"><span data-stu-id="57334-104">The [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="57334-105">Tyto atributy jsou popsané v části "Konfigurace koncových bodů" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="57334-105">These attributes are discussed in the "Configuring Endpoints" section of this topic.</span></span>  
  
 <span data-ttu-id="57334-106">[ \<Koncový bod >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) také obsahuje element [ \<metadata >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element, který slouží k určení nastavení pro import a Export metadat, [ \<hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element, který obsahuje kolekci hlaviček vlastní adresu, a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element, který umožňuje ověření koncový bod pomocí dalších koncových bodů Výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="57334-106">The [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element also contains a [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata , a [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="57334-107">[ \<Hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsané v [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="57334-107">The [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span> <span data-ttu-id="57334-108">Odkazy na témata, které vysvětlují použití rozšíření metadata jsou uvedeny v části dílčí konfigurace Metadata v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="57334-108">Links to topics that explain the use of metadata extensions are provided in the Configuring Metadata sub-section of this topic.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="57334-109">Konfigurace koncových bodů</span><span class="sxs-lookup"><span data-stu-id="57334-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="57334-110">Konfigurace klienta je navržena k umožnění klienta zadat jeden nebo více koncových bodů, každý s svůj vlastní název adres a smlouvy, s každou odkazující na [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) a [ \< chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementů v konfiguraci klienta, který se má použít ke konfiguraci tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="57334-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="57334-111">Konfigurační soubor klienta by měl mít název "App.config" vzhledem k tomu, že je to název, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] očekává modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="57334-111">The client configuration file should be named "App.config" because this is the name that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime expects.</span></span> <span data-ttu-id="57334-112">Následující příklad ukazuje konfigurační soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="57334-112">The following example shows a client configuration file.</span></span>  
  
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
  
 <span data-ttu-id="57334-113">Volitelné `name` atribut jednoznačně identifikuje koncový bod pro danou zakázku.</span><span class="sxs-lookup"><span data-stu-id="57334-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="57334-114">Je používán <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> , nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> k určení, které koncového bodu v konfiguraci klienta je cílem a musí být načteny, když kanál, který je vytvořen službě.</span><span class="sxs-lookup"><span data-stu-id="57334-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="57334-115">Název konfigurace koncového bodu zástupný znak "\*" je k dispozici a ukazuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> , ho předpokladu, že je přesně jeden k dispozici a jinak by se měly načíst všechny konfigurace koncového bodu v souboru, metoda vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="57334-115">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="57334-116">Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod přidruženou k zadané kontrakt typu.</span><span class="sxs-lookup"><span data-stu-id="57334-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="57334-117">Výchozí hodnota `name` atribut je řetězec prázdný, což je nalezena shoda s jako jiný název.</span><span class="sxs-lookup"><span data-stu-id="57334-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="57334-118">Každý koncový bod musí mít adresu přidruženo vyhledat a identifikovat koncový bod.</span><span class="sxs-lookup"><span data-stu-id="57334-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="57334-119">`address` Atributu lze zadat adresu URL, která poskytuje umístění koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="57334-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="57334-120">Ale adresu pro koncový bod služby můžete také zadat v kódu tak, že vytvoříte identifikátor URI (Uniform Resource) a přidají se do <xref:System.ServiceModel.ServiceHost> pomocí jedné z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="57334-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="57334-121">Další informace najdete v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="57334-121">For more information, see [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="57334-122">Jak uvádí, že zavedení, [ \<hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsány i v [ Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="57334-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="57334-123">`binding` Atribut určuje typ vazby koncového bodu očekává, že má použít při připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="57334-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="57334-124">Tento typ musí mít registrovaný konfigurační oddíl, pokud je na něj odkazovat.</span><span class="sxs-lookup"><span data-stu-id="57334-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="57334-125">V předchozím příkladu je to [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) část, která označuje, že používá koncový bod <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="57334-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="57334-126">Ale může být více než jednu vazbu daného typu, který můžete použít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="57334-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="57334-127">Každá z nich má svou vlastní [ \<vazby >](../../../../docs/framework/misc/binding.md) v rámci prvku typu (vazby).</span><span class="sxs-lookup"><span data-stu-id="57334-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="57334-128">`bindingconfiguration` Atribut slouží k rozlišení mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="57334-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="57334-129">Její hodnota je nalezena shoda s `name` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) element.</span><span class="sxs-lookup"><span data-stu-id="57334-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> <span data-ttu-id="57334-130">Další informace o tom, jak nakonfigurovat klienta vazby pomocí konfigurace, najdete v části [postupy: zadání klientské vazby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="57334-130">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="57334-131">`behaviorConfiguration` Atribut slouží k určení, které [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) by měl používat koncový bod.</span><span class="sxs-lookup"><span data-stu-id="57334-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="57334-132">Její hodnota je nalezena shoda s `name` atribut [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="57334-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="57334-133">Příklad použití konfigurace k určení chování klienta, naleznete v části [konfigurace chování klientů](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="57334-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="57334-134">`contract` Určuje atribut, který kontrakt koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="57334-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="57334-135">Tato hodnota se mapuje <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> z <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="57334-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="57334-136">Výchozí hodnota je název úplné typu třídy, která implementuje službu.</span><span class="sxs-lookup"><span data-stu-id="57334-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="57334-137">Konfigurace metadat</span><span class="sxs-lookup"><span data-stu-id="57334-137">Configuring Metadata</span></span>  
 <span data-ttu-id="57334-138">[ \<Metadata >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element se používá k určení nastavení použitá pro zaregistrování metadata importovat rozšíření.</span><span class="sxs-lookup"><span data-stu-id="57334-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="57334-139">Další informace o rozšíření systému metadat najdete v tématu[rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="57334-139">For more information about extending the metadata system, see[Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57334-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="57334-140">See Also</span></span>  
 [<span data-ttu-id="57334-141">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="57334-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="57334-142">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="57334-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
