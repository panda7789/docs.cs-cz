---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 7a4bae0def6599ab577656e970abbe20dd10692f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778024"
---
# <a name="netmsmqbinding"></a>\<netMsmqBinding>
Definuje vazbu s frontou vhodnou pro komunikaci mezi počítači.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netMsmqBinding>  
  
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
|`closeTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`customDeadLetterQueue`|Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv jednotlivým aplikacím, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly, přenos nebo doručení.<br /><br /> Fronty nedoručených zpráv je do fronty v správce fronty odesílání žádosti o zprávy s vypršenou platností, které se nepodařilo doručit.<br /><br /> Identifikátor URI, který je určen <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musí používat schéma net.msmq.|  
|`deadLetterQueue`|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> hodnotu určující, jaký typ fronty nedoručených zpráv, pokud chcete použít, pokud existuje.<br /><br /> Fronty nedoručených zpráv je místo, kde budou přeneseny zprávy, které se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které vyžadují `exactlyOnce` assurance (to znamená, `exactlyOnce` atribut je nastaven na `true`), výchozí hodnota tohoto atributu celý systém transakční fronty nedoručených zpráv služby MSMQ.<br /><br /> Pro zprávy, které vyžadují žádné záruky, tento atribut výchozí `null`.|  
|`durable`|Logická hodnota určující, zda zpráva je trvalé nebo přechodné ve frontě. Zpráv trvalý odolává chybovému ukončení správce fronty, ale volatile zpráva nikoli. Volatile zprávy jsou užitečné, pokud aplikace vyžaduje nižší latenci a která tolerují občasné ztracené zprávy. Pokud `exactlyOnce` atribut je nastaven na `true`, zprávy musí být trvalý. Výchozí hodnota je `true`.|  
|`exactlyOnce`|Logická hodnota, která určuje, zda každá zpráva zpracované touto vazbou se doručí jenom jednou. Odesílatel budete pak informováni o selhání doručování. Když `durable` je `false`, tento atribut se ignoruje a bez záruky doručení přenosu zpráv. Výchozí hodnota je `true`. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 8.|  
|`maxReceivedMessageSize`|Kladné celé číslo, který definuje maximální velikost zprávy, v bajtech, včetně záhlaví, která je zpracována touto vazbou. Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536. Vázaný na velikost zprávy se má omezit vystavení útokům DOS (DoS).|  
|`maxRetryCycles`|Celé číslo určující počet cyklů opakování používat funkci zjišťování poison zpráv. Zpráva změní nezpracovatelná zpráva, pokud selže všechny pokusy o doručení všechny cyklů. Výchozí hodnota je 3. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Požadovaný atribut. Řetězec, který obsahuje konfigurační název vazby. Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`QueueTransferProtocol`|Platný <xref:System.ServiceModel.QueueTransferProtocol> hodnota, která určuje přenos zařazených do fronty komunikačního kanálu, který tato vazba používá. MSMQ Active Directory adresování při použití spolehlivé zasílání zpráv protokolu SOAP nepodporuje. Proto by neměl tento atribut nastavte na `Srmp` nebo `Srmps` při `useActiveDirectory` atribut je nastaven na `true`.|  
|`receiveErrorHandling`|A <xref:System.ServiceModel.ReceiveErrorHandling> hodnota, která určuje způsob zpracování poison a nondispatchable zprávy.|  
|`receiveRetryCount`|Celé číslo, které určuje maximální počet pokusů odeslání zprávy před přenosem do fronty opakování má pokusit správce fronty.|  
|`receiveTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`retryCycleDelay`|Časový interval hodnotu, která určuje časovou prodlevu mezi opakovanými cykly při pokusu o doručení zprávy, která nemohla být doručena okamžitě. Hodnota definuje jen minimální doba čekání, protože skutečná čekací doba může být déle. Výchozí hodnota je 00:10:00. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`timeToLive`|Časový interval hodnotu, která určuje, jak dlouho zprávy jsou platné, před jejich platnost a zařadí do fronty nedoručených zpráv. Výchozí hodnota je 1.00:00:00.<br /><br /> Tento atribut je nastaven na Ujistěte se, že časově zprávy není zastaralá předtím, než se zpracovávají přijímajícími aplikacemi. Zprávy ve frontě, které se přijímající aplikací v rámci zadaného časového intervalu se říká, že platnost. Zprávy s vypršenou platností se odesílají do speciální fronty názvem fronty nedoručených zpráv. Umístění fronty nedoručených zpráv nastavena `DeadLetterQueue` atribut nebo na vhodné výchozí nastavení, v závislosti na záruky.|  
|`usingActiveDirectory`|Logická hodnota určující, pokud mají být adresy fronty převedeny pomocí služby Active Directory.<br /><br /> Adresy služby MSMQ se může skládat z názvů cesty nebo názvů v přímém formátu. Pomocí přímého názvu formátu MSMQ přeloží název počítače pomocí DNS, rozhraní NetBIOS nebo IP. Služby MSMQ s názvem cesty, překládá název počítače pomocí služby Active Directory.<br /><br /> Ve výchozím nastavení Windows Communication Foundation (WCF) zařazených do fronty přenosu převede identifikátor URI pro název formátu přímé fronty zpráv. Tím, že nastavíte `UseActiveDirectory` vlastnost na hodnotu true, aplikace můžete určit, že zařazených do fronty přenosu by měla vyřešit název počítače pomocí služby Active Directory místo DNS, rozhraní NetBIOS nebo IP.|  
|`useMsmqTracing`|Logická hodnota, která určuje, zda zprávy zpracované touto vazbou mají být vyvolány. Výchozí hodnota je `false`. Když je povoleno trasování, zprávy se vytváří a odesílají do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítači služby Řízení front zpráv.|  
|`useSourceJournal`|Logická hodnota určující kopie zpráv zpracovaných touto vazbou uskladněny ve deníku zdroje. Výchozí hodnota je `false`.<br /><br /> Ve frontě aplikace, které chcete sledovat zpráv, které ještě zbývá fronty odesílaných zpráv počítače můžete zkopírovat zprávy do fronty deníku. Jakmile opustí zprávu fronty odesílaných zpráv a přijetí potvrzení, že byla přijata zpráva v cílovém počítači, kopie zprávy, zůstane ve frontě deníků odesílající počítač systému.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje sadu standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 `netMsmqBinding` Poskytuje podporu pro službu Řízení front s využitím Microsoft Message Queuing (MSMQ) jako přenosového mechanismu a umožňuje podporu pro vyrovnání a odpojených operace načítání volně propojených aplikací, izolaci selhání vazby. Informace o těchto funkcích naleznete v tématu [fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
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
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
