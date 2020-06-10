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
# <a name="client-configuration"></a>Konfigurace klienta
Můžete použít konfiguraci klienta Windows Communication Foundation (WCF) k určení adresy, vazby, chování a kontraktu, vlastností "ABC" koncového bodu klienta, které klienti používají pro připojení ke koncovým bodům služby. [\<client>](../../configure-apps/file-schema/wcf/client.md)Element má [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, jehož atributy se používají ke konfiguraci koncového bodu ABCs. Tyto atributy jsou popsány v části [Konfigurace koncových bodů](#configuring-endpoints) .  
  
 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)Element také obsahuje [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element, který se používá k určení nastavení pro import a export metadat, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) elementu, který obsahuje kolekci vlastních hlaviček adres, a [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elementu, který umožňuje ověřování koncového bodu jinými koncovými body výměny zpráv. [\<headers>](../../configure-apps/file-schema/wcf/headers.md)Prvky a [\<identity>](../../configure-apps/file-schema/wcf/identity.md) jsou uvedeny <xref:System.ServiceModel.EndpointAddress> v části a jsou popsány v článku [adresy](endpoint-addresses.md) . Odkazy na témata, která vysvětlují použití rozšíření metadat, jsou k dispozici v části [Konfigurace metadat](#configuring-metadata) .  
  
## <a name="configuring-endpoints"></a>Konfigurace koncových bodů  
 Konfigurace klienta je navržena tak, aby umožňovala klientovi určit jeden nebo více koncových bodů, každý s vlastním názvem, adresou a kontraktem, přičemž každý odkazuje na [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) prvky a v konfiguraci klienta, které se mají použít ke konfiguraci tohoto koncového bodu. Konfigurační soubor klienta by měl mít název app. config, protože se jedná o název, který modul runtime WCF očekává. Následující příklad ukazuje konfigurační soubor klienta.  
  
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
  
 Volitelný `name` atribut jednoznačně identifikuje koncový bod pro daný kontrakt. Používá je <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> k určení, který koncový bod v konfiguraci klienta je cílen a který musí být načten při vytvoření kanálu ke službě. Zástupný znak konfigurace koncového bodu \* je k dispozici a označuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> metodu, kterou by měl načíst jakoukoli konfiguraci koncového bodu v souboru, pokud je k dispozici přesně jeden dostupný a jinak vyvolá výjimku. Pokud je tento atribut vynechán, použije se jako výchozí koncový bod přidružený k zadanému typu kontraktu odpovídající koncový bod. Výchozí hodnota `name` atributu je prázdný řetězec, který se shoduje s jiným názvem.  
  
 Každý koncový bod musí mít přidruženou adresu pro vyhledání a identifikaci koncového bodu. `address`Atribut lze použít k zadání adresy URL, která poskytuje umístění koncového bodu. Adresa koncového bodu služby se ale dá zadat i v kódu tak, že se vytvoří identifikátor URI (Uniform Resource Identifier) a přidá se k němu <xref:System.ServiceModel.ServiceHost> pomocí jedné z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod. Další informace najdete v tématu [adresy](endpoint-addresses.md). Jak je uvedeno v úvodu [\<headers>](../../configure-apps/file-schema/wcf/headers.md) , [\<identity>](../../configure-apps/file-schema/wcf/identity.md) jsou prvky a součástí <xref:System.ServiceModel.EndpointAddress> a jsou také popsány v tématu [adresy](endpoint-addresses.md) .  
  
 `binding`Atribut určuje typ vazby, který koncový bod očekává, že se má použít při připojování ke službě. Typ musí mít registrovaný konfigurační oddíl, pokud na něj odkazuje. V předchozím příkladu je to [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) oddíl, který indikuje, že koncový bod používá <xref:System.ServiceModel.WSHttpBinding> . Může ale existovat více než jedna vazba daného typu, který může koncový bod použít. Každá z nich má svůj vlastní [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) prvek v rámci elementu typu (Binding). `bindingconfiguration`Atribut slouží k rozlišení mezi vazbami stejného typu. Jeho hodnota je porovnána s `name` atributem [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu. Další informace o tom, jak nakonfigurovat vazbu klienta pomocí konfigurace, najdete v tématu [Postupy: určení vazby klienta v konfiguraci](../how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration`Atribut slouží k určení, který [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) koncový bod má použít. Jeho hodnota je porovnána s `name` atributem [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu. Příklad použití konfigurace k určení chování klienta najdete v tématu [Konfigurace chování klienta](../configuring-client-behaviors.md).  
  
 `contract`Atribut určuje, ve kterém kontraktu se koncový bod zveřejňuje. Tato hodnota je mapována na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute> . Výchozí hodnota je úplný název typu třídy, která implementuje službu.  
  
### <a name="configuring-metadata"></a>Konfigurace metadat  
 [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)Element se používá k určení nastavení, která se používají k registraci rozšíření pro import metadat. Další informace o rozšíření systému metadat naleznete v tématu [rozšíření systému metadat](../extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Viz také

- [Koncové body: adresy, vazby a kontrakty](endpoints-addresses-bindings-and-contracts.md)
- [Konfigurace chování klienta](../configuring-client-behaviors.md)
