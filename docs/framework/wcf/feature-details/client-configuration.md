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
ms.openlocfilehash: 19d1f7630c96f557791f0682fbc0c5d7286c7eb7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="client-configuration"></a>Konfigurace klienta
Můžete použít [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] konfigurace klienta a zadejte adresy, vazby chování, smlouvy, "ABC" vlastnosti klienta koncového bodu, který používají klienti k připojení ke koncovým bodům služby. [ \<Klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element má [ \<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element, jehož atributy se používají ke konfiguraci koncového bodu základních informací. Tyto atributy jsou popsané v části "Konfigurace koncových bodů" v tomto tématu.  
  
 [ \<Koncový bod >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) také obsahuje element [ \<metadata >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element, který slouží k určení nastavení pro import a Export metadat, [ \<hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element, který obsahuje kolekci hlaviček vlastní adresu, a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element, který umožňuje ověření koncový bod pomocí dalších koncových bodů Výměna zpráv s ním. [ \<Hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsané v [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tématu. Odkazy na témata, které vysvětlují použití rozšíření metadata jsou uvedeny v části dílčí konfigurace Metadata v tomto tématu.  
  
## <a name="configuring-endpoints"></a>Konfigurace koncových bodů  
 Konfigurace klienta je navržena k umožnění klienta zadat jeden nebo více koncových bodů, každý s svůj vlastní název adres a smlouvy, s každou odkazující na [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) a [ \< chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementů v konfiguraci klienta, který se má použít ke konfiguraci tohoto koncového bodu. Konfigurační soubor klienta by měl mít název "App.config" vzhledem k tomu, že je to název, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] očekává modulu runtime. Následující příklad ukazuje konfigurační soubor klienta.  
  
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
  
 Volitelné `name` atribut jednoznačně identifikuje koncový bod pro danou zakázku. Je používán <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> , nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> k určení, které koncového bodu v konfiguraci klienta je cílem a musí být načteny, když kanál, který je vytvořen službě. Název konfigurace koncového bodu zástupný znak "*" je k dispozici a ukazuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> , ho předpokladu, že je přesně jeden k dispozici a jinak by se měly načíst všechny konfigurace koncového bodu v souboru, metoda vyvolá výjimku. Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod přidruženou k zadané kontrakt typu. Výchozí hodnota `name` atribut je řetězec prázdný, což je nalezena shoda s jako jiný název.  
  
 Každý koncový bod musí mít adresu přidruženo vyhledat a identifikovat koncový bod. `address` Atributu lze zadat adresu URL, která poskytuje umístění koncového bodu. Ale adresu pro koncový bod služby můžete také zadat v kódu tak, že vytvoříte identifikátor URI (Uniform Resource) a přidají se do <xref:System.ServiceModel.ServiceHost> pomocí jedné z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Další informace najdete v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Jak uvádí, že zavedení, [ \<hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsány i v [ Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tématu.  
  
 `binding` Atribut určuje typ vazby koncového bodu očekává, že má použít při připojení ke službě. Tento typ musí mít registrovaný konfigurační oddíl, pokud je na něj odkazovat. V předchozím příkladu je to [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) část, která označuje, že používá koncový bod <xref:System.ServiceModel.WSHttpBinding>. Ale může být více než jednu vazbu daného typu, který můžete použít koncový bod. Každá z nich má svou vlastní [ \<vazby >](../../../../docs/framework/misc/binding.md) v rámci prvku typu (vazby). `bindingconfiguration` Atribut slouží k rozlišení mezi vazby stejného typu. Její hodnota je nalezena shoda s `name` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) element. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Postup konfigurace klienta vazby pomocí konfigurace, najdete v části [postupy: zadání klientské vazby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration` Atribut slouží k určení, které [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) by měl používat koncový bod. Její hodnota je nalezena shoda s `name` atribut [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element. Příklad použití konfigurace k určení chování klienta, naleznete v části [konfigurace chování klientů](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 `contract` Určuje atribut, který kontrakt koncový bod je vystavení. Tato hodnota se mapuje <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> z <xref:System.ServiceModel.ServiceContractAttribute>. Výchozí hodnota je název úplné typu třídy, která implementuje službu.  
  
### <a name="configuring-metadata"></a>Konfigurace metadat  
 [ \<Metadata >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element se používá k určení nastavení použitá pro zaregistrování metadata importovat rozšíření. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] rozšíření systému metadat, najdete v části[rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncové body: adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Konfigurace chování klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
