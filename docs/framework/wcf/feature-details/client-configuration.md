---
title: Konfigurace klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 6a5cbf5d536af8649b0b8bb93600e94a48c507c1
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141766"
---
# <a name="client-configuration"></a>Konfigurace klienta
Můžete použít konfiguraci klienta Windows Communication Foundation (WCF) k určení adresy, vazby, chování a kontraktu, vlastností "ABC" koncového bodu klienta, které klienti používají pro připojení ke koncovým bodům služby. [> Prvek\<klienta](../../configure-apps/file-schema/wcf/client.md) má [\<> element koncového bodu](../../configure-apps/file-schema/wcf/endpoint-of-client.md) , jehož atributy se používají ke konfiguraci koncového bodu ABCs. Tyto atributy jsou popsány v části [Konfigurace koncových bodů](#configuring-endpoints) .  
  
 [\<koncový bod >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element obsahuje také [\<metadat >](../../configure-apps/file-schema/wcf/metadata.md) element, který se používá k určení nastavení pro import a export metadat, [\<hlaviček](../../configure-apps/file-schema/wcf/headers.md) > element, který obsahuje kolekci vlastních hlaviček adres, a\<prvek [> identity](../../configure-apps/file-schema/wcf/identity.md) , který umožňuje ověřování koncového bodu jinými koncovými body výměny zpráv. [\<hlavičky >](../../configure-apps/file-schema/wcf/headers.md) a [\<prvky identity >](../../configure-apps/file-schema/wcf/identity.md) jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsány v článku [adresy](../../wcf/feature-details/endpoint-addresses.md) . Odkazy na témata, která vysvětlují použití rozšíření metadat, jsou k dispozici v části [Konfigurace metadat](#configuring-metadata) .  
  
## <a name="configuring-endpoints"></a>Konfigurace koncových bodů  
 Konfigurace klienta je navržena tak, aby umožňovala klientovi určit jeden nebo více koncových bodů, každý s vlastním názvem, adresou a kontraktem, přičemž každý odkaz na [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) a [\<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) prvcích v konfiguraci klienta, které se mají použít ke konfiguraci tohoto koncového bodu. Konfigurační soubor klienta by měl mít název app. config, protože se jedná o název, který modul runtime WCF očekává. Následující příklad ukazuje konfigurační soubor klienta.  
  
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
  
 Volitelný atribut `name` jednoznačně identifikuje koncový bod pro daný kontrakt. Používá je <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> k určení, který koncový bod v konfiguraci klienta je cílen a který musí být načten při vytvoření kanálu ke službě. Zástupný znak konfigurace koncového bodu "\*" je k dispozici a označuje se jako <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> metoda, kterou by měl v souboru načíst libovolnou konfiguraci koncového bodu, pokud je k dispozici přesně jeden dostupný a jinak vyvolá výjimku. Pokud je tento atribut vynechán, použije se jako výchozí koncový bod přidružený k zadanému typu kontraktu odpovídající koncový bod. Výchozí hodnota pro atribut `name` je prázdný řetězec, který se shoduje s jiným názvem.  
  
 Každý koncový bod musí mít přidruženou adresu pro vyhledání a identifikaci koncového bodu. Atribut `address` lze použít k zadání adresy URL, která poskytuje umístění koncového bodu. Adresa koncového bodu služby se ale taky dá zadat v kódu tak, že se vytvoří identifikátor URI (Uniform Resource Identifier) a přidá se do <xref:System.ServiceModel.ServiceHost> pomocí jedné z metod <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>. Další informace najdete v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Jak je uvedeno v úvodu, [\<hlaviček >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [\<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) prvky jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou také popsány v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) .  
  
 Atribut `binding` určuje typ vazby, který koncový bod očekává, že se má použít při připojování ke službě. Typ musí mít registrovaný konfigurační oddíl, pokud na něj odkazuje. V předchozím příkladu se jedná o oddíl [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) , který indikuje, že koncový bod používá <xref:System.ServiceModel.WSHttpBinding>. Může ale existovat více než jedna vazba daného typu, který může koncový bod použít. Každé z nich má svou vlastní [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) elementu v rámci elementu typu (Binding). Atribut `bindingconfiguration` slouží k rozlišení mezi vazbami stejného typu. Jeho hodnota je porovnána s atributem `name` prvku [\<vazby >](../../configure-apps/file-schema/wcf/bindings.md) elementu. Další informace o tom, jak nakonfigurovat vazbu klienta pomocí konfigurace, najdete v tématu [Postupy: určení vazby klienta v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 Atribut `behaviorConfiguration` slouží k určení, které [chování\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) má koncový bod použít. Jeho hodnota je porovnána s atributem `name` [\<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu. Příklad použití konfigurace k určení chování klienta najdete v tématu [Konfigurace chování klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 Atribut `contract` určuje, ve kterém kontraktu se koncový bod zveřejňuje. Tato hodnota se mapuje na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute>. Výchozí hodnota je úplný název typu třídy, která implementuje službu.  
  
### <a name="configuring-metadata"></a>Konfigurace metadat  
 K určení nastavení použitých k registraci rozšíření pro import metadat se používá element [> metadata\<](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) . Další informace o rozšíření systému metadat naleznete v tématu [rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Viz také:

- [Koncové body: adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurace chování klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
