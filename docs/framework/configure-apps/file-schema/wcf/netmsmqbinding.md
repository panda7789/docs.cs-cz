---
title: '&lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: d4d28a799acecd335d8155a7ae67b6365b3f0023
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751672"
---
# <a name="ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt;
Definuje vazbu zařazených do fronty vhodný pro komunikaci mezi počítači.  
  
 \<system.ServiceModel>  
\<vazby >  
\<– netMsmqBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>  
    <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxBufferPoolSize="Integer"  
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
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
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
          <security>  
                  <message    
                        algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/InfoCard "/>  
                  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding></netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`customDeadLetterQueue`|Identifikátor URI, která obsahuje umístění fronty nedoručených zpráv jednotlivých aplikací, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly přenos nebo doručení.<br /><br /> Fronta nedoručených zpráv je do fronty v správce front odeslání žádosti o zprávy s vypršenou platností, které se nepodařilo doručit.<br /><br /> Identifikátor URI, která je zadána <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musí používat schéma net.msmq.|  
|`deadLetterQueue`|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> hodnota, která určuje typu frontu nedoručených zpráv, pokud chcete použít, pokud existuje.<br /><br /> Frontu nedoručených zpráv je místem, kde budou přeneseny zprávy, které se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které vyžadují `exactlyOnce` záruku (to znamená `exactlyOnce` je atribut nastaven na `true`), použije se výchozí hodnota tohoto atributu do fronty transakcí nedoručených zpráv systémové služby MSMQ.<br /><br /> Pro zprávy, které vyžadují žádné záruky, tento atribut výchozí `null`.|  
|`durable`|Logická hodnota, která určuje, zda je zpráva trvalé nebo přechodné ve frontě. Trvanlivý zprávu odolává fronty manager havárie, při volatile zpráva neexistuje. Volatile zprávy jsou užitečné, když aplikace vyžadují nižší latenci a tolerovat příležitostně ztrátě zpráv. Pokud `exactlyOnce` je atribut nastaven na `true`, zprávy musí být odolné. Výchozí hodnota je `true`.|  
|`exactlyOnce`|Logická hodnota, která určuje, zda každá zpráva zpracovávané touto vazbou doručuje pouze jednou. Odesílatel pak budou informováni o selhání doručení. Když `durable` je `false`, tento atribut je ignorován a přenosu zpráv bez záruky doručení. Výchozí hodnota je `true`. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 8.|  
|`maxReceivedMessageSize`|Kladné celé číslo, který definuje maximální velikost zprávy, v bajtech, včetně hlavičky, které je zpracovávané touto vazbou. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536. Vázaný na velikost zprávy se má omezit riziko napadení útok na dostupnost služby (DoS).|  
|`maxRetryCycles`|Celé číslo určující počet cyklů opakování používané funkce rozpoznávání poison zprávy. Zprávu stane nezpracovatelná zpráva, pokud se nezdaří všechny pokusy o doručení všech cyklů. Výchozí hodnota je 3. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Požadovaný atribut. Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`QueueTransferProtocol`|Platná <xref:System.ServiceModel.QueueTransferProtocol> hodnotu, která určuje přenosu kanál komunikace ve frontě, která používá tuto vazbu. MSMQ nepodporuje služby Active Directory adresování při použití protokolu SOAP spolehlivého zasílání zpráv. Proto by nemělo nastavte tento atribut na `Srmp` nebo `Srmps` při `u``seActiveDirectory` je nastavena na hodnotu `true`.|  
|`receiveErrorHandling`|A <xref:System.ServiceModel.ReceiveErrorHandling> hodnotu, která určuje způsob zpracování zprávy poison a nondispatchable.|  
|`receiveRetryCount`|Celé číslo, které určuje maximální počet nezdařených pokusů o správce front mají pokusit o odeslání zprávy před přenosu do fronty opakování.|  
|`receiveTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`retryCycleDelay`|Hodnota časového rozpětí, který určuje prodlevu mezi opakování cyklů při pokusu o doručení zprávy, která nelze doručit okamžitě. Hodnota definuje jen minimální doba čekání, protože skutečná čekací dobu může být delší. Výchozí hodnota je 00:10:00. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`timeToLive`|Hodnota časového rozpětí, která určuje, jak dlouho zprávy jsou platné předtím, než se platnost a zařazena do fronty nedoručených zpráv. Výchozí hodnota je 1.00:00:00.<br /><br /> Tento atribut nastavený zajistit, že zprávy dobou nepřestali být zastaralé dříve, než je přijímací aplikace. Zprávy ve frontě, který není přijímající aplikace v rámci zadaného časového intervalu říká, že je mít skončenou platnost. Zprávy s vypršenou platností se odesílají do speciální fronty názvem fronty nedoručených zpráv. Umístění fronty nedoručených zpráv nastavena `DeadLetterQueue` atribut, nebo odpovídající výchozí, aby na základě záruky.|  
|`usingActiveDirectory`|Logická hodnota, která určuje, pokud mají být převedeny fronty adresy pomocí služby Active Directory.<br /><br /> MSMQ fronty adresy se může skládat z názvů cestu nebo přímé formátu. Pomocí přímého názvu formátu vyřeší MSMQ názvu počítače pomocí DNS, pro rozhraní NetBIOS nebo IP. S názvem cesty vyřeší MSMQ názvu počítače pomocí služby Active Directory.<br /><br /> Ve výchozím nastavení Windows Communication Foundation (WCF) zařazených do fronty přenosu převede identifikátor URI k přímého názvu formátu fronty zpráv. Nastavením `UseActiveDirectory` vlastnost na hodnotu true, aplikace můžete určit, že zařazených do fronty přenosu by měla vyřešit název počítače pomocí služby Active Directory místo DNS, pro rozhraní NetBIOS nebo IP.|  
|`useMsmqTracing`|Logická hodnota, která určuje, zda zprávy zpracovávané touto vazbou má trasovat. Výchozí hodnota je `false`. Pokud je povoleno sledování, sestava zprávy se vytváří a odesílají do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítači služby Řízení front zpráv.|  
|`useSourceJournal`|Logická hodnota, která určuje kopie zprávy zpracovávané touto vazbou by měl být uložen v deníku zdroje. Výchozí hodnota je `false`.<br /><br /> Ve frontě aplikací, které chcete zachovat záznam zprávy, které mají zbývající počítače fronty odesílaných zpráv můžete zkopírovat do deníku fronty zpráv. Jakmile zprávu opustí fronty odesílaných zpráv a je obdržena potvrzení, že zpráva byla přijata v cílovém počítači, je udržováno kopie zprávy ve frontě deníku odesílající počítač systému.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `netMsmqBinding` Vazby poskytuje podporu pro službu Řízení front s využitím Microsoft řízení front zpráv (MSMQ) jako přenosového mechanismu a umožňuje podporu pro volně párované aplikace, izolace selhání načtení operace vyrovnání a odpojené. Informace o těchto funkcích, najdete v části [fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
           <netMsmqBinding>  
                <binding   
                         closeTimeout="00:00:10"   
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
            </netMsmqBinding>  
    </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
