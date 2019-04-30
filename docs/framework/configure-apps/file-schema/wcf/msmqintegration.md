---
title: <msmqIntegration>
ms.date: 03/30/2017
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
ms.openlocfilehash: 850d117ca17b5929c219c3b7d6453cf76136bad3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772527"
---
# <a name="msmqintegration"></a>\<msmqIntegration>
Určuje přenos služby MSMQ pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<msmqIntegration>  
  
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
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customDeadLetterQueue|Identifikátor URI, který označuje umístění fronty nedoručených zpráv jednotlivým aplikacím, kde se přenáší zprávy, které mají platnost nebo se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které vyžadují záruky ExactlyOnce (to znamená `exactlyOnce` je nastavena na `true`), výchozí hodnota tohoto atributu celý systém transakční fronty nedoručených zpráv služby MSMQ.<br /><br /> Pro zprávy, které vyžadují žádné záruky (to znamená `exactlyOnce` je nastavena na `false`), výchozí hodnota tohoto atributu `null`.<br /><br /> Hodnota musí používat schéma net.msmq. Výchozí hodnota je `null`.<br /><br /> Pokud `deadLetterQueue` je nastavena na `None` nebo `System`, tento atribut musí být nastaven na `null`. Pokud tento atribut není `null`, pak `deadLetterQueue` musí být nastaveno na `Custom`.|  
|deadLetterQueue|Určuje typ fronty nepoužívaných dopisů používat.<br /><br /> Platné hodnoty jsou<br /><br /> – Vlastní: Fronty nedoručených zpráv vlastní.<br />-Žádný: Žádné fronty nedoručených zpráv se má použít.<br />– System: Použití fronty nedoručených zpráv systému.<br /><br /> Tento atribut je typu DeadLetterQueue.|  
|trvalý|Logická hodnota určující, zda zprávy zpracované touto vazbou jsou trvalé nebo přechodné. Výchozí hodnota je `true`.<br /><br /> Zpráv trvalý odolává chybovému ukončení správce fronty, ale volatile zpráva nikoli. Volatile zprávy jsou užitečné, pokud aplikace vyžaduje nižší latenci a která tolerují občasné ztracené zprávy.<br /><br /> Pokud `exactlyOnce` je nastavena na `true`, zprávy musí být trvalý.|  
|exactlyOnce|Logická hodnota, která určuje, zda zprávy zpracované touto vazbou budou obdrženy pouze jednou. Výchozí hodnota je `true`.<br /><br /> S nebo bez záruky, může být odeslána zpráva. Zajištění umožňuje aplikaci zajistit, že odeslaná zpráva dorazila přijímající fronty zpráv nebo pokud tomu tak není, používání této služby můžete zjistit načtením do fronty nedoručených zpráv.<br /><br /> `exactlyOnce`, pokud je nastavena na `true`, označuje, že služby MSMQ zajistí, že odeslané zprávy se doručí do fronty zpráv přijímací pouze jednou a jednou, a pokud selže doručování je zpráva odeslána do fronty nedoručených zpráv.<br /><br /> Zprávy odeslané s `exactlyOnce` nastavena na `true` se musí odeslat na transakční frontu.|  
|Vlastnost manualAddressing|Logická hodnota, která umožňuje uživateli řídit adresování zpráv. Tato vlastnost se obvykle používá ve scénářích směrovače, kde aplikace určuje, který z nich několik cílů odeslat zprávu do.<br /><br /> Pokud je nastavena na `true`, kanál se předpokládá zprávu už nemá řešení a k němu nepřidává žádné další informace. Uživatel může pak Adresujte všechny zprávy jednotlivě.<br /><br /> Pokud je nastavena na `false`, výchozího mechanismu adresování Windows Communication Foundation (WCF) automaticky vytvoří adresy pro všechny zprávy.<br /><br /> Výchozí hodnota je `false`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávacích pamětí. Výchozí hodnota je 524288.<br /><br /> Mnoho částí WCF pomocí vyrovnávací paměti. Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné. S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi. Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.|  
|maxImmediateRetries|Celé číslo, které určuje maximální počet okamžitých opakovaných pokusů o zprávu, která je načtena z fronty aplikace. Výchozí hodnota je 5.<br /><br /> Pokud dojde k pokusu o maximální počet okamžité opakování u zprávy a zprávy není používané aplikace, je zpráva odeslána do fronty opakování pro opakování někdy později v čase. Pokud nejsou zadány žádné cyklů opakování, pak buď odesílají zprávy do fronty nezpracovatelných zpráv nebo negativní potvrzení budou odeslána zpět do odesílatele.|  
|maxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy v bajtech, včetně záhlaví. Odesílatel zprávy obdrží chybu protokolu SOAP v případě, že zprávy je příliš velký pro příjemce. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|maxRetryCycles|Celé číslo, které určuje maximální počet opakovaných cyklů pokusů o doručení zpráv do přijímající aplikace. Výchozí hodnota je <xref:System.Int32.MaxValue>.<br /><br /> Jednoho opakování cyklu pokusí o doručení zprávy do aplikace zadaného počtu opakování. Počet pokusů o se nastavil `maxImmediateRetries` atribut. Pokud aplikace po vyčerpání pokusů na doručování využívat zprávy, zprávu odeslat do fronty zkuste to znovu. Dalším pokusem cykly se skládají zprávy se do fronty aplikace vrací z fronty opakování pokusu o doručení pro aplikaci znovu spustit, po době určené `retryCycleDelay` atribut. `maxRetryCycles` Atribut určuje počet cyklů opakování pokusu o doručení zprávy používá aplikace.|  
|rejectAfterLastRetry|Logická hodnota, která určuje, jaká akce má být zprávy, která se nezdařila doručování po maximální počet opakování pokusů.<br /><br /> `true` znamená, že negativní potvrzení se vrátí do odesílatele a zprávy se zahodí; `false` znamená, že je zpráva odeslána do fronty nezpracovatelných zpráv. Výchozí hodnota je `false`.<br /><br /> Pokud je hodnota `false`, přijímající aplikace může číst nezpracovatelných zpráv fronty ke zpracování nezpracovatelných zpráv (to znamená, zprávy, které selhaly doručování).<br /><br /> Služba MSMQ 3.0 nepodporuje vrácení negativní potvrzení odesílateli, takže tento atribut se bude ignorovat ve službě MSMQ 3.0.|  
|retryCycleDelay|A <xref:System.TimeSpan> , která určuje časovou prodlevu mezi cyklů opakování při pokusu o doručení zprávy, která nemohla být doručena okamžitě. Výchozí hodnota je 00:10:00.<br /><br /> Pro doručení zprávy do přijímající aplikace zadaného počtu opakování pokusů o jednoho opakování cyklu. Je určený počet pokusů o `maxImmediateRetries` atribut. Pokud aplikace využívat zprávy po zadaný počet okamžité opakování, je zpráva odeslána do fronty zkuste to znovu. Dalším pokusem cykly se skládají zprávy se do fronty aplikace vrací z fronty opakování pokusu o doručení pro aplikaci znovu spustit, po době určené `retryCycleDelay` atribut. Počet cyklů opakování je určená `maxRetryCycles` atribut.|  
|třídu serializationFormat|Určuje formátování, který se používá k serializaci objektů, které jsou odeslány jako součást zprávy MSMQ. Platné hodnoty jsou<br /><br /> -ActiveX: Formátovací modul ActiveX se používá při serializaci objektů COM.<br />-Binární:  Serializuje objekt do binární paketů.<br />-ByteArray:  Serializuje objekt na pole bajtů.<br />-Stream:  Serializuje objekt do datového proudu.<br />-   Xml:  Serializuje objekt, který má paket XML. Výchozí hodnota je XML.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|A <xref:System.TimeSpan> , která určuje, jak dlouho jsou zprávy platné předtím, než platnost a jsou vloženy do fronty nedoručených zpráv. Výchozí hodnota je 1.00:00:00, což znamená, že 1 den.<br /><br /> Tento atribut je nastaven na Ujistěte se, že časově zprávy není zastaralá předtím, než se zpracovávají přijímajícími aplikacemi. Zprávy ve frontě, které se přijímající aplikací v rámci zadaného časového intervalu se říká, že platnost. Zprávy s vypršenou platností se odesílají do speciální fronty názvem fronty nedoručených zpráv. Umístění fronty nedoručených zpráv nastavena `customDeadLetterQueue` atribut nebo na vhodné výchozí nastavení, v závislosti na záruky.|  
|useMsmqTracing|Logická hodnota, která určuje, zda zprávy zpracované touto vazbou mají být vyvolány. Výchozí hodnota je `false`.<br /><br /> Když je povoleno trasování, zprávy se vytváří a odesílají do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítači služby Řízení front zpráv.|  
|useSourceJournal|Logická hodnota určující, zda kopie zpráv zpracovaných touto vazbou uskladněny ve frontě deníku zdroje. Výchozí hodnota je `false`.<br /><br /> Ve frontě aplikace, které chcete sledovat zpráv, které ještě zbývá fronty odesílaných zpráv počítače můžete zkopírovat zprávy do fronty deníku. Jakmile opustí zprávu fronty odesílaných zpráv a přijetí potvrzení, že byla přijata zpráva v cílovém počítači, kopie zprávy, zůstane ve frontě deníků odesílající počítač systému.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|msmqTransportSecurity|Určuje nastavení zabezpečení přenosu pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.MsmqIntegrationElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
