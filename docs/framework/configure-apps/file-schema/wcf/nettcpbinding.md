---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: c43c141093c8287adb6d5a841a43ac893deefccd
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139339"
---
# <a name="nettcpbinding"></a>\<netTcpBinding >

Určuje zabezpečenou, spolehlivou a optimalizovanou vazbu vhodnou pro komunikaci mezi počítači. Ve výchozím nastavení vygeneruje komunikační zásobník za běhu s zabezpečením systému Windows za účelem zabezpečení a ověřování zpráv, TCP pro doručování zpráv a kódování binárních zpráv.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netTcpBinding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`closeTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`hostNameComparisonMode`|Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.|  
|`listenBacklog`|Celé kladné číslo určující maximální počet kanálů, které čekají na přijetí na naslouchací službě. Překročení tohoto limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem. Atribut `connectionTimeout` omezuje dobu, po kterou bude klient čekat na připojení před vyvoláním výjimky připojení. Výchozí hodnota je 10.|  
|`maxBufferPoolSize`|Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 512 × 1024 bajtů. Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti. Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu. Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.|  
|`maxBufferSize`|Celé kladné číslo určující maximální velikost vyrovnávací paměti, která se používá k ukládání zpráv v paměti, v bajtech.<br /><br /> Pokud atribut `transferMode` se rovná `Buffered`, tento atribut by měl být roven hodnotě atributu `maxReceivedMessageSize`.<br /><br /> Pokud atribut `transferMode` se rovná `Streamed`, tento atribut nemůže být větší než hodnota atributu `maxReceivedMessageSize` a měla by být alespoň velikost záhlaví.<br /><br /> Výchozí hodnota je 65536. Další informace najdete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|`maxConnections`|Celé číslo, které určuje maximální počet odchozích a příchozích připojení, které služba vytvoří nebo přijme. Příchozí a odchozí připojení se počítají na základě zvláštního limitu určeného tímto atributem.<br /><br /> Příchozí připojení přesahující tento limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.<br /><br /> Odchozí připojení přesahující limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.<br /><br /> Výchozí hodnota je 10.|  
|`maxReceivedMessageSize`|Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby. Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|`name`|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby. Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`portSharingEnabled`|Logická hodnota, která určuje, zda je pro toto připojení povoleno sdílení portu TCP. Pokud je to `false`, každá vazba používá vlastní výhradní port. Toto nastavení je relevantní pouze pro služby, protože nejsou ovlivněni klienti.|  
|`receiveTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`sendTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`transactionFlow`|Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions. Výchozí hodnota je `false`.|  
|`transactionProtocol`|Určuje transakční protokol, který se má použít s touto vazbou. Platné hodnoty jsou<br /><br /> – OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Výchozí hodnota je OleTransactions. Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.|  
|`transferMode`|Hodnota <xref:System.ServiceModel.TransferMode>, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány nebo jsou požadavkem či odpovědí.|  
  
### <a name="child-elements"></a>Podřízené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-nettcpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.|  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazby\<](bindings.md)|Tento prvek obsahuje kolekci standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky

Tato vazba generuje ve výchozím nastavení zásobník pro komunikaci za běhu, který používá zabezpečení přenosu, TCP pro doručování zpráv a binární kódování zpráv. Tato vazba je vhodným uživatelem určeným Windows Communication Foundation (WCF) pro komunikaci přes intranet.  
  
 Výchozí konfigurace `netTcpBinding` je rychlejší než konfigurace, kterou poskytuje `wsHttpBinding`, ale je určena pouze pro komunikaci WCF. Chování zabezpečení lze konfigurovat pomocí volitelného atributu `securityMode`. Použití WS-ReliableMessaging lze konfigurovat pomocí volitelného atributu `reliableSessionEnabled`. Ale spolehlivé zasílání zpráv je ve výchozím nastavení vypnuté. Obecně platí, že vazby poskytované systémem HTTP, například `wsHttpBinding` a `basicHttpBinding`, jsou nakonfigurovány tak, aby ve výchozím nastavení zapnuly výchozí hodnoty, zatímco vazba `netTcpBinding` ve výchozím nastavení vypne, takže je nutné se přihlásit k podpoře, například pro jednu z možností WS-*. tématech. To znamená, že výchozí konfigurace pro protokol TCP je rychlejší při výměně zpráv mezi koncovými body, než jsou nastavené pro vazby HTTP ve výchozím nastavení.  
  
## <a name="example"></a>Příklad

Vazba je určena v konfiguračních souborech pro klienta a službu. Typ vazby je určen v atributu `binding` `<endpoint>` elementu. Pokud chcete nakonfigurovat vazbu netTcpBinding a změnit některá její nastavení, je nutné definovat konfiguraci vazby. Koncový bod musí odkazovat na konfiguraci vazby s atributem `bindingConfiguration`. V následujícím příkladu je definována konfigurace vazby.  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
