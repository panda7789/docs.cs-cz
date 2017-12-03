---
title: "&lt;– wsDualHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d7a6cd2d1a5028463d6d9b4b492c88707f08145
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltwsdualhttpbindinggt"></a>&lt;– wsDualHttpBinding&gt;
Definuje vazbu zabezpečené, spolehlivé a vzájemná spolupráce, který je vhodný pro služby duplexní kontrakty nebo komunikaci prostřednictvím protokolu SOAP zprostředkovatelů.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<– wsDualHttpBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|bypassProxyOnLocal|Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy. Výchozí hodnota je `false`.|  
|clientBaseAddress|Identifikátor URI, který nastaví základní adresu, která klient naslouchá odpovědí na zprávy ze služby. -Li zadána, tato adresa (plus za channelGUID) se používá k naslouchání. Pokud hodnotu nezadáte, vygeneruje se způsobem specifické pro přenos základní adresu klienta. Výchozí hodnota je `null`.|  
|Intervalu|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|hostnameComparisonMode|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 * 1024). Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|MaxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|messageEncoding|Definuje kodér použitá ke kódování zprávy. Platné hodnoty patří:<br /><br /> -Text: Pomocí kodéru text zprávy.<br />-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).<br />-Výchozí hodnota je Text.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useDefaultWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|sendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|textEncoding|Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby. Platné hodnoty patří:<br /><br /> -BigEndianUnicode: Unicode BigEndian kódování.<br />-Unicode: 16bitové kódování.<br />-UTF8: kódování 8bitové<br /><br /> Výchozí hodnota je UTF8. Tento atribut je typu <xref:System.Text.Encoding>.|  
|transactionFlow|Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|useDefaultWebProxy|Logická hodnota, která určuje, zda je použít server proxy protokolu HTTP pro automatickou konfiguraci systému. Adresa proxy serveru musí být `null` (to znamená, že není nastavena) Pokud tento atribut je `true`. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Určuje, pokud jsou určeny spolehlivé relace mezi koncovými body kanálu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `WSDualHttpBinding` Poskytuje stejné podporu pro webové služby protokoly, jako `WSHttpBinding`, ale pro použití s duplexní kontrakty. `WSDualHttpBinding`pouze podporuje zabezpečení protokolu SOAP a vyžaduje spolehlivé zasílání zpráv. Tato vazba vyžaduje, aby klient veřejné identifikátor URI, který poskytuje koncový bod zpětného volání pro službu. To zajišťuje `clientBaseAddress` atribut. Duální vazbu zpřístupní IP adresu klienta ke službě. Klient musí použít zabezpečení zajistit, že pouze připojení k službám ho vztahy důvěryhodnosti.  
  
 Tato vazba umožňuje spolehlivě komunikovat prostřednictvím jednoho nebo více zprostředkovatelů protokolu SOAP.  
  
 Ve výchozím nastavení, vygeneruje tuto vazbu runtime zásobníku pomocí protokolu WS-ReliableMessaging pro spolehlivost, WS-zabezpečení pro zabezpečení zpráv a ověřování protokolu HTTP pro doručování zpráv a kódování zpráv Text/XML.  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
