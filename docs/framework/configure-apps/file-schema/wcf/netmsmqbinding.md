---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: a315ec508b378d1a3ba0189b0867c7b6b61e34d2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398321"
---
# <a name="netmsmqbinding"></a>\<netMsmqBinding>
Definuje vazbu s frontou vhodnou pro komunikaci mezi počítači.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netMsmqBinding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxBufferPoolSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           poisonMessageHandling="Disabled/EnabledIfSupported"
           queueTransferProtocol="Native/Srmp/SrmpSecure"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           rejectAfterLastRetry="Boolean"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           timeToLive="TimeSpan"
           useActiveDirectory="Boolean"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/InfoCard" />
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`customDeadLetterQueue`|Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv pro jednotlivé aplikace, kde jsou umístěny zprávy, jejichž platnost vypršela nebo se nezdařil přenos nebo doručení.<br /><br /> Fronta nedoručených zpráv je frontou ve Správci fronty odesílající aplikace, jejichž doručení se nezdařilo.<br /><br /> Identifikátor URI, který je určen <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> parametrem, musí používat schéma NET. MSMQ.|  
|`deadLetterQueue`|<xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Hodnota určující, který typ fronty nedoručených zpráv se má použít, pokud existuje.<br /><br /> Fronta nedoručených zpráv je místo, kam se budou přenášet zprávy, které se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které `exactlyOnce` vyžadují ujištění (to znamená `exactlyOnce` , že atribut je `true`nastaven na hodnotu) se tento atribut standardně používá pro nedoručené transakční fronty v rámci systému MSMQ.<br /><br /> Pro zprávy, které nevyžadují žádné záruky, je tento atribut `null`nastaven na hodnotu.|  
|`durable`|Logická hodnota, která označuje, zda je zpráva ve frontě trvalá nebo nestálá. Trvalá zpráva se zachováním správce front dojde k chybě, zatímco nestálá zpráva. Nestálé zprávy jsou užitečné v případě, že aplikace vyžadují nižší latenci a můžou tolerovat občasné ztracené zprávy. `true`Pokud je `exactlyOnce` atribut nastaven na hodnotu, musí být zprávy trvalé. Výchozí hodnota je `true`.|  
|`exactlyOnce`|Logická hodnota, která určuje, zda každá zpráva zpracovávaná touto vazbou je dodávána pouze jednou. Odesílatel bude upozorněn na selhání doručení. Když `durable` je`false`tento atribut ignorován a zprávy se přenesou bez záruky doručení. Výchozí hodnota je `true`. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 8.|  
|`maxReceivedMessageSize`|Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček zpracovávaných touto vazbou. Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536. Cílem této velikosti zprávy je omezit vystavení útokům DOS (Denial of Service).|  
|`maxRetryCycles`|Celé číslo, které označuje počet opakovaných cyklů používaných funkcí detekce nepoškozených zpráv. Zpráva se zobrazí jako nepoškozená zpráva, když dojde k chybě všech pokusů o doručení všech cyklů. Výchozí hodnota je 3. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Požadovaný atribut. Řetězec, který obsahuje název konfigurace vazby. Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`QueueTransferProtocol`|Platná <xref:System.ServiceModel.QueueTransferProtocol> hodnota, která určuje přenos komunikačního kanálu ve frontě, který tato vazba používá. Služba MSMQ nepodporuje adresování služby Active Directory při použití protokolu SOAP Reliable Messaging Protocol. Proto byste neměli tento atribut nastavovat na `Srmp` nebo `Srmps` , pokud `useActiveDirectory` je atribut nastaven na `true`hodnotu.|  
|`receiveErrorHandling`|<xref:System.ServiceModel.ReceiveErrorHandling> Hodnota, která určuje, jak jsou zpracovávány nezpracované zprávy.|  
|`receiveRetryCount`|Celé číslo, které určuje maximální počet pokusů, kolikrát se správce fronty pokusí odeslat zprávu do fronty opakování.|  
|`receiveTimeout`|<xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`retryCycleDelay`|Hodnota TimeSpan, která určuje časovou prodlevu mezi opakovanými cykly při pokusu o doručení zprávy, která nemohla být doručena okamžitě. Hodnota definuje pouze minimální dobu čekání, protože skutečná čekací doba může být delší. Výchozí hodnota je 00:10:00. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|<xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`timeToLive`|Hodnota TimeSpan, která určuje, jak dlouho jsou zprávy platné, než vyprší jejich platnost, a umístí se do fronty nedoručených zpráv. Výchozí hodnota je 1,00:00:00.<br /><br /> Tento atribut je nastaven tak, aby bylo zajištěno, že zprávy citlivé na čas nejsou před zpracováním přijímajícími aplikacemi zastaraly. U zprávy ve frontě, kterou přijímající aplikace nespotřebovává v zadaném časovém intervalu, se říká, že platnost vypršela. Zprávy s vypršenou platností se odesílají do speciální fronty označované jako fronta nedoručených zpráv. Umístění fronty nedoručených zpráv je nastaveno s `DeadLetterQueue` atributem nebo na odpovídající výchozí hodnotu na základě ujištění.|  
|`usingActiveDirectory`|Logická hodnota, která určuje, zda mají být adresy front převedeny pomocí služby Active Directory.<br /><br /> Adresy front MSMQ se můžou skládat z názvů cest nebo názvů přímých formátů. S přímým názvem formátu MSMQ přeloží název počítače pomocí DNS, NetBIOS nebo IP adresy. V případě názvu cesty služba MSMQ překládá název počítače pomocí služby Active Directory.<br /><br /> Ve výchozím nastavení přenos ve frontě Windows Communication Foundation (WCF) převede identifikátor URI fronty zpráv na název přímého formátu. Nastavením `UseActiveDirectory` vlastnosti na hodnotu true může aplikace určit, že přenos ve frontě by měl přeložit název počítače pomocí služby Active Directory, nikoli DNS, NetBIOS nebo IP.|  
|`useMsmqTracing`|Logická hodnota určující, zda mají být zprávy zpracované touto vazbou sledovány. Výchozí hodnota je `false`. Je-li povoleno trasování, jsou vytvořeny zprávy sestavy a odesílány do fronty sestav pokaždé, když zpráva opustí nebo dorazí na počítač služby Řízení front zpráv.|  
|`useSourceJournal`|Logická hodnota, která určuje kopie zpráv zpracovaných touto vazbou, by měla být uložena ve zdrojovém deníku. Výchozí hodnota je `false`.<br /><br /> Aplikace ve frontě, které chtějí uchovávat záznam zpráv, které opustily odchozí fronty počítače, mohou kopírovat zprávy do fronty deníku. Jakmile zpráva opustí odchozí frontu a potvrzení, že byla zpráva přijata v cílovém počítači, bude uložena kopie zprávy ve frontě deníku systému odesílajícího počítače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<> zabezpečení](security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> vazeb](bindings.md)|Tento prvek obsahuje kolekci standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 `netMsmqBinding` Vazba poskytuje podporu pro řízení front využitím služby MSMQ (Microsoft Message Queuing) jako přenosu a umožňuje podporu volně vázaných aplikací, izolaci selhání, Vyrovnávání zatížení a odpojených operací. Diskuzi o těchto funkcích najdete v tématu [fronty ve službě WCF](../../../wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netMsmqBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 sourceJournal="true"
                 useMsmqTracing="true"
                 useActiveDirectory="true">
          <security>
            <message clientCredentialType="Windows" />
          </security>
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>
- [\<> vazby](../../../misc/binding.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
