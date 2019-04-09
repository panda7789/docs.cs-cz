---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: dc1af462222920c7b3c6b66c3822e7b2b326b244
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169816"
---
# <a name="netnamedpipebinding"></a>\<netNamedPipeBinding>
Definuje vazbu, která je zabezpečená, spolehlivá, optimalizovaná pro komunikaci mezi procesy dané stanice. Ve výchozím nastavení vygeneruje zásobník modulu runtime komunikace s WS-ReliableMessaging spolehlivosti, zabezpečení přenosu pro zabezpečení přenosu, pojmenované kanály pro doručování zpráv a kódování binární zprávy.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netNamedPipeBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|hostNameComparisonMode|Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.|  
|maxBufferPoolSize|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524,288 bajtů (512 * 1024). Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti. Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné. S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi. Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.|  
|maxBufferSize|Kladné celé číslo, které určuje maximální velikost v bajtech, vyrovnávací paměti používané k ukládání zpráv v paměti. Pokud vyrovnávací paměť je plná, zůstane nadbytečná data řadit v podkladové soketu, dokud znovu místnosti má vyrovnávací paměť. Tato hodnota nemůže být menší než `maxReceivedMessageSize` atribut. Výchozí hodnota je 65536. Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Celé číslo, které určuje maximální počet odchozí a příchozí připojení služby vytvořit/přijme. Příchozí a odchozí připojení se započítávají i samostatné limit specifikovaný pro tento atribut.<br /><br /> Příchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.<br /><br /> Odchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.<br /><br /> Výchozí hodnota je 10.|  
|maxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou. Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|name|Řetězec, který obsahuje konfigurační název vazby. Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|SendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|transactionFlow|Logická hodnota určující, zda vazba podporuje průchodu WS-transakce. Výchozí hodnota je `false`.|  
|transactionProtocol|Určuje protokol transakce, jenž má být použit s touto vazbou. Platné hodnoty jsou<br /><br /> -OleTransactions<br />– WS-AtomicTransactionOctober2004<br /><br /> Výchozí hodnota je OleTransactions. Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|A <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavek nebo odpověď.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje sadu standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 `NetNamedPipeBinding` Generuje runtime komunikačního balíku ve výchozím nastavení, která používá zabezpečení přenosu pojmenované kanály pro doručování zpráv a zprávy v binární kódování. Tato vazba je vhodné Windows Communication Foundation (WCF) poskytované systémem volbou pro komunikaci na počítači. Také podporuje transakce.  
  
 Výchozí konfigurace pro `NetNamedPipeBinding` se podobá konfiguraci poskytované `NetTcpBinding`, ale je jednodušší, protože implementace WCF je určená jenom pro použití na počítači a v důsledku toho nejsou zveřejněné méně funkcí. Nejdůležitější rozdíl je, že `securityMode` nastavení pouze nabídky `None` a `Transport` možnosti. Podpora protokolu SOAP zabezpečení není možné zahrnuté. Chování zabezpečení je možné konfigurovat pomocí volitelného `securityMode` atribut.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje netNamedPipeBinding vazbu, která poskytuje komunikaci mezi procesy ve stejném počítači. Pojmenované kanály napříč počítači nefungují.  
  
 Vazba je zadán v konfiguračních souborech pro klienta a služby. Typ vazby je zadán v `binding` atribut `<endpoint>` elementu. Pokud chcete konfiguraci vazby netNamedPipeBinding a některé z nastavení změnit, je nutné definovat konfiguraci vazby. Koncový bod musí odkazovat konfigurace vazby podle názvu pomocí `bindingConfiguration` atribut. V tomto příkladu má název konfigurace vazby Binding1.  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
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
        <binding closeTimeout="00:01:00"
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
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
