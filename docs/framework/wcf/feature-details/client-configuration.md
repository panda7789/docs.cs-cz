---
title: Konfigurace klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 2e178f8b08fbadbb5549fa10631d3a57f71a7e0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503219"
---
# <a name="client-configuration"></a>Konfigurace klienta
Konfigurace klienta Windows Communication Foundation (WCF) můžete použít k určení adresy, vazby, chování a kontrakt, vlastnosti "ABC" koncový bod klienta, který klienti používají k připojení ke koncovým bodům služby. [ \<Klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element má [ \<koncový bod >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu, jejichž atributy se používají ke konfiguraci koncového bodu základních informací. Tyto atributy jsou popsány v části "Konfigurace koncových bodů" tohoto tématu.  
  
 [ \<Koncový bod >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) také obsahuje element [ \<metadat >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element, který se používá k určení nastavení pro import a Export metadat, [ \<záhlaví >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element, který obsahuje kolekce záhlaví adres vlastní, a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element, který umožňuje ověřování z koncového bodu jiné koncové body Výměna zpráv s ním. [ \<Záhlaví >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) prvky jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou popsány v [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tématu. Odkazy na témata, která popisují použití metadata rozšíření jsou k dispozici v části Konfigurace metadat dílčí části tohoto tématu.  
  
## <a name="configuring-endpoints"></a>Konfigurace koncových bodů  
 Konfigurace klienta je navržena k umožnění klienta určit jeden nebo další koncové body, každý s vlastními názvy adres a smlouvy se každá odkazující na [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) a [ \< chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) prvky v konfiguraci klienta, který se má použít ke konfiguraci tohoto koncového bodu. Konfigurační soubor klienta by měl s názvem "App.config", protože jde o název, který očekává, že modul runtime WCF. Následující příklad ukazuje klienta konfigurační soubor.  
  
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
  
 Volitelný `name` atribut jednoznačně identifikuje koncový bod pro daný kontrakt. Používá se <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> , nebo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> k určení, který koncový bod v konfiguraci klienta je cílem a musí být načten, když se vytvoří kanál ke službě. Zástupný název konfigurace koncového bodu "*" je k dispozici a pozná, <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> , že ho předpokladu, že existuje přesně jeden k dispozici a jinak by se měly načíst všechny konfigurace koncového bodu v souboru, metoda vyvolá výjimku. Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod přidružený k typu zadaného kontraktu. Výchozí hodnota `name` atribut je prázdný řetězec, což je nalezena shoda s jako jakýkoli jiný název.  
  
 Každý koncový bod musí mít adresu přidruženo k vyhledání a identifikaci koncového bodu. `address` Atribut lze použít k určení adresy URL, která poskytuje umístění koncového bodu. Ale adresu koncového bodu služby můžete také zadat v kódu tak, že vytvoříte identifikátor URI (Uniform Resource) a je přidán <xref:System.ServiceModel.ServiceHost> pomocí jedné z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Další informace najdete v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Protože po zavedení naznačuje, [ \<záhlaví >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) prvky jsou součástí <xref:System.ServiceModel.EndpointAddress> a jsou také popsány v [ Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tématu.  
  
 `binding` Atribut určuje typ vazby koncového bodu očekává, že mají používat při připojování ke službě. Typ musí mít registrované konfigurační oddíl, pokud má odkazovat. V předchozím příkladu je to [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) části, která označuje, že koncový bod používá <xref:System.ServiceModel.WSHttpBinding>. Nicméně mohou existovat více než jednu vazbu daného typu, který můžete použít koncový bod. Každý z nich má vlastní [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu v typu elementu (vazby). `bindingconfiguration` Atribut se používá k rozlišení mezi vazby stejného typu. Její hodnota je nalezena shoda s `name` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu. Další informace o tom, jak nakonfigurovat klienta vazby pomocí konfigurace, najdete v článku [jak: Zadání klientské vazby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration` Atribut se používá k určení [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) koncový bod by měl používat. Její hodnota je nalezena shoda s `name` atribut [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu. Příklad použití konfigurace k určení chování klienta najdete v tématu [konfigurace chování klientů](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 `contract` Atribut určuje kontrakt, který vystavuje koncový bod. Tato hodnota se mapuje <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> z <xref:System.ServiceModel.ServiceContractAttribute>. Výchozí hodnota je název úplný typ třídy, která implementuje služby.  
  
### <a name="configuring-metadata"></a>Konfigurace metadat  
 [ \<Metadat >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element slouží k určení nastavení použije k registraci metadat import rozšíření. Další informace o rozšíření systému metadat najdete v tématu [rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Viz také:
- [Koncové body: Adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurace chování klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
