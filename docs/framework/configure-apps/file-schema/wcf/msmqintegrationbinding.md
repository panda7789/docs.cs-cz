---
title: <msmqIntegrationBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: 95942e9818eccc018c123148949c6f2dee4fa6e0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736622"
---
# <a name="msmqintegrationbinding"></a>\<msmqIntegrationBinding >
Definuje vazbu, která poskytuje podporu fronty směrováním zpráv prostřednictvím služby MSMQ.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<msmqIntegrationBinding >**  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|closeTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|customDeadLetterQueue|Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv pro jednotlivé aplikace, kde jsou umístěny zprávy, jejichž platnost vypršela nebo se nezdařil přenos nebo doručení.<br /><br /> Fronta nedoručených zpráv je frontou ve Správci fronty odesílající aplikace, jejichž doručení se nezdařilo.<br /><br /> Identifikátor URI, který je určen <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>, musí používat schéma NET. MSMQ.|  
|deadLetterQueue|<xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>. Value určující typ fronty nedoručených zpráv, která se má použít, pokud existuje<br /><br /> Fronta nedoručených zpráv je umístění, do kterého se přenesou zprávy, které se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které vyžadují zabezpečení exactlyOnce (tj. `exactlyOnce` atribut je nastaven na `true`), tento atribut ve výchozím nastavení odpovídá frontě nedoručených transakcí transakčního systému v rámci služby MSMQ.<br /><br /> U zpráv, které nevyžadují žádné záruky, je tento atribut standardně `null`.|  
|dočasných|Logická hodnota, která označuje, zda je zpráva ve frontě trvalá nebo nestálá. Trvalá zpráva se zachováním správce front dojde k chybě, zatímco nestálá zpráva. Nestálé zprávy jsou užitečné v případě, že aplikace vyžadují nižší latenci a můžou tolerovat občasné ztracené zprávy. Pokud je atribut `exactlyOnce` nastaven na hodnotu `true`, musí být zprávy trvalé. Výchozí hodnota je `true`.|  
|Třída|Logická hodnota, která označuje, zda je každá zpráva doručena pouze jednou. Odesílatel bude upozorněn na selhání doručení. Pokud je `false``durable`, tento atribut se ignoruje a zprávy se přenesou bez záruky doručení. Výchozí hodnota je `true`. Další informace najdete v tématu <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček zpracovávaných touto vazbou. Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536. Cílem této velikosti zprávy je omezit vystavení útokům DOS (Denial of Service).|  
|maxRetryCycles|Celé číslo, které označuje počet opakovaných cyklů používaných funkcí detekce nepoškozených zpráv. Zpráva se zobrazí jako nepoškozená zpráva, když dojde k chybě všech pokusů o doručení všech cyklů. Výchozí hodnota je 2. Další informace najdete v tématu <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|receiveErrorHandling|Hodnota <xref:System.ServiceModel.ReceiveErrorHandling>, která určuje, jak jsou zpracovávány nezpracované zprávy.|  
|receiveRetryCount|Celé číslo, které určuje maximální počet okamžitých opakovaných pokusů, by se měl správce fronty pokusit, pokud se nezdaří přenos zprávy z fronty aplikace do aplikace.<br /><br /> Pokud jste dosáhli maximálního počtu pokusů o doručení a zpráva k ní nepoužívá aplikace, pošle se zpráva do fronty opakovaných pokusů o opětovné doručení v pozdějším čase. Doba před přenosem zprávy zpět do odesílající fronty je řízena `retryCycleDelay`. Pokud opakované cykly dosáhnou `maxRetryCycles` hodnoty, zpráva se buď pošle do fronty nepotvrzené zprávy, nebo se pošle zpět do odesilatele negativní potvrzení.|  
|receiveTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|receiveContextEnabled|Logická hodnota, která určuje, zda je povolen kontext příjmu pro zpracování zpráv ve frontách. Pokud je tato možnost nastavená na `true`, může služba "prohlížet" zprávy ve frontě, aby ji bylo možné začít zpracovávat, a pokud se něco nepovede a vyvolá se výjimka, zůstane ve frontě. Služba může také "uzamknout" zprávy, aby bylo možné opakovat zpracování později v pozdějším časovém bodě. ReceiveContext poskytuje mechanismus pro "dokončování" zprávu po zpracování, aby ji bylo možné odebrat z fronty. Zprávy již nejsou čteny a znovu zapisovány do front přes síť a jednotlivé zprávy nejsou během zpracování skákající napříč různými instancemi služby.|  
|retryCycleDelay|Hodnota TimeSpan, která určuje časovou prodlevu mezi opakovanými cykly při pokusu o doručení zprávy, která nemohla být doručena okamžitě. Hodnota definuje pouze minimální dobu čekání, protože skutečná čekací doba může být delší. Výchozí hodnota je 00:30:00. Další informace najdete v tématu <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|SendTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|serializationFormat|Definuje formát použitý pro serializaci těla zprávy. Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Hodnota TimeSpan, která určuje, jak dlouho jsou zprávy platné, než vyprší jejich platnost, a umístí se do fronty nedoručených zpráv. Výchozí hodnota je 1,00:00:00.<br /><br /> Tento atribut je nastaven tak, aby bylo zajištěno, že zprávy citlivé na čas nejsou před zpracováním přijímajícími aplikacemi zastaraly. U zprávy ve frontě, kterou přijímající aplikace nespotřebovává v zadaném časovém intervalu, se říká, že platnost vypršela. Zprávy s vypršenou platností se odesílají do speciální fronty označované jako fronta nedoručených zpráv. Umístění fronty nedoručených zpráv je nastaveno s atributem `DeadLetterQueue` nebo odpovídajícím výchozím nastavením na základě ujištění.|  
|useMsmqTracing|Logická hodnota určující, zda mají být zprávy zpracované touto vazbou sledovány. Výchozí hodnota je `false`. Je-li povoleno trasování, jsou vytvořeny zprávy sestavy a odesílány do fronty sestav pokaždé, když zpráva opustí nebo dorazí na počítač služby Řízení front zpráv.|  
|useSourceJournal|Logická hodnota, která určuje kopie zpráv zpracovaných touto vazbou, by měla být uložena ve zdrojovém deníku. Výchozí hodnota je `false`.<br /><br /> Aplikace ve frontě, které chtějí uchovávat záznam zpráv, které opustily odchozí fronty počítače, mohou kopírovat zprávy do fronty deníku. Jakmile zpráva opustí odchozí frontu a potvrzení, že byla zpráva přijata v cílovém počítači, bude uložena kopie zprávy ve frontě deníku systému odesílajícího počítače.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Přidělen  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|XML|Formát XML|  
|binární|Binární formát|  
|ActiveX|Formát ActiveX|  
|ByteArray|Serializace objektu na pole bajtů.|  
|Stream|Tělo formátované jako datový proud|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-msmqintegrationbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazby\<](bindings.md)|Tento prvek obsahuje kolekci standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek vazby lze použít k povolení aplikace Windows Communication Foundation (WCF) k posílání zpráv a přijímání zpráv z existujících aplikací služby MSMQ, které používají rozhraní API modelu COM, služby MSMQ Native, nebo typů definovaných v oboru názvů <xref:System.Messaging?displayProperty=nameWithType>, který můžete použít. Tento prvek konfigurace určuje způsoby, jak adresovat frontu, převádět záruky, zda musí být zprávy uloženy trvale a jakým způsobem by měly být zprávy chráněny a ověřeny. Další informace najdete v tématu [Postup: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
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
- [vazba \<](bindings.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
