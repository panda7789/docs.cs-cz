---
title: '&lt;netTcpBinding&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 057baf6d18cba61c0ceeb7d5152edcf082392310
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="ltnettcpbindinggt"></a>&lt;netTcpBinding&gt;
Určuje bezpečné, spolehlivé a optimalizované vazbu vhodný pro komunikaci mezi počítači. Ve výchozím nastavení vygeneruje zásobníku runtime komunikace s zabezpečení systému Windows pro zabezpečení zpráv a ověřování, TCP pro doručování zpráv a zprávy v binární kódování.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netTcpBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netTcpBinding>  
   <binding   
      closeTimeout="TimeSpan"  
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
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="None/Transport/Message/Both">  
            <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                defaultProtectionLevel="None/Sign/EncryptAndSign"   
algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
            <transport clientCredentialType="None/Windows/Certificate"  
                protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Intervalu|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|hostnameComparisonMode|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI. Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele. Výchozí hodnota je `StrongWildcard`, který ignoruje název hostitele se shodují.|  
|listenBacklog|Kladné celé číslo, které určuje maximální počet kanálů čekání třeba přijmout na naslouchací proces. Připojení překračující tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit. `connectionTimeout` Atribut omezuje čas klient čekat, než se připojený. teprve potom vyvolání k výjimce připojení. Výchozí hodnota je 10.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 512 * 1024 bajtů. Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|maxBufferSize|Kladné celé číslo, které určuje maximální velikost v bajtech vyrovnávací paměti používané k uložení zpráv v paměti.<br /><br /> Pokud `transferMode` atribut se rovná `Buffered`, tento atribut musí být roven `maxReceivedMessageSize` hodnota atributu.<br /><br /> Pokud `transferMode` atribut se rovná `Streamed`, tento atribut nemůže být více než `maxReceivedMessageSize` hodnotu atributu a by mělo obsahovat aspoň velikost záhlaví.<br /><br /> Výchozí hodnota je 65536. Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Celé číslo, které určuje maximální počet odchozí a příchozí připojení služby bude vytvoření/přijmout. Příchozí a odchozí připojení, se počítají oproti samostatné limitu určeného tento atribut.<br /><br /> Příchozí připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.<br /><br /> Odchozí připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.<br /><br /> Výchozí hodnota je 10.|  
|MaxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|portSharingEnabled|Logická hodnota, která určuje, zda je povoleno sdílení portů TCP pro toto připojení. Pokud je to `false`, každou vazbu používá vlastní výhradní port. Toto nastavení je relevantní pouze pro služby, protože klienti, nejsou nijak ovlivněny.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|sendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|transactionFlow|Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|transactionProtocol|Určuje protokol transakce, který se má použít s touto vazbou. Platné hodnoty jsou<br /><br /> -OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> Výchozí hodnota je OleTransactions. Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|A <xref:System.ServiceModel.TransferMode> hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Určuje, pokud jsou určeny spolehlivé relace mezi koncovými body kanálu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tato vazba generuje běhu komunikačního balíku ve výchozím nastavení, která používá zabezpečení přenosu, TCP pro doručování zpráv a zprávy v binární kódování. Tato vazba je odpovídající [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] poskytované systémem volbou pro komunikaci v síti Intranet.  
  
 Výchozí konfiguraci pro `netTcpBinding` je rychlejší než zadaná podle konfigurace `wsHttpBinding`, která je určena pouze pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]- na -[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] komunikace. Chování zabezpečení je možné konfigurovat pomocí volitelné `securityMode` atribut. Použití protokolu WS-ReliableMessaging je možné konfigurovat pomocí volitelné `reliableSessionEnabled` atribut. Ale spolehlivé zasílání zpráv ve výchozím nastavení vypnuté. Obecně platí, HTTP vazby poskytované systémem, jako `wsHttpBinding` a `basicHttpBinding` jsou nakonfigurovány, aby zapnout věcí ve výchozím nastavení, zatímco `netTcpBinding` vazby vypne věcí ve výchozím nastavení tak, že budete muset přihlásit k získat podporu, například pro jednu z WS-* specifikace. To znamená, že výchozí konfiguraci pro TCP je rychlejší při výměně zpráv mezi koncovými body než ty, které ve výchozím nastavení nakonfigurované pro vazby HTTP.  
  
## <a name="example"></a>Příklad  
 Vazba je zadána v konfiguračních souborech pro klienta a služby. Typ vazby je zadán v `binding` atribut `<endpoint>` elementu. Pokud chcete nakonfigurovat netTcpBinding vazby a některá z jeho nastavení změnit, je nutné definovat Konfigurace vazeb. Koncový bod musí odkazovat Konfigurace vazeb s `bindingConfiguration` atribut. V následujícím příkladu je definována konfiguraci vazby.  
  
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
    <binding   
             closeTimeout="00:01:00"  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
