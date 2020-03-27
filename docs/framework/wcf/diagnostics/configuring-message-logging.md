---
title: Konfigurace protokolování zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 283f43239d6cf5aea5ea668397a52313ff526e2a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345187"
---
# <a name="configuring-message-logging"></a>Konfigurace protokolování zpráv

Toto téma popisuje, jak můžete nakonfigurovat protokolování zpráv pro různé scénáře.

## <a name="enabling-message-logging"></a>Povolení protokolování zpráv

Windows Communication Foundation (WCF) neprotokoluje zprávy ve výchozím nastavení. Chcete-li aktivovat protokolování zpráv, `System.ServiceModel.MessageLogging` je nutné přidat posluchače `<messagelogging>` trasování do zdroje trasování a nastavit atributy prvku v konfiguračním souboru.

Následující příklad ukazuje, jak povolit protokolování a zadat další možnosti.

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
         <add name="messages"
              type="System.Diagnostics.XmlWriterTraceListener"
              initializeData="c:\logs\messages.svclog" />
        </listeners>
    </source>
  </sources>
</system.diagnostics>

<system.serviceModel>
  <diagnostics>
    <messageLogging
         logEntireMessage="true"
         logMalformedMessages="false"
         logMessagesAtServiceLevel="true"
         logMessagesAtTransportLevel="false"
         maxMessagesToLog="3000"
         maxSizeOfMessageToLog="2000"/>
  </diagnostics>
</system.serviceModel>
```

Další informace o nastavení protokolování zpráv naleznete v [tématu Doporučená nastavení trasování a protokolování zpráv](./tracing/recommended-settings-for-tracing-and-message-logging.md).

Můžete zadat `add` název a typ naslouchacího procesu, který chcete použít. V příkladu konfigurace listener s názvem "zprávy" a přidá standardní`System.Diagnostics.XmlWriterTraceListener`.NET Framework naslouchací proces trasování ( ) jako typ, který má být používán. Pokud používáte `System.Diagnostics.XmlWriterTraceListener`, musíte zadat umístění výstupního souboru a název v konfiguračním souboru. To se provádí `initializeData` nastavením názvu souboru protokolu. V opačném případě systém vyvolá výjimku. Můžete také implementovat vlastní naslouchací proces, který vydává protokoly do výchozího souboru.

> [!NOTE]
> Vzhledem k tomu, že protokolování zpráv přistupuje k místu na disku, měli byste omezit počet zpráv zapsaných na disk pro určitou službu. Po dosažení limitu zprávy je vytvořeno trasování na úrovni Informace a všechny aktivity protokolování zpráv zastavit.

Úroveň protokolování, stejně jako další možnosti, jsou popsány v části Úroveň protokolování a možnosti.

Atribut `switchValue` a `source` je platný pouze pro trasování. Pokud zadáte `switchValue` atribut pro `System.ServiceModel.MessageLogging` zdroj trasování následujícím způsobem, nemá žádný vliv.

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
</source>
```

Chcete-li zakázat zdroj trasování, `logMessagesAtServiceLevel`měli `logMalformedMessages`byste `logMessagesAtTransportLevel` místo toho `messageLogging` použít atributy , a atributy prvku. Všechny tyto atributy byste `false`měli nastavit na . To lze provést pomocí konfiguračního souboru v předchozím příkladu kódu, prostřednictvím rozhraní uživatelského rozhraní editoru konfigurace nebo pomocí služby WMI. Další informace o nástroji Editor konfigurace naleznete v [tématu Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md). Další informace o službě WMI naleznete [v tématu Použití nástroje Pro diagnostiku systému Windows](./wmi/index.md).

## <a name="logging-levels-and-options"></a>Úrovně protokolování a možnosti

U příchozích zpráv protokolování dochází bezprostředně po vytvoření zprávy, bezprostředně před zpráva se dostane do uživatelského kódu na úrovni služby a při zjištění poškozených zpráv.

U odchozích zpráv protokolování dochází ihned po zprávě opustí uživatelský kód a bezprostředně před zpráva přejde na lince.

WCF protokoluje zprávy na dvou různých úrovních, služby a přenos. Jsou také protokolovány poškozené zprávy. Tyto tři kategorie jsou na sobě nezávislé a lze je aktivovat samostatně v konfiguraci.

Úroveň protokolování můžete řídit `logMessagesAtServiceLevel`nastavením `logMalformedMessages` `logMessagesAtTransportLevel` , a `messageLogging` atributy prvku.

### <a name="service-level"></a>Úroveň služeb

Zprávy zaznamenané v této vrstvě se chystají zadat (při příjmu) nebo nechat (při odesílání) uživatelský kód. Pokud byly definovány filtry, jsou protokolovány pouze zprávy, které odpovídají filtrům. V opačném případě jsou protokolovány všechny zprávy na úrovni služby. Zprávy infrastruktury (transakce, kanál peer a zabezpečení) jsou také protokolovány na této úrovni, s výjimkou spolehlivé zprávy zpráv. U streamovaných zpráv jsou protokolovány pouze záhlaví. Kromě toho jsou na této úrovni zaznamenány zabezpečené zprávy.

### <a name="transport-level"></a>Úroveň přepravy

Zprávy zaznamenané v této vrstvě jsou připraveny k zakódování nebo dekódování pro nebo po přepravě po lince. Pokud byly definovány filtry, jsou protokolovány pouze zprávy, které odpovídají filtrům. V opačném případě jsou protokolovány všechny zprávy ve vrstvě přenosu. Všechny zprávy infrastruktury jsou protokolovány v této vrstvě, včetně spolehlivé zprávy zpráv. U streamovaných zpráv jsou protokolovány pouze záhlaví. Kromě toho jsou zabezpečené zprávy protokolovány jako šifrované na této úrovni, s výjimkou případů, kdy je použit zabezpečený přenos, jako je https.

### <a name="malformed-level"></a>Nepoškozená úroveň

Poškozené zprávy jsou zprávy, které jsou odmítnuty zásobníku WCF v jakékoli fázi zpracování. Poškozené zprávy jsou protokolovány tak, jak jsou: šifrovány, pokud tomu tak je, s nesprávným XML a tak dále. `maxSizeOfMessageToLog`definována velikost zprávy, která má být zaznamenána jako CDATA. Ve výchozím `maxSizeOfMessageToLog` nastavení se rovná 256 kM. Další informace o tomto atributu naleznete v části Další možnosti.

### <a name="other-options"></a>Další možnosti

Kromě úrovní protokolování může uživatel zadat následující možnosti:

- Protokolovat celou`logEntireMessage` zprávu (atribut): Tato hodnota určuje, zda je protokolována celá zpráva (záhlaví a text zprávy). Výchozí hodnota `false`je , což znamená, že je zaznamenána pouze hlavička. Toto nastavení ovlivňuje úrovně protokolování zpráv o službách a přenosu..

- Maximální počet zpráv`maxMessagesToLog` k protokolu ( atribut): Tato hodnota určuje maximální počet zpráv, které mají být protokolovat. Všechny zprávy (služby, přenosy a poškozené zprávy) se započítávají do této kvóty. Po dosažení kvóty je vyzařováno trasování a je zaznamenána žádná další zpráva. Výchozí hodnota je 10000.

- Maximální velikost zprávy pro`maxSizeOfMessageToLog` protokol (atribut): Tato hodnota určuje maximální velikost zpráv pro přihlášení bajtů. Zprávy, které překračují limit velikosti, nejsou protokolovány a pro tuto zprávu se neprovádí žádná jiná aktivita. Toto nastavení ovlivní všechny úrovně trasování. Pokud servicemodel trasování je zapnuto, sledování úrovně upozornění je emitován v prvním bodě protokolování (ServiceModelSend* nebo TransportReceive) upozornit uživatele. Výchozí hodnota pro zprávy na úrovni služeb a přenosu je 256 kN, zatímco výchozí hodnota pro poškozené zprávy je 4 K.

  > [!CAUTION]
  > Velikost zprávy, která je vypočítána porovnat proti `maxSizeOfMessageToLog` je velikost zprávy v paměti před serializace. Tato velikost se může lišit od skutečné délky řetězce zprávy, který je protokolován a v mnoha případech je větší než skutečná velikost. V důsledku toho zprávy nemusí být protokolovány. Tuto skutečnost můžete vysvětlit zadáním `maxSizeOfMessageToLog` atributu o 10 % větší než očekávaná velikost zprávy. Kromě toho pokud jsou protokolovány poškozené zprávy, skutečné místo na disku využité protokoly zpráv může být `maxSizeOfMessageToLog`až 5 krát velikost hodnoty určené .

Pokud v konfiguračním souboru není definován žádný posluchač trasování, není generován žádný výstup protokolování bez ohledu na zadanou úroveň protokolování.

Možnosti protokolování zpráv, jako jsou atributy popsané v této části, lze změnit za běhu pomocí nástroje WMI (WMI). To lze provést přístupem k instanci [AppDomainInfo,](./wmi/appdomaininfo.md) která `LogMessagesAtServiceLevel`zpřístupňuje tyto logické vlastnosti: , `LogMessagesAtTransportLevel`a `LogMalformedMessages`. Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale nastavte tyto možnosti v `false` konfiguraci, můžete je později změnit na `true` při spuštění aplikace. To efektivně umožňuje protokolování zpráv za běhu. Podobně pokud povolíte protokolování zpráv v konfiguračním souboru, můžete jej zakázat za běhu pomocí služby WMI. Další informace naleznete [v tématu Using Windows Management Instrumentation for Diagnostics](./wmi/index.md).

Pole `source` v protokolu zpráv určuje, ve kterém kontextu je zpráva zaznamenána: při odesílání/přijímání zprávy požadavku, pro požadavek odpověď nebo požadavek na 1 cestu, na modelu služby nebo transportní vrstvě nebo v případě poškozené zprávy.

U poškozených `source` zpráv se `Malformed`rovná . Jinak zdroj má následující hodnoty založené na kontextu.

Pro požadavek/odpověď

||Odeslat požadavek|Žádost o přijetí|Odeslat odpověď|Přijímat odpovědi|
|-|------------------|---------------------|----------------|-------------------|
|Vrstva modelu služby|Služba<br /><br /> Úroveň<br /><br /> Odeslat<br /><br /> Žádost|Služba<br /><br /> Úroveň<br /><br /> Přijmout<br /><br /> Žádost|Služba<br /><br /> Úroveň<br /><br /> Odeslat<br /><br /> Odpovědět|Služba<br /><br /> Úroveň<br /><br /> Přijmout<br /><br /> Odpovědět|
|Transportní vrstva|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijmout|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijmout|

Pro jednosměrný požadavek

||Odeslat požadavek|Žádost o přijetí|
|-|------------------|---------------------|
|Vrstva modelu služby|Služba<br /><br /> Úroveň<br /><br /> Odeslat<br /><br /> Datagram|Služba<br /><br /> Úroveň<br /><br /> Přijmout<br /><br /> Datagram|
|Transportní vrstva|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijmout|

## <a name="message-filters"></a>Filtry zpráv

Filtry zpráv jsou `messageLogging` definovány `diagnostics` v konfiguračním prvku konfigurační části. Používají se na úrovni služeb a dopravy. Pokud je definován jeden nebo více filtrů, jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů. Pokud není definován žádný filtr, všechny zprávy projít.

Filtry podporují úplnou syntaxi XPath a jsou použity v pořadí, v jakém se zobrazují v konfiguračním souboru. Syntakticky nesprávný filtr má za následek výjimku konfigurace.

Filtry také poskytují bezpečnostní `nodeQuota` funkci pomocí atributu, který omezuje maximální počet uzlů v XPath DOM, které lze zkontrolovány tak, aby odpovídaly filtru.

Následující příklad ukazuje, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.

```xml
<messageLogging logEntireMessage="true"
    logMalformedMessages="true"
    logMessagesAtServiceLevel="true"
    logMessagesAtTransportLevel="true"
    maxMessagesToLog="420">
    <filters>
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
                 /soap:Envelope/soap:Header
        </add>
     </filters>
</messageLogging>
```

Filtry nelze použít na text zprávy. Filtry, které se pokoušejí manipulovat s tělem zprávy, budou odebrány ze seznamu filtrů. Událost je také emitován, který označuje toto. Následující filtr by byl například odebrán z tabulky filtrů.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Konfigurace vlastního naslouchací procesu

Můžete také nakonfigurovat vlastní naslouchací proces s dalšími možnostmi. Vlastní naslouchací proces může být užitečné při filtrování prvků PII specifické pro aplikaci ze zpráv před protokolováním. Následující příklad ukazuje vlastní konfiguraci naslouchací proces.

```xml
<system.diagnostics>
   <sources>
     <source name="System.ServiceModel.MessageLogging">
           <listeners>
             <add name="MyListener"
                    type="YourCustomListener"
                    initializeData="c:\logs\messages.svclog"
                    maxDiskSpace="1000"/>
           </listeners>
     </source>
   </sources>
</system.diagnostics>
```

Měli byste si `type` být vědomi toho, že atribut by měl být nastaven na kvalifikovaný název sestavení typu.

## <a name="see-also"></a>Viz také

- [\<messageLogging>](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Protokolování zpráv](message-logging.md)
- [Doporučené nastavení pro trasování a protokolování zpráv](./tracing/recommended-settings-for-tracing-and-message-logging.md)
