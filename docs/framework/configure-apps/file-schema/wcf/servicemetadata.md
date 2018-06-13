---
title: '&lt;serviceMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 3c59a47f8a45fbccb05eb1f385215fe2aa739836
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751773"
---
# <a name="ltservicemetadatagt"></a>&lt;serviceMetadata&gt;
Určuje publikování metadat služby a související informace.  
  
\<system.serviceModel>  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceMetadata >  
  
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
|ExternalMetadataLocation|Identifikátor Uri, která obsahuje umístění souboru WSDL, která je vrátil uživateli v reakci na požadavky WSDL a MEX místo automaticky generovaný WSDL. Pokud není tento atribut nastavený, je výchozí WSDL vrátila. Výchozí hodnota je prázdný řetězec.|  
|elementy httpGetBinding|Řetězec, který určuje typ vazby, který se použije pro načtení metadat pomocí metody GET protokolu HTTP. Toto nastavení je volitelné. Pokud není zadaný, použije se výchozí vazby.<br /><br /> Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> budou podporovány. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Řetězec, který nastaví název vazby, který je uveden v `httpGetBinding` atribut, který odkazuje na další konfigurační informace této vazby. Se stejným názvem, musí být definován v `<bindings>` oddílu.|  
|HttpGetEnabled|Logická hodnota, která určuje, zda publikování metadat služby k získání pomocí požadavek HTTP/Get. Výchozí hodnota je `false`.<br /><br /> Pokud není zadán atribut httpGetUrl, adresu, kde je zveřejněna metadat je adresa služby plus "? wsdl". Například, pokud je adresa služby "http://localhost:8080/CalculatorService", je adresa protokolu HTTP nebo získat metadata"http://localhost:8080/CalculatorService?wsdl".<br /><br /> Pokud je tato vlastnost `false`, nebo adresu služby není založen na protokolu HTTP nebo HTTPS, "? wsdl" je ignorována.|  
|HttpGetUrl|Identifikátor Uri, který určuje, kdy je zveřejněna metadata k získání pomocí požadavek HTTP nebo získat adresu. Pokud je zadán relativní identifikátor Uri nakládáno jako relativně k základní adresa služby.|  
|httpsGetBinding|Řetězec, který určuje typ vazby, který se použije pro načtení metadat prostřednictvím protokolu HTTPS získat. Toto nastavení je volitelné. Pokud není zadaný, použije se výchozí vazby.<br /><br /> Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> budou podporovány. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Řetězec, který nastaví název vazby, který je uveden v `httpsGetBinding` atribut, který odkazuje na další konfigurační informace této vazby. Se stejným názvem, musí být definován v `<bindings>` oddílu.|  
|HttpsGetEnabled|Logická hodnota, která určuje, zda publikování metadat služby k získání pomocí požadavek HTTPS nebo získat. Výchozí hodnota je `false`.<br /><br /> Pokud není zadán atribut httpsGetUrl, adresu, kde je zveřejněna metadat je adresa služby plus "? wsdl". Například, pokud je adresa služby "https://localhost:8080/CalculatorService", je adresa protokolu HTTP nebo získat metadata"https://localhost:8080/CalculatorService?wsdl".<br /><br /> Pokud je tato vlastnost `false`, nebo adresu služby není založen na protokolu HTTP nebo HTTPS, "? wsdl" je ignorována.|  
|HttpsGetUrl|Identifikátor Uri, který určuje, kdy je zveřejněna metadata k získání pomocí požadavek HTTPS nebo získat adresu.|  
|PolicyVersion|Řetězec, který určuje verzi specifikace WS-Policy, který je používán. Tento atribut je typu <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element konfigurace můžete k řízení funkcí publikování metadat služby. Pokud chcete zabránit neúmyslnému zveřejnění metadata potenciálně citlivých služby, výchozí konfiguraci pro služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečení, ale také znamená, že nelze použít metadata importovat nástroj (například Svcutil.exe) ke generování kódu klienta pro volání služby, pokud není výslovně povolena chování publikování metadat služby v konfiguraci požadován. Pomocí elementu. Tato konfigurace, můžete povolit toto chování při publikování pro vaši službu.  
  
 Podrobný příklad konfigurace toto chování najdete v tématu [chování publikování metadat](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 Volitelné `httpGetBinding` a `httpsGetBinding` atributů umožňují konfigurovat vazby používá pro načtení metadat prostřednictvím metody GET protokolu HTTP (nebo získat HTTPS). Pokud nejsou zadané, výchozí vazby (`HttpTransportBindingElement`, v případě protokolu HTTP a `HttpsTransportBindingElement`, v případě HTTPS) se používají pro načtení metadat podle potřeby. Všimněte si, že tyto atributy nelze použít s integrovanou vazby WCF. Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> budou podporovány. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Aby se snížila zranitelnost služby uživatelům se zlými úmysly, je možné zabezpečit přenos pomocí protokolu SSL přes protokol HTTP (HTTPS) mechanismus. To pokud chcete udělat, je třeba nejprve svázat vhodný certifikát X.509 konkrétní port, na počítači, který je hostitelem služby. (Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Druhý, přidejte tento element konfigurace služby a nastavte `httpsGetEnabled` atribut `true`. Nakonec nastavte `httpsGetUrl` atribut na adresu URL metadat koncového bodu služby, jak je znázorněno v následujícím příkladu.  
  
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
 Následující příklad konfigurace ve službě vystavit metadat pomocí \<serviceMetadata > elementu. Nakonfiguruje taky koncový bod ke zveřejnění `IMetadataExchange` kontrakt jako implementaci protokolu WS-MetadataExchange (MEX). V příkladu se používá `mexHttpBinding`, což je pro vaše pohodlí standardní vazby, která je ekvivalentní `wsHttpBinding` s režim zabezpečení nastavený na `None`. Relativní adresu "mex" se používá v koncovém bodě, který v případě přeložit proti služby základní adresu výsledkem koncový bod adresy http://localhost/servicemodelsamples/service.svc/mex.  
  
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
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Chování při publikování metadat](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
