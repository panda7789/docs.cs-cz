---
title: Konfigurace klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: ff82f56639ec451c04624d22fff0bcb03f46d946
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185366"
---
# <a name="client-configuration"></a>Konfigurace klienta
Pomocí konfigurace klienta WCF (Windows Communication Foundation) můžete určit adresu, vazbu, chování a smlouvu, vlastnosti "ABC" koncového bodu klienta, který klienti používají k připojení ke koncovým bodům služby. Prvek [ \<klienta>](../../configure-apps/file-schema/wcf/client.md) má [ \<koncový bod>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) prvek, jehož atributy se používají ke konfiguraci řadičů domény koncového bodu. Tyto atributy jsou popsány v [části Konfigurace koncových bodů.](#configuring-endpoints)  
  
 [ \<Koncový bod>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) prvek také obsahuje [ \<prvek>metadata,](../../configure-apps/file-schema/wcf/metadata.md) který se používá k určení nastavení pro import a export metadat, [ \<záhlaví>](../../configure-apps/file-schema/wcf/headers.md) prvek, který obsahuje kolekci vlastních adresních hlaviček, a prvek>[ \<identity,](../../configure-apps/file-schema/wcf/identity.md) který umožňuje ověřování koncového bodu jinými koncovými body, které si s ním vyměňují zprávy. [ \<Záhlaví>](../../configure-apps/file-schema/wcf/headers.md) a [ \<prvky>identity](../../configure-apps/file-schema/wcf/identity.md) jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsány v článku [Adresy.](../../wcf/feature-details/endpoint-addresses.md) Odkazy na témata, která vysvětlují použití rozšíření metadat, jsou uvedeny v části [Konfigurace metadat.](#configuring-metadata)  
  
## <a name="configuring-endpoints"></a>Konfigurace koncových bodů  
 Konfigurace klienta je navržena tak, aby klientovi umožnila zadat jeden nebo více koncových bodů, z nichž každý má svůj vlastní název, adresu a smlouvu, přičemž každá odkazující [ \<na vazby>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) a [ \<chování>prvky](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) v konfiguraci klienta, které mají být použity ke konfiguraci tohoto koncového bodu. Konfigurační soubor klienta by měl mít název "App.config", protože se jedná o název, který očekává běh WCF. Následující příklad ukazuje konfigurační soubor klienta.  
  
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
  
 Volitelný `name` atribut jednoznačně identifikuje koncový bod pro danou smlouvu. Používá se <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> určit, který koncový bod v konfiguraci klienta je cílována a musí být načten při vytvoření kanálu do služby. Název konfigurace koncového bodu\*se zástupnými symboly " je k dispozici a označuje metodu, <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> která by měla načíst libovolnou konfiguraci koncového bodu v souboru, za předpokladu, že je k dispozici přesně jedna a jinak vyvolá výjimku. Pokud je tento atribut vynechán, odpovídající koncový bod se používá jako výchozí koncový bod přidružený k zadanému typu smlouvy. Výchozí hodnota atributu `name` je prázdný řetězec, který odpovídá jako jakýkoli jiný název.  
  
 Každý koncový bod musí mít přidruženou adresu, aby bylo možné koncový bod vyhledat a identifikovat. Atribut `address` lze zadat adresu URL, která poskytuje umístění koncového bodu. Ale adresu pro koncový bod služby lze také zadat v kódu vytvořením identifikátoru <xref:System.ServiceModel.ServiceHost> uniformní <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> prostředky (URI) a je přidán do pomocí jedné z metod. Další informace naleznete [v tématu Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Jak naznačuje úvod, [ \<záhlaví>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a <xref:System.ServiceModel.EndpointAddress> [ \<prvky>identity](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) jsou součástí a jsou také popsány v tématu [Adresy.](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
  
 Atribut `binding` označuje typ vazby, kterou koncový bod očekává při připojení ke službě. Typ musí mít registrovaný konfigurační oddíl, pokud má být odkazován. V předchozím příkladu se jedná o <xref:System.ServiceModel.WSHttpBinding> [ \<oddíl wsHttpBinding>,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) který označuje, že koncový bod používá . Ale může existovat více než jednu vazbu daného typu, který může koncový bod použít. Každý z nich má vlastní [ \<vazby>](../../configure-apps/file-schema/wcf/bindings.md) prvek v rámci elementu typu (vazba). Atribut `bindingconfiguration` se používá k rozlišení mezi vazbami stejného typu. Jeho hodnota je porovnána s atributem `name` [ \<prvku vazby>.](../../configure-apps/file-schema/wcf/bindings.md) Další informace o konfiguraci vazby klienta pomocí konfigurace naleznete v [tématu How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 Atribut `behaviorConfiguration` se používá k určení [ \<chování,](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) které chování [ \<>koncového boduBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) koncový bod by měl použít. Jeho hodnota je porovnána s atributem `name` [ \<prvku>chování.](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Příklad použití konfigurace k určení chování klienta naleznete v [tématu Konfigurace chování klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 Atribut `contract` určuje, který kontrakt koncový bod je vystavení. Tato hodnota se <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> mapuje na <xref:System.ServiceModel.ServiceContractAttribute>rozhraní . Výchozí hodnota je úplný název typu třídy, která implementuje službu.  
  
### <a name="configuring-metadata"></a>Konfigurace metadat  
 Prvek [ \<>metadat](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) se používá k určení nastavení používaných k registraci rozšíření importu metadat. Další informace o rozšíření systému metadat naleznete v [tématu Rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Viz také

- [Koncové body: adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurace chování klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
