---
title: "&lt;– ws2007HttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c28b5f0304106fb2aa3e95e68ddb798b5a1fe0b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltws2007httpbindinggt"></a>&lt;– ws2007HttpBinding&gt;
Definuje vazbu umožňuje vzájemnou spolupráci, která poskytuje podporu pro správné verze <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementů vazby.  
  
 \<system.serviceModel >  
\<vazby >  
\<– ws2007HttpBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007HttpBinding>  
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
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowCookies`|Hodnota, která určuje, jestli klient přijímá soubory cookie a rozšiřuje je na dalších požadavků. Výchozí hodnota je `false`.<br /><br /> Pokud při práci s ASP.NET – webové služby (ASMX), které používají soubory cookie, můžete tuto vlastnost. Tím se zajistí, že soubory cookie, které vrací na server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.|  
|`bypassProxyOnLocal`|Hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy. Výchozí hodnota je `false`.|  
|`closeTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`hostnameComparisonMode`|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory Uniform Resource (Identifier). Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.|  
|`maxBufferPoolSize`|Velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 × 1 024 jednotek). Mnoho částí [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] použít vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je náročné, jako je uvolňování paměti pro vyrovnávací paměti. S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Tím je zabráněno režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|`maxReceivedMessageSize`|Maximální velikost zprávy, v bajtech, včetně hlavičky, které jsou konfigurovány pomocí této vazby kanál může přijímat. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|`messageEncoding`|Definuje kodér použitá ke kódování zprávy. Platné hodnoty patří:<br /><br /> -   `Text`: Pomocí kodéru text zprávy.<br />-   `Mtom`: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).<br /><br /> Výchozí hodnota je `Text`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`proxyAddress`|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|`receiveTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`textEncoding`|Určuje znakovou sadu kódování použité pro generování zpráv v rámci vazby. Platné hodnoty patří:<br /><br /> -   `UnicodeFffeTextEncoding`: Unicode Big Endian kódování.<br />-   `Utf16TextEncoding`: 16bitové kódování.<br />-   `Utf8TextEncoding`: 8bitové kódování.<br /><br /> Výchozí hodnota je `Utf8TextEncoding`.<br /><br /> Tento atribut je typu <xref:System.Text.Encoding>.|  
|`transactionFlow`|Hodnota, která určuje, zda vazby podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|`useDefaultWebProxy`|Hodnota, která určuje, jestli je použít server proxy protokolu HTTP pro automatickou konfiguraci systému. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které může zpracovat koncových bodů s touto vazbou. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Určuje, zda jsou určeny spolehlivé relace mezi koncovými body kanálu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `WS2007HttpBinding` Přidá poskytované systémem vazbu podobná `WSHttpBinding` ale používá organizace pro standardní verze protokoly ReliableSession, zabezpečení a TransactionFlow rozvoj z strukturovaných informace standardy (OASIS). Při použití této vazbě je potřeba žádné změny objektu modelu, nebo výchozí nastavení.  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
