---
title: <wsHttpContextBinding>
ms.date: 03/30/2017
ms.assetid: 1e40b5c9-0df2-4d66-afc5-a99d0e4ae7a4
ms.openlocfilehash: 20d931dfd1805dd4b56aabbab778e6587caa003a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112460"
---
# <a name="wshttpcontextbinding"></a>\<wsHttpContextBinding>
Poskytuje kontext pro <xref:System.ServiceModel.WSHttpBinding> , která vyžaduje, aby úroveň ochrany byla podepsána.  
  
\<system.serviceModel>  
\<vazby >  
\<wsHttpContextBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<wsHttpContextBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           contextProtectionLevel="EncryptAndSign/None/Sign"
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
                 realm="string"
                 defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 defaultRealm="string" />
      <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
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
</wsHttpContextBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je `false`.<br /><br /> Když `allowCookies` je nastavena na `true`, kanál contextChannel použije httpCookies jako režim výměny kontextu. Když tento atribut je nastaven na `false`, kontext se vyměňují jako záhlaví soap.<br /><br /> Výchozí hodnota je `false`.<br /><br /> Tuto vlastnost můžete použít, když pracujete s ASMX webovými službami, které používají soubory cookie. Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.|  
|bypassProxyOnLocal|Logická hodnota určující, zda obejít proxy server pro místní adresy. Výchozí hodnota je `false`.|  
|closeTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|contextProtectionLevel|Platný <xref:System.Net.Security.ProtectionLevel> hodnotu, která určuje úroveň ochrany požadované záhlaví SOAP umožňuje šíření informací o kontextu.  Výchozí hodnota je `Sign`.|  
|hostnameComparisonMode|Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 * 1024). Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti. Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné. S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi. Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.|  
|maxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou. Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|messageEncoding|Definuje kodér pro kódování zprávy. Platné hodnoty patří:<br /><br /> -Text: Použijte kodér textu zprávy.<br />-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).<br />– Výchozí hodnota je Text.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Řetězec, který obsahuje konfigurační název vazby. Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|SendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|textEncoding|Určuje znakovou sadu kódování pro vysílání zpráv z vazby. Platné hodnoty patří:<br /><br /> -UnicodeFffeTextEncoding: Kódování Unicode BigEndian.<br />-Utf16TextEncoding: 16bitové kódování.<br />-Utf8TextEncoding: 8bitové kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding.<br /><br /> Tento atribut je typu <xref:System.Text.Encoding>.|  
|transactionFlow|Logická hodnota určující, zda vazba podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|useDefaultWebProxy|Logická hodnota, která určuje, jestli se používá v systému automaticky nakonfigurovaný proxy HTTP. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Určuje, pokud jsou mezi koncovými body kanál navázat spolehlivé relace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje sadu standardních a vlastních vazeb.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpContextBinding>
- <xref:System.ServiceModel.Configuration.WSHttpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
- [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
