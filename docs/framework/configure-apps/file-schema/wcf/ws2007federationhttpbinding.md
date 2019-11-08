---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 0a5090166efd90efa7537f87d5fa47b8c9d078cb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735766"
---
# <a name="ws2007federationhttpbinding"></a>\<ws2007FederationHttpBinding >

Zabezpečená a interoperabilní vazba, která je odvozena z [\<> WSFederationHttpBinding](wsfederationhttpbinding.md) a podporuje federované zabezpečení.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007FederationHttpBinding >**  
  
## <a name="syntax"></a>Syntaxe

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`bypassProxyOnLocal`|Hodnota, která označuje, zda se má obejít proxy server pro místní adresy. Výchozí hodnota je `false`.|
|`closeTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|`hostNameComparisonMode`|Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.|
|`maxBufferPoolSize`|Maximální velikost fondu vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524 288 bajtů (512 * 1024). Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti. Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu. Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.|
|`maxReceivedMessageSize`|Maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby. Odesílatel zprávy, která překračuje toto omezení, obdrží chybu protokolu SOAP. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|
|`messageEncoding`|Definuje kodér použitý ke kódování zprávy. Platné hodnoty jsou následující:<br /><br /> -Text: Použijte kodér textové zprávy.<br />-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).<br /><br /> Výchozí hodnota je text.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|
|`name`|Název konfigurace vazby Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|
|`openTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|`privacyNoticeAt`|Identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.|
|`privacyNoticeVersion`|Verze aktuálního oznámení o ochraně osobních údajů.|
|`proxyAddress`|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud je `true``useDefaultWebProxy`, musí být toto nastavení `null`. Výchozí hodnota je `null`.|
|`receiveTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|
|`sendTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|`textEncoding`|Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě. Platné hodnoty jsou následující:<br /><br /> -BigEndianUnicode: kódování Unicode big endian.<br />-Unicode: 16 bitů kódování.<br />-UTF8:8bitové kódování.<br /><br /> Výchozí hodnota je UTF8. Tento atribut je typu <xref:System.Text.Encoding>.|
|`transactionFlow`|Hodnota, která určuje, zda vazba podporuje tok dat WS-Transactions. Výchozí hodnota je `false`.|
|`useDefaultWebProxy`|Hodnota, která označuje, zda je použit automaticky konfigurovaný proxy server HTTP. Adresa proxy serveru musí být `null` (tj. není nastavena), pokud je tento atribut `true`. Výchozí hodnota je `true`.|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[> zabezpečení \<](security-of-wsfederationhttpbinding.md)|Definuje nastavení zabezpečení zprávy. Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|
|[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[vazby\<](bindings.md)|Tento prvek obsahuje kolekci standardních a vlastních vazeb.|

## <a name="remarks"></a>Poznámky

Federace je schopnost sdílet identity napříč několika společnostmi nebo důvěřovat doménám pro ověřování a autorizaci. Používá protokol WS-Trust k mapování reprezentace identity z jedné domény důvěryhodnosti na jinou. Federační vazba protokolu HTTP podporuje zabezpečení SOAP i zabezpečení ve smíšeném režimu, ale nepodporuje zabezpečení přenosu. Služby nakonfigurované s touto vazbou musí používat přenos HTTP. Další informace najdete v tématu [\<wsFederationHttpBinding >](wsfederationhttpbinding.md).

## <a name="example"></a>Příklad

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding >](wsfederationhttpbinding.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
