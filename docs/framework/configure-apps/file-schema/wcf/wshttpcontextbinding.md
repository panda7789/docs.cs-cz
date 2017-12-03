---
title: '&lt;wsHttpContextBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e40b5c9-0df2-4d66-afc5-a99d0e4ae7a4
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d17c270b7969b858903e5b86124801a1fb1acdc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltwshttpcontextbindinggt"></a>&lt;wsHttpContextBinding&gt;
Poskytuje kontext pro <xref:System.ServiceModel.WSHttpBinding> který vyžaduje, aby byly podepsány úroveň ochrany.  
  
\<system.serviceModel >  
\<vazby >  
\<wsHttpContextBinding >  
  
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
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků. Výchozí hodnota je `false`.<br /><br /> Když `allowCookies` je nastaven na `true`, contextChannel použije httpCookies jako režim výměna kontextu. Když tento atribut je nastaven na `false`, kontextu se vyměňují jako hlavičky soap.<br /><br /> Výchozí hodnota je `false`.<br /><br /> Tuto vlastnost lze použít při používání ASMX webové služby, které používají soubory cookie. Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.|  
|bypassProxyOnLocal|Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy. Výchozí hodnota je `false`.|  
|Intervalu|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|contextProtectionLevel|Platná <xref:System.Net.Security.ProtectionLevel> hodnotu, která určuje úroveň ochrany požadované hlavičky SOAP šíří kontextové informace.  Výchozí hodnota je `Sign`.|  
|hostnameComparisonMode|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 * 1024). Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|MaxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|messageEncoding|Definuje kodér použitá ke kódování zprávy. Platné hodnoty patří:<br /><br /> -Text: Pomocí kodéru text zprávy.<br />-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).<br />-Výchozí hodnota je Text.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|sendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|textEncoding|Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby. Platné hodnoty patří:<br /><br /> -UnicodeFffeTextEncoding: Unicode BigEndian kódování.<br />-Utf16TextEncoding: 16bitové kódování.<br />-Utf8TextEncoding: 8bitové kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding.<br /><br /> Tento atribut je typu <xref:System.Text.Encoding>.|  
|transactionFlow|Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|useDefaultWebProxy|Logická hodnota, která určuje, jestli je použít server proxy protokolu HTTP pro automatickou konfiguraci systému. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Určuje, pokud jsou určeny spolehlivé relace mezi koncovými body kanálu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.WSHttpContextBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [\<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
