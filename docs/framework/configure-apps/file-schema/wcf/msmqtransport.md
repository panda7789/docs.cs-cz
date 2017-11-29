---
title: '&lt;msmqTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d89f35-76ac-49dc-832b-e8bec2d5e33b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc96bcaae74be5e59f0da69b02e350e2c77d61e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmsmqtransportgt"></a>&lt;msmqTransport&gt;
Na přenos MSMQ způsobí kanálu pro přenos zpráv, když je zahrnutý do vlastní vazby.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<msmqIntegration >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<msmqTransport>  
    customDeadLetterQueue="Uri"  
    deadLetterQueue="Custom/None/System"  
    durable="Boolean"  
    exactlyOnce="Boolean"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxImmediateRetries="Integer"  
    maxPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    maxRetryCycles="Integer"  
....queueTransferProtocol="Native/Srmp/SrmpSecure"  
    rejectAfterLastRetry="Boolean"  
    retryCycleDelay="TimeSpan"  
    timeToLive="TimeSpan"  
    useActiveDirectory="Boolean"  
    useSourceJournal="Boolean"  
    useMsmqTracing="Boolean"  
    <msmqTransportSecurity>  
    </msmqTransportSecurity>  
</msmqIntegration>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customDeadLetterQueue|Identifikátor URI, který určuje umístění do fronty nedoručených zpráv jednotlivých aplikací, které se přenáší zprávy, které mají vypršela platnost, nebo se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které vyžadují ExactlyOnce záruky (tedy `exactlyOnce` je nastaven na `true`), použije se výchozí hodnota tohoto atributu do fronty transakcí nedoručených zpráv systémové služby MSMQ.<br /><br /> Pro zprávy, které vyžadují žádné záruky (tedy `exactlyOnce` je nastaven na `false`), použije se výchozí hodnota tohoto atributu `null`.<br /><br /> Hodnota musí používat schéma net.msmq. Výchozí hodnota je `null`.<br /><br /> Pokud `deadLetterQueue` je nastaven na `None` nebo `System`, pak tento atribut musí být nastaven na `null`. Pokud není tento atribut `null`, pak `deadLetterQueue` musí být nastavena na `Custom`.|  
|deadLetterQueue|Určuje typ fronty nedoručených zpráv používat.<br /><br /> Platné hodnoty patří<br /><br /> – Vlastní: Fronty nedoručených zpráv vlastní.<br />-None: Žádná fronta nedoručených zpráv se má použít.<br />-Systém: Použijte fronty nedoručených zpráv systému.<br /><br /> Tento atribut je typu DeadLetterQueue.|  
|trvanlivý|Logická hodnota, která určuje, zda jsou zprávy zpracovávané touto vazbou trvalé nebo přechodné. Výchozí hodnota je `true`.<br /><br /> Trvanlivý zprávu odolává fronty manager havárie, při volatile zpráva neexistuje. Volatile zprávy jsou užitečné, když aplikace vyžadují nižší latenci a tolerovat příležitostně ztrátě zpráv.<br /><br /> Pokud `exactlyOnce` je nastaven na `true`, musí být trvanlivý zprávy.|  
|exactlyOnce|Logická hodnota, která určuje, zda budou zprávy zpracovávané touto vazbou obdrženy pouze jednou. Výchozí hodnota je `true`.<br /><br /> S nebo bez záruky, může být odeslána zpráva. Zajištění umožňuje aplikaci zkontrolujte, že odeslaná zpráva dorazila do přijímající fronty zpráv nebo pokud nebyla, aplikace této služby můžete zjistit načtením fronty nedoručených zpráv.<br /><br /> `exactlyOnce`, pokud je nastavena na `true`, označuje, že služby MSMQ zajišťují, že odeslaná zpráva se doručí na přijímací fronty zpráv jednou a pouze jednou, a pokud doručení selže, je zpráva odeslána do fronty nedoručených zpráv.<br /><br /> Zprávy s `exactlyOnce` nastavena na `true` do transakční fronty, musí se poslat.|  
|manualAddressing|Logická hodnota, která umožňuje uživatelům převzít kontrolu nad adresování zprávy. Tato vlastnost se obvykle používá ve scénářích směrovače, kde aplikace určuje, které jeden z několika cílů odeslat zprávu na.<br /><br /> Pokud nastavíte hodnotu `true`, kanál předpokládá zpráva již splněna a k němu nepřidává žádné další informace. Uživatel pak může jednotlivě adres každou zprávu.<br /><br /> Pokud nastavíte hodnotu `false`, výchozího mechanismu adresování Windows Communication Foundation (WCF) automaticky vytvoří adresy pro všechny zprávy.<br /><br /> Výchozí hodnota je `false`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti. Výchozí hodnota je 524288.<br /><br /> Mnoho části služby WCF pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|maxImmediateRetries|Celé číslo, které určuje maximální počet opakování okamžitou pokusí na zprávu, která je pro čtení z fronty aplikace... Výchozí hodnota je 5.<br /><br /> Pokud dojde k pokusu o maximální počet okamžitou opakovaných pokusů pro zprávu a zpráva není spotřebovávají aplikace, je zpráva odeslána do fronty opakování pro opakování novější někde v čase. Pokud nejsou zadány žádné opakování cykly, pak je buď odeslaných zpráv do fronty nezpracovatelná zpráva nebo záporné potvrzení budou odeslána zpět do odesílatele.|  
|MaxPoolSize|Kladné celé číslo, které určuje maximální velikost fondu. Výchozí hodnota je 524288.|  
|MaxReceivedMessageSize|Kladné celé číslo, které určuje maximální velikost zprávy v bajtech, včetně hlavičky. Odesílatel zprávy obdrží chybu protokolu SOAP po příliš velké vzhledem k příjemce zprávy. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|maxRetryCycles|Celé číslo, které určuje maximální počet cyklů opakování pokusu o doručení zprávy do přijímající aplikace. Výchozí hodnota je <xref:System.Int32.MaxValue>.<br /><br /> Cyklus jeden opakování se pokusí odeslat zprávu do aplikace zadaného počtu opakování. Počet provedených pokusů nastavena `maxImmediateRetries` atribut. Pokud aplikace využívat zprávu po byly vyčerpány pokusů na doručení, je zpráva odeslána do fronty opakování. Následné opakování cykly obsahovat zprávy do fronty aplikace návratu z fronty opakování pokusu o doručení do aplikace znovu po prodlevě určeného `retryCycleDelay` atribut. `maxRetryCycles` Atribut určuje počet cyklů opakování aplikace využívá při pokusu o doručení zprávy.|  
|Třída QueueTransferProtocol|Určuje přenosu kanál komunikace ve frontě, která používá tuto vazbu. Platné hodnoty jsou<br /><br /> -Native: Použijte nativní protokol služby MSMQ.<br />-Srmp: Použijte spolehlivého zasílání zpráv protokolu Soap (SRMP).<br />-SrmpSecure: Používají přenos protokolu Soap spolehlivého zasílání zpráv protokolu zabezpečení (SRMPS).<br /><br /> Tento atribut je typu <xref:System.ServiceModel.QueueTransferProtocol>.<br /><br /> Vzhledem k tomu, že služby MSMQ nepodporuje služby Active Directory adresování při použití protokolu SOAP spolehlivého zasílání zpráv, by neměl nastavte tento atribut Srmp nebo Srmps při `u``seActiveDirectory` je nastaven na `true`.|  
|rejectAfterLastRetry|Logická hodnota, která určuje, jaká opatření se mají přijmout zprávy, která se nezdařila doručení po maximální počet opakovaných pokusů se pokusil.<br /><br /> `true`znamená, že záporné potvrzení se vrátí do odesílatele a zpráva je vyřazena; `false` znamená, že je zpráva odeslána do fronty poškozených zpráv. Výchozí hodnota je `false`.<br /><br /> Pokud je hodnota `false`, má přijímající aplikace může číst nezpracovatelná zpráva fronty ke zpracování poškozených zpráv (tedy zpráv, které selhaly doručení).<br /><br /> Služba MSMQ 3.0 nepodporuje záporné potvrzení vrácením odesílatele, tento atribut bude proto ignorován v MSMQ 3.0.|  
|retryCycleDelay|A <xref:System.TimeSpan> , který určuje prodlevu mezi cykly opakovat při pokusu o doručení zprávy, která nelze doručit okamžitě. Výchozí hodnota je 00:10:00.<br /><br /> Cyklus jeden opakování se pokusí doručit zprávu přijímající aplikace zadaného počtu opakování. Počet provedených pokusů je zadána `maxImmediateRetries` atribut. Pokud aplikace využívat zprávu po zadaný počet opakování okamžitě, je zpráva odeslána do fronty opakování. Následné opakování cykly obsahovat zprávy do fronty aplikace návratu z fronty opakování pokusu o doručení do aplikace znovu po prodlevě určeného `retryCycleDelay` atribut. Počet cyklů opakování je zadána `maxRetryCycles` atribut.|  
|TimeToLive|A <xref:System.TimeSpan> určující, jak dlouho jsou zprávy platné předtím, než platnost a jsou umístěna do fronty nedoručených zpráv. Výchozí hodnota je 1.00:00:00, což znamená 1 den.<br /><br /> Tento atribut nastavený zajistit, že zprávy dobou nepřestali být zastaralé dříve, než je přijímací aplikace. Zprávy ve frontě, který není přijímající aplikace v rámci zadaného časového intervalu říká, že je mít skončenou platnost. Zprávy s vypršenou platností se odesílají do speciální fronty názvem fronty nedoručených zpráv. Umístění fronty nedoručených zpráv nastavena `customDeadLetterQueue` atribut, nebo odpovídající výchozí, aby na základě záruky.|  
|Třída UseActiveDirectory|Logická hodnota, která určuje, zda mají být převedeny fronty adresy pomocí služby Active Directory.<br /><br /> MSMQ fronty adresy se může skládat z názvů cestu nebo přímé formátu. Pomocí přímého názvu formátu vyřeší MSMQ názvu počítače pomocí DNS, pro rozhraní NetBIOS nebo IP. S názvem cesty vyřeší MSMQ názvu počítače pomocí služby Active Directory. Ve výchozím nastavení Windows Communication Framework (WCF) zařazených do fronty přenosu převede identifikátor URI k přímého názvu formátu fronty zpráv. Nastavením tohoto atributu na `true`, aplikace, můžete určit, že zařazených do fronty přenosu by měla vyřešit název počítače pomocí služby Active Directory místo DNS, pro rozhraní NetBIOS nebo IP.|  
|useMsmqTracing|Logická hodnota, která určuje, zda zprávy zpracovávané touto vazbou má trasovat. Výchozí hodnota je `false`.<br /><br /> Pokud je povoleno sledování, sestava zprávy se vytváří a odesílají do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítači služby Řízení front zpráv.|  
|useSourceJournal|Logická hodnota, která určuje, zda by měly být uložené kopie zprávy zpracovávané touto vazbou ve frontě deníku zdroje. Výchozí hodnota je `false`.<br /><br /> Ve frontě aplikací, které chcete zachovat záznam zprávy, které mají zbývající počítače fronty odesílaných zpráv můžete zkopírovat do deníku fronty zpráv. Jakmile zprávu opustí fronty odesílaných zpráv a je obdržena potvrzení, že zpráva byla přijata v cílovém počítači, je udržováno kopie zprávy ve frontě deníku odesílající počítač systému.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<msmqTransportSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransportsecurity.md)|Určuje nastavení zabezpečení přenosu pro tuto vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `msmqTransport` Element umožňuje uživatelům nastavit vlastnosti ve frontě komunikační kanál. Ve frontě komunikační kanál používá pro jeho přenos služby Řízení front zpráv.  
  
 Tento element vazba je výchozí element vazba používá standardní vazby služby Řízení front zpráv (`netMsmqBinding`).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.MsmqTransportElement>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
