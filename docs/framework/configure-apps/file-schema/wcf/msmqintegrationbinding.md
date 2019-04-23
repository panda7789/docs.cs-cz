---
title: <msmqIntegrationBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: 4960740af9637a1743dc86965d7831b76828e58a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130036"
---
# <a name="msmqintegrationbinding"></a>\<msmqIntegrationBinding>
Definuje vazbu, která podporuje řazení do fronty pomocí směrování zpráv prostřednictvím služby MSMQ.  
  
 \<system.ServiceModel>  
\<vazby >  
msmqIntegrationBinding  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<msmqIntegrationBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveContextEnabled="Boolean"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
           timeToLive="TimeSpan"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|customDeadLetterQueue|Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv jednotlivým aplikacím, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly, přenos nebo doručení.<br /><br /> Fronty nedoručených zpráv je do fronty v správce fronty odesílání žádosti o zprávy s vypršenou platností, které se nepodařilo doručit.<br /><br /> Identifikátor URI, který je určen <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musí používat schéma net.msmq.|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>. hodnotu určující typ fronty nedoručených zpráv, pokud chcete použít, pokud existuje<br /><br /> Fronty nedoručených zpráv je umístění, zprávy, které se nepodařilo doručit do aplikace se přesunou.<br /><br /> Pro zprávy, které vyžadují záruky exactlyOnce (to znamená, `exactlyOnce` atribut je nastaven na `true`), výchozí hodnota tohoto atributu celý systém transakční fronty nedoručených zpráv služby MSMQ.<br /><br /> Pro zprávy, které vyžadují žádné záruky, tento atribut výchozí `null`.|  
|trvalý|Logická hodnota určující, zda zpráva je trvalé nebo přechodné ve frontě. Zpráv trvalý odolává chybovému ukončení správce fronty, ale volatile zpráva nikoli. Volatile zprávy jsou užitečné, pokud aplikace vyžaduje nižší latenci a která tolerují občasné ztracené zprávy. Pokud `exactlyOnce` atribut je nastaven na `true`, zprávy musí být trvalý. Výchozí hodnota je `true`.|  
|exactlyOnce|Logická hodnota, která určuje, zda každá zpráva se doručí jenom jednou. Odesílatel budete pak informováni o selhání doručování. Když `durable` je `false`, tento atribut se ignoruje a bez záruky doručení přenosu zpráv. Výchozí hodnota je `true`. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Kladné celé číslo, který definuje maximální velikost zprávy, v bajtech, včetně záhlaví, která je zpracována touto vazbou. Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536. Vázaný na velikost zprávy se má omezit vystavení útokům DOS (DoS).|  
|maxRetryCycles|Celé číslo určující počet cyklů opakování používat funkci zjišťování poison zpráv. Zpráva změní nezpracovatelná zpráva, pokud selže všechny pokusy o doručení všechny cyklů. Výchozí hodnota je 2. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Řetězec, který obsahuje konfigurační název vazby. Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|receiveErrorHandling|A <xref:System.ServiceModel.ReceiveErrorHandling> hodnota, která určuje způsob zpracování poison a nondispatchable zprávy.|  
|receiveRetryCount|Celé číslo, které určuje maximální počet okamžité opakování správce fronty snažit, pokud selže přenos zprávy z fronty aplikace do aplikace.<br /><br /> Pokud je dosažen maximální počet pokusů o doručení a zpráva není přistupuje aplikace, pak zpráva je odeslána do fronty opakování pro opakované dodání později. Množství času, než se přenáší zprávy zpět do fronty odesílání se řídí `retryCycleDelay`. Pokud cyklů opakování dosahu `maxRetryCycles` hodnotu, pak buď je zpráva odeslána do fronty zpráv poison nebo negativní potvrzení budou odeslána zpět do odesílatele.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|receiveContextEnabled|Logická hodnota, která určuje, pokud kontextu přijetí pro zpracování zpráv ve frontách je povolená. Pokud je nastavené na `true`, služba může "náhled" zprávu ve frontě a spustit, zpracování, a pokud se něco pokazí, a je vyvolána výjimka, zůstane ve frontě. Služby můžete také "zamknout" zprávy, aby bylo možné opakovat zpracování později v čase. Kontext ReceiveContext poskytuje mechanismus pro "dokončení" zprávu po zpracování, můžete ho odebrat z fronty. Zprávy již probíhá čtení a zápis znovu do fronty v síti, a jednotlivé zprávy nejsou skákání napříč instancemi jinou službu během zpracování.|  
|retryCycleDelay|Časový interval hodnotu, která určuje časovou prodlevu mezi opakovanými cykly při pokusu o doručení zprávy, která nemohla být doručena okamžitě. Hodnota definuje jen minimální doba čekání, protože skutečná čekací doba může být déle. Výchozí hodnota je 00:30:00. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|SendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|třídu serializationFormat|Definuje formát použitý pro serializaci textu zprávy. Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Časový interval hodnotu, která určuje, jak dlouho zprávy jsou platné, před jejich platnost a zařadí do fronty nedoručených zpráv. Výchozí hodnota je 1.00:00:00.<br /><br /> Tento atribut je nastaven na Ujistěte se, že časově zprávy není zastaralá předtím, než se zpracovávají přijímajícími aplikacemi. Zprávy ve frontě, které se přijímající aplikací v rámci zadaného časového intervalu se říká, že platnost. Zprávy s vypršenou platností se odesílají do speciální fronty názvem fronty nedoručených zpráv. Umístění fronty nedoručených zpráv nastavena `DeadLetterQueue` atribut nebo na vhodné výchozí nastavení, v závislosti na záruky.|  
|useMsmqTracing|Logická hodnota, která určuje, zda zprávy zpracované touto vazbou mají být vyvolány. Výchozí hodnota je `false`. Když je povoleno trasování, zprávy se vytváří a odesílají do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítači služby Řízení front zpráv.|  
|useSourceJournal|Logická hodnota určující kopie zpráv zpracovaných touto vazbou uskladněny ve deníku zdroje. Výchozí hodnota je `false`.<br /><br /> Ve frontě aplikace, které chcete sledovat zpráv, které ještě zbývá fronty odesílaných zpráv počítače můžete zkopírovat zprávy do fronty deníku. Jakmile opustí zprávu fronty odesílaných zpráv a přijetí potvrzení, že byla přijata zpráva v cílovém počítači, kopie zprávy, zůstane ve frontě deníků odesílající počítač systému.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|XML|Formát XML|  
|binární|Binární formát|  
|ActiveX|Formát ActiveX|  
|ByteArray|Serializuje objekt na pole bajtů.|  
|Stream|Jako datový proud ve formátu textu|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje sadu standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element vazby slouží k povolení aplikace Windows Communication Foundation (WCF) k odesílání a příjem zpráv z existujících aplikací služby MSMQ, které používají modelu COM, nativní rozhraní API služby MSMQ nebo typy definované v <xref:System.Messaging?displayProperty=nameWithType> obor názvů je můžete použít tento prvek konfigurace k určení způsoby, jak vyřešit fronty přenosu záruky, zda zprávy musí být trvale uložen a jak by měl chráněný a ověření zprávy. Další informace najdete v tématu [jak: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <msmqIntegrationBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxImmediateRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 useSourceJournal="true"
                 useMsmqTracing="true"
                 serializationFormat="Binary">
          <security mode="None" />
        </binding>
      </msmqIntegrationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
