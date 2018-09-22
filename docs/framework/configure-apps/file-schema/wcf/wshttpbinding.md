---
title: '&lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 480e10b9667712fbd2a3ffa95e1373d72ee1a9df
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46585465"
---
# <a name="ltwshttpbindinggt"></a>&lt;wsHttpBinding&gt;
Definuje bezpečné, spolehlivé a interoperabilní vazby vhodné pro neduplexní servisní smlouvy. Vazba implementuje následující specifikace: zasílání zpráv WS-Reliable spolehlivost a WS-Security pro ověřování a zabezpečení zpráv. Přenos HTTP a kódování zpráv je Text/XML kódování.  
  
 \<system.ServiceModel>  
\<vazby >  
\<wsHttpBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<wsHttpBinding>  
    <binding   
        allowCookies="Boolean"  
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
          <message   
             algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                          clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
             establishSecurityContext="Boolean"  
             negotiateServiceCredential="Boolean" />  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je false.<br /><br /> Tuto vlastnost můžete použít, když pracujete s ASMX webovými službami, které používají soubory cookie. Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.|  
|bypassProxyOnLocal|Logická hodnota určující, zda obejít proxy server pro místní adresy. Výchozí hodnota je `false`.|  
|closeTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|hostnameComparisonMode|Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 * 1024). Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti. Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné. S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi. Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.|  
|maxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou. Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|messageEncoding|Definuje kodér pro kódování zprávy. Platné hodnoty patří:<br /><br /> -Text: Použijte kodér textu zprávy.<br />-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).<br />– Výchozí hodnota je Text.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Řetězec, který obsahuje konfigurační název vazby. Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|SendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|textEncoding|Určuje znakovou sadu kódování pro vysílání zpráv z vazby. Platné hodnoty patří:<br /><br /> -UnicodeFffeTextEncoding: BigEndian kódování Unicode kódování.<br />-Utf16TextEncoding: kódování 16 bitů.<br />-Utf8TextEncoding: 8 bitů kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding.<br /><br /> Tento atribut je typu <xref:System.Text.Encoding>.|  
|transactionFlow|Logická hodnota určující, zda vazba podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|useDefaultWebProxy|Logická hodnota, která určuje, jestli se používá v systému automaticky nakonfigurovaný proxy HTTP. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Určuje, pokud jsou mezi koncovými body kanál navázat spolehlivé relace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje sadu standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 `WSHttpBinding` Je podobný `BasicHttpBinding` , ale poskytuje další funkce webové služby. Používá přenos pomocí protokolu HTTP a poskytuje zabezpečení zpráv, stejně jako BasicHttpBinding, ale také poskytuje transakce, spolehlivé zasílání zpráv a WS-Addressing, buď povolená ve výchozím nastavení nebo jsou k dispozici nastavení jeden ovládací prvek.  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://foo/bar"  
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
           </wsHttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
