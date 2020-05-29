---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201788"
---
# \<serviceMetadata>
Určuje publikování metadat služby a přidružených informací.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
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
|externalMetadataLocation|Identifikátor URI, který obsahuje umístění souboru WSDL, který je vrácen uživateli v odpovědi na požadavky WSDL a MEX namísto automaticky generovaného WSDL. Pokud tento atribut není nastaven, je vrácen výchozí prvek WSDL. Výchozí hodnota je prázdný řetězec.|  
|httpGetBinding|Řetězec, který určuje typ vazby, který bude použit pro načtení metadat prostřednictvím HTTP GET. Toto nastavení je volitelné. Pokud není zadaný, použijí se výchozí vazby.<br /><br /> Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> . Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .|  
|httpGetBindingConfiguration|Řetězec, který nastaví název vazby, která je zadána v `httpGetBinding` atributu, který odkazuje na Další informace o konfiguraci této vazby. V části se musí definovat stejný název `<bindings>` .|  
|httpGetEnabled|Logická hodnota, která určuje, zda se mají publikovat metadata služby pro načtení pomocí požadavku HTTP/GET. Výchozí formát je `false`.<br /><br /> Pokud není zadán atribut httpGetUrl, adresa, na které jsou metadata publikována, je adresa služby plus a "? WSDL". Například pokud je adresa služby `http://localhost:8080/CalculatorService` , adresa HTTP/GET metadat je `http://localhost:8080/CalculatorService?wsdl` .<br /><br /> Pokud je tato vlastnost `false` nebo adresa služby není založena na http nebo https, "? WSDL" se ignoruje.|  
|httpGetUrl|Identifikátor URI, který určuje adresu, na které jsou metadata publikována pro načtení pomocí požadavku HTTP/GET. Je-li zadán relativní identifikátor URI, bude považován za relativní k základní adrese služby.|  
|httpsGetBinding|Řetězec, který určuje typ vazby, který bude použit pro načtení metadat prostřednictvím protokolu HTTPS GET. Toto nastavení je volitelné. Pokud není zadaný, použijí se výchozí vazby.<br /><br /> Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> . Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .|  
|httpsGetBindingConfiguration|Řetězec, který nastaví název vazby, která je zadána v `httpsGetBinding` atributu, který odkazuje na Další informace o konfiguraci této vazby. V části se musí definovat stejný název `<bindings>` .|  
|httpsGetEnabled|Logická hodnota, která určuje, zda se mají publikovat metadata služby pro načtení pomocí požadavku HTTPS/Get. Výchozí formát je `false`.<br /><br /> Pokud není zadán atribut httpsGetUrl, adresa, na které jsou metadata publikována, je adresa služby plus a "? WSDL". Například pokud je adresa služby " https://localhost:8080/CalculatorService ", adresa HTTP/GET metadat je " https://localhost:8080/CalculatorService?wsdl ".<br /><br /> Pokud je tato vlastnost `false` nebo adresa služby není založena na http nebo https, "? WSDL" se ignoruje.|  
|httpsGetUrl|Identifikátor URI, který určuje adresu, na které jsou metadata publikována pro načtení pomocí požadavku HTTPS/Get.|  
|policyVersion|Řetězec, který určuje verzi používané specifikace WS-Policy. Tento atribut je typu <xref:System.ServiceModel.Description.PolicyVersion> .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace umožňuje řídit funkce publikování metadat služby. Aby nedocházelo k neúmyslnému zveřejnění potenciálně citlivých metadat služby, služba výchozí konfigurace služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je standardně zabezpečené, ale také znamená, že nemůžete použít nástroj pro import metadat (například Svcutil. exe), aby se vygeneroval kód klienta vyžadovaný pro volání služby, pokud není v konfiguraci explicitně povolený chování publikování metadat služby. Pomocí tohoto elementu konfigurace můžete toto chování publikování povolit pro vaši službu.  
  
 Podrobný příklad konfigurace tohoto chování najdete v tématu chování při [publikování metadat](../../../wcf/samples/metadata-publishing-behavior.md).  
  
 Volitelné `httpGetBinding` atributy a `httpsGetBinding` umožňují konfigurovat vazby používané pro načtení METADAT prostřednictvím HTTP GET (nebo https Get). Pokud nejsou zadány, použijí se výchozí vazby ( `HttpTransportBindingElement` v případě protokolu HTTP a `HttpsTransportBindingElement` v případě protokolu HTTPS) pro načtení metadat podle potřeby. Všimněte si, že nemůžete použít tyto atributy s předdefinovanými vazbami WCF. Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> . Kromě toho <xref:System.ServiceModel.Channels.MessageVersion> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .  
  
 Aby se snížila pravděpodobnost, že se služba vystavuje uživatelům se zlými úmysly, je možné zabezpečit přenos pomocí mechanismu SSL přes protokol HTTP (HTTPS). K tomu je nutné nejdřív navazovat vhodný certifikát X. 509 na konkrétní port v počítači, který je hostitelem služby. (Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).) Za druhé přidejte tento prvek do konfigurace služby a nastavte `httpsGetEnabled` atribut na `true` . Nakonec nastavte `httpsGetUrl` atribut na adresu URL koncového bodu metadat služby, jak je znázorněno v následujícím příkladu.  
  
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
 Následující příklad nakonfiguruje službu tak, aby zveřejnila metadata pomocí \<serviceMetadata> elementu. Také nakonfiguruje koncový bod k zveřejnění `IMetadataExchange` kontraktu jako implementace protokolu WS-MetadataExchange (MEX). V příkladu se používá `mexHttpBinding` , což je pohodlná standardní vazba, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastaveným na `None` . V koncovém bodu se používá relativní adresa "MEX", která při překladu na základě základní adresy služeb má za následek adresu koncového bodu `http://localhost/servicemodelsamples/service.svc/mex` .  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Chování publikování metadat](../../../wcf/samples/metadata-publishing-behavior.md)
