---
title: '&lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd11c1381de3d2c965e884ee2d43b8a0c08063bb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltnetnamedpipebindinggt"></a>&lt;netNamedPipeBinding&gt;
Definuje vazbu, která je zabezpečená, spolehlivé, optimalizované pro na počítač křížové proces komunikace. Ve výchozím nastavení vygeneruje zásobníku runtime komunikaci pomocí protokolu WS-ReliableMessaging pro spolehlivost, zabezpečení přenosu pro zabezpečení přenosu, pojmenované kanály pro doručování zpráv a zprávy v binární kódování.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netNamedPipeBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netNamedPipeBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"   
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"  
      transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"  
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
      <security mode="None/Transport">  
            <transport  protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Intervalu|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|hostnameComparisonMode|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI. Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele. Výchozí hodnota je `StrongWildcard`, který ignoruje název hostitele se shodují.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 * 1024). Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|maxBufferSize|Kladné celé číslo, které určuje maximální velikost v bajtech vyrovnávací paměti používané k uložení zpráv v paměti. Pokud vyrovnávací paměť je plná, zůstane nadbytečná data v podkladové soketu, dokud znovu místnosti má vyrovnávací paměť. Hodnota nesmí být menší než `maxReceivedMessageSize` atribut. Výchozí hodnota je 65536. Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Celé číslo, které určuje maximální počet odchozí a příchozí připojení služby bude vytvoření/přijmout. Příchozí a odchozí připojení, se počítají oproti samostatné limitu určeného tento atribut.<br /><br /> Příchozí připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.<br /><br /> Odchozí připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.<br /><br /> Výchozí hodnota je 10.|  
|MaxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|sendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|transactionFlow|Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|transactionProtocol|Určuje protokol transakce, který se má použít s touto vazbou. Platné hodnoty jsou<br /><br /> -OleTransactions<br />-   WS-AtomicTransactionOctober2004<br /><br /> Výchozí hodnota je OleTransactions. Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|A <xref:System.ServiceModel.TransferMode> hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `NetNamedPipeBinding` Generuje běhu komunikačního balíku ve výchozím nastavení, která používá zabezpečení přenosu pojmenované kanály pro doručování zpráv a zprávy v binární kódování. Tato vazba je vhodné Windows Communication Foundation (WCF) poskytované systémem volbou pro komunikaci ve počítače. Také podporuje transakce.  
  
 Výchozí konfiguraci pro `NetNamedPipeBinding` je podobná konfigurace poskytované `NetTcpBinding`, ale je jednodušší, protože implementace WCF je určená jenom pro použití ve počítač a v důsledku toho jsou méně zveřejněné funkce. Nejdůležitější rozdíl je, že `securityMode` nastavení pouze nabídky `None` a `Transport` možnosti. Podpora protokolu SOAP zabezpečení není zahrnuta možnost. Chování zabezpečení je možné konfigurovat pomocí volitelné `securityMode` atribut.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje – netNamedPipeBinding vazby, která poskytuje komunikaci mezi procesy ve stejném počítači. Pojmenované kanály nefungují mezi počítači.  
  
 Vazba je zadána v konfiguračních souborech pro klienta a služby. Typ vazby je zadán v `binding` atribut `<endpoint>` elementu. Pokud chcete nakonfigurovat – netNamedPipeBinding vazby a některá z jeho nastavení změnit, je nutné zadat konfiguraci vazby. Koncový bod musí odkazovat Konfigurace vazeb podle názvu s `bindingConfiguration` atribut. V tomto příkladu je vazba konfigurace s názvem Binding1.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->  
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
                  binding="netNamedPipeBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <netNamedPipeBinding>  
        <binding   
                 closeTimeout="00:01:00"  
                 openTimeout="00:01:00"   
                 receiveTimeout="00:10:00"   
                 sendTimeout="00:01:00"  
                 transactionFlow="false"   
                 transferMode="Buffered"   
                 transactionProtocol="OleTransactions"  
                 hostNameComparisonMode="StrongWildcard"   
                 maxBufferPoolSize="524288"  
                 maxBufferSize="65536"   
                 maxConnections="10"   
                 maxReceivedMessageSize="65536">  
          <security mode="Transport">  
            <transport protectionLevel="EncryptAndSign" />  
          </security>  
        </binding>  
      </netNamedPipeBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)
