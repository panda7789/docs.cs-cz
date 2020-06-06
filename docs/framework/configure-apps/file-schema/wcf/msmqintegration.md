---
title: <msmqIntegration>
ms.date: 03/30/2017
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
ms.openlocfilehash: 143557833457f379d410c3b71d87199a5b9e783b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738892"
---
# \<msmqIntegration>
Určuje přenos služby MSMQ pro vlastní vazbu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqIntegration>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<msmqIntegration customDeadLetterQueue="Uri"
                 deadLetterQueue="Custom/None/System"
                 durable="Boolean"
                 exactlyOnce="Boolean"
                 manualAddressing="Boolean"
                 maxBufferPoolSize="Integer"
                 maxImmediateRetries="Integer"
                 maxReceivedMessageSize="Integer"
                 maxRetryCycles="Integer"
                 rejectAfterLastRetry="Boolean"
                 retryCycleDelay="TimeSpan"
                 serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
                 timeToLive="TimeSpan"
                 useSourceJournal="Boolean"
                 useMsmqTracing="Boolean">
  <msmqTransportSecurity>
  </msmqTransportSecurity>
</msmqIntegration>
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customDeadLetterQueue|Identifikátor URI, který označuje umístění fronty nedoručených zpráv pro jednotlivé aplikace, ve které se přenáší zprávy, jejichž platnost vypršela nebo se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které vyžadují ujištění ExactlyOnce (tj. `exactlyOnce` je nastaveno na `true` ), je tento atribut ve výchozím nastavení nastaven na transakční frontu nedoručených transakčních zpráv v rámci služby MSMQ.<br /><br /> Pro zprávy, které nevyžadují žádné záruky (tj. `exactlyOnce` je nastaveno na `false` ), je tento atribut nastaven na hodnotu `null` .<br /><br /> Hodnota musí používat schéma NET. MSMQ. Výchozí formát je `null`.<br /><br /> Pokud `deadLetterQueue` je nastaven na `None` nebo `System` , pak tento atribut musí být nastaven na `null` . Pokud tento atribut není `null` , `deadLetterQueue` musí být nastaven na `Custom` .|  
|deadLetterQueue|Určuje typ fronty nedoručených zpráv, která se má použít.<br /><br /> Platné hodnoty zahrnují<br /><br /> -Custom: vlastní fronta nedoručených zpráv.<br />-None: nemusíte používat žádnou frontu nedoručených zpráv.<br />-System: použijte frontu nedoručených zpráv systému.<br /><br /> Tento atribut je typu DeadLetterQueue.|  
|dočasných|Logická hodnota určující, zda zprávy zpracované touto vazbou jsou trvalé nebo nestálé. Výchozí formát je `true`.<br /><br /> Trvalá zpráva se zachováním správce front dojde k chybě, zatímco nestálá zpráva. Nestálé zprávy jsou užitečné v případě, že aplikace vyžadují nižší latenci a můžou tolerovat občasné ztracené zprávy.<br /><br /> Pokud `exactlyOnce` je nastaveno na `true` , musí být zprávy trvalé.|  
|Třída|Logická hodnota, která určuje, zda zprávy zpracované touto vazbou budou přijímány právě jednou. Výchozí formát je `true`.<br /><br /> Zprávu je možné odeslat s ujištěním nebo bez ní. Záruka umožňuje aplikaci zajistit, aby se odeslaná zpráva dostala do fronty přijímání zpráv, nebo pokud nebyla, aplikace ji může zjistit čtením fronty nedoručených zpráv.<br /><br /> `exactlyOnce`, pokud je nastaveno na `true` , označuje, že služba MSMQ zajistí doručování odeslané zprávy do fronty příjmu zpráv pouze jednou a v případě, že doručení selže, zpráva je odeslána do fronty nedoručených zpráv.<br /><br /> Zprávy odeslané s `exactlyOnce` nastavením na `true` musí být odesílány pouze do transakční fronty.|  
|Jeho|Logická hodnota, která umožňuje uživateli převzít kontrolu nad adresováním zpráv. Tato vlastnost se obvykle používá ve scénářích směrovačů, kde aplikace určuje, do kterého jednoho z několika míst má poslat zprávu.<br /><br /> Když nastavíte na `true` , kanál předpokládá, že zpráva již byla adresována a do ní nepřidá žádné další informace. Uživatel pak může každou zprávu adresovat jednotlivě.<br /><br /> Když je nastaveno na `false` , výchozí mechanismus adresování Windows Communication Foundation (WCF) automaticky vytvoří adresy pro všechny zprávy.<br /><br /> Výchozí formát je `false`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti. Výchozí hodnota je 524288.<br /><br /> Mnoho částí služby WCF používá vyrovnávací paměti. Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu. Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.|  
|maxImmediateRetries|Celé číslo, které určuje maximální počet okamžitých opakovaných pokusů o zprávu, která je čtena z fronty aplikace. Výchozí hodnota je 5.<br /><br /> Pokud je proveden pokus o maximální počet okamžitých opakovaných pokusů o zprávu a zpráva není aplikací spotřebována, zpráva je odeslána do fronty opakovaných pokusů o opakování v pozdějším časovém bodě. Pokud nejsou zadány žádné cykly opakování, zprávy jsou buď odesílány do fronty nezpracovatelných zpráv, nebo se do odesilatele pošle negativní potvrzení.|  
|maxReceivedMessageSize|Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně záhlaví. Odesílatel zprávy obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|maxRetryCycles|Celé číslo, které určuje maximální počet opakovaných cyklů pro pokus o doručení zpráv do přijímající aplikace. Výchozí formát je <xref:System.Int32.MaxValue>.<br /><br /> Jeden cyklus opakování se pokusí o doručení zprávy do aplikace zadaného počtu opakování. Počet pokusů, které provedete, je nastaven `maxImmediateRetries` atributem. Pokud aplikace nedokáže tuto zprávu spotřebovat po vyčerpání pokusů o doručení, zpráva se odešle do fronty opakování. Další cykly opakování se skládají z zprávy vracené z fronty opakování do fronty aplikace, aby se znovu pokusily o doručení do aplikace po zpoždění určeném `retryCycleDelay` atributem. `maxRetryCycles`Atribut určuje počet opakovaných cyklů opakování, které aplikace používá k pokusu o doručení zprávy.|  
|rejectAfterLastRetry|Logická hodnota, která určuje, jaká akce má být provedena pro zprávu s neúspěšným doručením po pokusu o maximální počet opakovaných pokusů.<br /><br /> `true`znamená, že odesílateli je vráceno záporné potvrzení a zpráva je vyřazena; `false`znamená, že zpráva je odeslána do fronty nezpracovatelných zpráv. Výchozí formát je `false`.<br /><br /> Pokud je hodnota `false` , přijímající aplikace může číst nepoškozenou frontu zpráv pro zpracování škodlivých zpráv (tj. zprávy s neúspěšným doručením).<br /><br /> Služba MSMQ 3,0 nepodporuje vrácení negativního potvrzení odesilateli, takže tento atribut bude v MSMQ 3,0 ignorován.|  
|retryCycleDelay|<xref:System.TimeSpan>Určuje časovou prodlevu mezi opakovanými cykly při pokusu o doručení zprávy, která nemohla být doručena okamžitě. Výchozí hodnota je 00:10:00.<br /><br /> Jeden cyklus opakování se pokusí o doručení zprávy do přijímající aplikace zadaného počtu opakování. Počet pokusů, které byly zadány `maxImmediateRetries` atributem. Pokud aplikace nedokáže tuto zprávu spotřebovat po zadaném počtu okamžitých pokusů, zpráva se odešle do fronty opakování. Další cykly opakování se skládají z zprávy vracené z fronty opakování do fronty aplikace, aby se znovu pokusily o doručení do aplikace po zpoždění určeném `retryCycleDelay` atributem. Počet cyklů opakování je určen `maxRetryCycles` atributem.|  
|serializationFormat|Určuje formátovací modul, který slouží k serializaci objektů, které jsou odeslány jako součást zprávy služby MSMQ. Platné hodnoty jsou<br /><br /> -ActiveX: používá se formátovací modul ActiveX při serializaci objektů COM.<br />-Binary: serializace objektu do binárního paketu.<br />-ByteArray: serializace objektu na pole bajtů.<br />-Stream: serializace objektu do datového proudu.<br />-XML: serializace objektu do paketu XML. Výchozí hodnota je XML.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat> .|  
|timeToLive|A <xref:System.TimeSpan> Určuje, jak dlouho jsou zprávy platné, než vyprší jejich platnost a jsou vloženy do fronty nedoručených zpráv. Výchozí hodnota je 1,00:00:00, což znamená 1 den.<br /><br /> Tento atribut je nastaven tak, aby bylo zajištěno, že zprávy citlivé na čas nejsou před zpracováním přijímajícími aplikacemi zastaraly. U zprávy ve frontě, kterou přijímající aplikace nespotřebovává v zadaném časovém intervalu, se říká, že platnost vypršela. Zprávy s vypršenou platností se odesílají do speciální fronty označované jako fronta nedoručených zpráv. Umístění fronty nedoručených zpráv je nastaveno s `customDeadLetterQueue` atributem nebo na odpovídající výchozí hodnotu na základě ujištění.|  
|useMsmqTracing|Logická hodnota určující, zda mají být zprávy zpracované touto vazbou sledovány. Výchozí formát je `false`.<br /><br /> Je-li povoleno trasování, jsou vytvořeny zprávy sestavy a odesílány do fronty sestav pokaždé, když zpráva opustí nebo dorazí na počítač služby Řízení front zpráv.|  
|useSourceJournal|Logická hodnota určující, zda mají být kopie zpráv zpracovaných touto vazbou uloženy ve frontě deníku zdroje. Výchozí formát je `false`.<br /><br /> Aplikace ve frontě, které chtějí uchovávat záznam zpráv, které opustily odchozí fronty počítače, mohou kopírovat zprávy do fronty deníku. Jakmile zpráva opustí odchozí frontu a potvrzení, že byla zpráva přijata v cílovém počítači, bude uložena kopie zprávy ve frontě deníku systému odesílajícího počítače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|msmqTransportSecurity|Určuje nastavení zabezpečení přenosu pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.MsmqIntegrationElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
