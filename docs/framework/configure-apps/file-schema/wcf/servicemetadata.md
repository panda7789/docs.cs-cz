---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 0b06d61a33cd6a704a5ab0f75d29bde3f72d77fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115853"
---
# <a name="servicemetadata"></a>\<serviceMetadata>
Určuje zveřejnění metadat služby a související informace.  
  
\<system.serviceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceMetadata>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|externalMetadataLocation|Identifikátor Uri, který obsahuje umístění souboru WSDL, který je vrácen uživateli v reakci na požadavky WSDL a MEX, namísto automaticky generovaného WSDL. Pokud tento atribut není nastaven, výchozí WSDL vrácena. Výchozí hodnota je prázdný řetězec.|  
|httpGetBinding|Řetězec, který určuje typ vazby, který se použije pro načtení metadat prostřednictvím HTTP GET. Toto nastavení je volitelné. Pokud se nezadá, použije se výchozí vazby.<br /><br /> Pouze vazby s vnitřní elementy vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> bude podporovat. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Řetězec, který nastaví název vazby určený v `httpGetBinding` atribut, který odkazuje Další informace o konfiguraci této vazby. Se stejným názvem musí být definován v `<bindings>` oddílu.|  
|httpGetEnabled|Logická hodnota, která určuje, jestli se má být zveřejněna metadata služby pro načtení pomocí požadavku HTTP/Get. Výchozí hodnota je `false`.<br /><br /> Pokud není zadán atribut httpGetUrl, adresu, kde jsou zveřejněna metadata je adresa služby navíc "? wsdl". Například, pokud je adresa služby "http://localhost:8080/CalculatorService", je adresa protokolu HTTP/Get metadat"http://localhost:8080/CalculatorService?wsdl".<br /><br /> Pokud je tato vlastnost `false`, nebo adresu služby není založen na protokolu HTTP nebo HTTPS, "? wsdl" se ignoruje.|  
|httpGetUrl|Identifikátor Uri určující adresu, která je zveřejněna metadata pro načtení pomocí požadavku HTTP/Get. Pokud je zadán relativní identifikátor Uri bude zpracována jako relativní k základní adresu služby.|  
|httpsGetBinding|Řetězec, který určuje typ vazby, který bude použit pro načtení metadat prostřednictvím HTTPS GET. Toto nastavení je volitelné. Pokud se nezadá, použije se výchozí vazby.<br /><br /> Pouze vazby s vnitřní elementy vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> bude podporovat. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Řetězec, který nastaví název vazby určený v `httpsGetBinding` atribut, který odkazuje Další informace o konfiguraci této vazby. Se stejným názvem musí být definován v `<bindings>` oddílu.|  
|httpsGetEnabled|Logická hodnota, která určuje, jestli se má být zveřejněna metadata služby pro načtení pomocí požadavku HTTPS/Get. Výchozí hodnota je `false`.<br /><br /> Pokud není zadán atribut httpsGetUrl, adresu, kde jsou zveřejněna metadata je adresa služby navíc "? wsdl". Například, pokud je adresa služby "https://localhost:8080/CalculatorService", je adresa protokolu HTTP/Get metadat"https://localhost:8080/CalculatorService?wsdl".<br /><br /> Pokud je tato vlastnost `false`, nebo adresu služby není založen na protokolu HTTP nebo HTTPS, "? wsdl" se ignoruje.|  
|httpsGetUrl|Identifikátor Uri určující adresu, která je zveřejněna metadata pro načtení pomocí požadavku HTTPS/Get.|  
|policyVersion|Řetězec, který určuje verzi používané specifikace WS-Policy. Tento atribut je typu <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace umožňuje ovládat funkce publikování metadat služby. Pokud chcete zabránit neúmyslnému zveřejnění metadat služby potenciálně citlivých, výchozí konfigurace pro služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečený, ale také znamená, že nemůžete použít metadat importovat nástroj (například Svcutil.exe) ke generování kódu klienta, který je potřeba volat službu, není-li v konfiguraci není explicitně povoleno chování publikování metadat služby. Pomocí tento prvek konfigurace, můžete povolit toto chování publikování pro vaši službu.  
  
 Podrobný příklad konfigurace toto chování najdete v tématu [chování publikování metadat](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 Volitelný `httpGetBinding` a `httpsGetBinding` atributy umožňují konfigurovat vazbu použitou pro načtení metadat prostřednictvím HTTP GET (nebo HTTPS GET). Pokud zadané není, výchozí vazby (`HttpTransportBindingElement`, v případě protokolu HTTP a `HttpsTransportBindingElement`, v případě protokolu HTTPS) se používají pro načtení metadat podle potřeby. Všimněte si, že tyto atributy nelze použít s integrovanou vazeb WCF. Pouze vazby s vnitřní elementy vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> bude podporovat. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Aby se snížila zranitelnost služby k uživateli se zlými úmysly, je možné na vyžádání bezpečného přenosu pomocí protokolu SSL přes HTTP (HTTPS) mechanismus. Uděláte to tak, musíte nejprve vytvořit vazbu vhodný certifikát X.509, na konkrétní port na počítači, který je hostitelem služby. (Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Za druhé, přidejte tento element konfigurace služby a nastavte `httpsGetEnabled` atribut `true`. Nastavte `httpsGetUrl` atribut na adresu URL koncového bodu metadat služby, jak je znázorněno v následujícím příkladu.  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace ve službě zpřístupňují metadata s využitím \<serviceMetadata > element. Nakonfiguruje taky zveřejnit koncový bod `IMetadataExchange` kontrakt jako implementaci protokolu WS-MetadataExchange (MEX). V příkladu se používá `mexHttpBinding`, což je usnadnění standardní vazbu, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastaveno `None`. Relativní adresa "mex" se používá koncový bod, který se při vyřešení proti základní služby adresu výsledkem adresy koncového bodu z `http://localhost/servicemodelsamples/service.svc/mex`.  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Chování publikování metadat](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
