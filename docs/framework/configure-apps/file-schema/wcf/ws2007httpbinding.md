---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 2f8cff87280f08af0c426b7a726949b9a9c40197
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732523"
---
# <a name="ws2007httpbinding"></a>\<ws2007HttpBinding >
Definuje interoperabilní vazbu, která poskytuje podporu pro správné verze prvků vazby <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A>.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007HttpBinding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowCookies`|Hodnota, která určuje, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je `false`.<br /><br /> Tuto vlastnost můžete použít při práci s ASP.NET webovými službami (ASMX), které používají soubory cookie. Tím se zajistí, že soubory cookie, které server vrátí, se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.|  
|`bypassProxyOnLocal`|Hodnota, která označuje, zda se má obejít proxy server pro místní adresy. Výchozí hodnota je `false`.|  
|`closeTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval pro dokončení operace ukončení. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`hostNameComparisonMode`|Určuje režim porovnání názvů hostitelů HTTP, který se používá k analýze identifikátorů URI (Uniform Resource Identifier). Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.|  
|`maxBufferPoolSize`|Maximální velikost fondu vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524 288 bajtů (512 × 1 024). Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti. Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné, stejně jako uvolňování paměti pro vyrovnávací paměti. Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a po dokončení vrátit ji do fondu. Tím se vyhnete režie při vytváření a ničení vyrovnávacích pamětí.|  
|`maxReceivedMessageSize`|Maximální velikost zprávy (v bajtech), která je v bajtech nakonfigurovaná pomocí této vazby, může získat. Odesílatel zprávy překračující toto omezení obdrží chybu protokolu SOAP. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|`messageEncoding`|Definuje kodér použitý ke kódování zprávy. Platné hodnoty jsou následující:<br /><br /> -   `Text`: Použijte kodér textové zprávy.<br />-   `Mtom`: Použijte kodér 1,0 (pro organizaci přenosu zpráv).<br /><br /> Výchozí hodnota je `Text`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Název konfigurace vazby Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`proxyAddress`|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud je `true``useSystemWebProxy`, musí být toto nastavení `null`. Výchozí hodnota je `null`.|  
|`receiveTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`sendTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`textEncoding`|Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě. Platné hodnoty jsou následující:<br /><br /> -   `UnicodeFffeTextEncoding`: kódování Unicode big endian.<br />-   `Utf16TextEncoding`: 16bitové kódování.<br />-   `Utf8TextEncoding`: 8bitové kódování.<br /><br /> Výchozí hodnota je `Utf8TextEncoding`.<br /><br /> Tento atribut je typu <xref:System.Text.Encoding>.|  
|`transactionFlow`|Hodnota, která určuje, zda vazba podporuje tok dat WS-Transactions. Výchozí hodnota je `false`.|  
|`useDefaultWebProxy`|Hodnota, která určuje, zda je použit automaticky konfigurovaný proxy server HTTP. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou koncových bodů nakonfigurovaných pomocí této vazby zpracovat. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazby\<](bindings.md)|Tento prvek obsahuje kolekci standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 `WS2007HttpBinding` přidá vazbu poskytnutou systémem, která je podobná `WSHttpBinding`, ale používá organizaci pro pokládání se standardními verzemi OASIS (Structured Information Standards) pro ReliableSession, zabezpečení a TransactionFlow protokoly. Při použití této vazby nejsou vyžadovány žádné změny v objektovém modelu ani výchozí nastavení.  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
