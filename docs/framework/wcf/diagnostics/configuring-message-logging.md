---
title: Konfigurace protokolování zpráv
description: Naučte se konfigurovat protokolování zpráv, včetně toho, jak povolit protokolování, úrovně protokolování, filtry zpráv a jak nakonfigurovat vlastní naslouchací proces ve službě WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 5203f19a18e5fa6b0ed7f68e1d1de0447da41abd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247659"
---
# <a name="configuring-message-logging"></a>Konfigurace protokolování zpráv

Toto téma popisuje, jak můžete nakonfigurovat protokolování zpráv pro různé scénáře.

## <a name="enabling-message-logging"></a>Povolení protokolování zpráv

Windows Communication Foundation (WCF) neprotokoluje zprávy ve výchozím nastavení. Chcete-li aktivovat protokolování zpráv, je nutné přidat naslouchací proces trasování do `System.ServiceModel.MessageLogging` zdroje trasování a nastavit atributy `<messagelogging>` prvku v konfiguračním souboru.

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

Další informace o nastavení protokolování zpráv najdete v tématu [Doporučené nastavení pro trasování a protokolování zpráv](./tracing/recommended-settings-for-tracing-and-message-logging.md).

Můžete použít `add` k zadání názvu a typu naslouchacího procesu, který chcete použít. V ukázkové konfiguraci má naslouchací proces název "zprávy" a přidává standardní .NET Framework trasování trasování ( `System.Diagnostics.XmlWriterTraceListener` ) jako typ, který se má použít. Pokud používáte `System.Diagnostics.XmlWriterTraceListener` , musíte zadat umístění a název výstupního souboru do konfiguračního souboru. To se provádí nastavením `initializeData` na název souboru protokolu. V opačném případě systém vyvolá výjimku. Můžete také implementovat vlastní naslouchací proces, který vysílá protokoly do výchozího souboru.

> [!NOTE]
> Vzhledem k tomu, že protokolování zpráv přistupuje místo na disku, měli byste omezit počet zpráv zapsaných na disk pro konkrétní službu. Po dosažení limitu zpráv se vyprodukuje trasování na úrovni informací a zastaví se všechny aktivity protokolování zpráv.

Úroveň protokolování, jakož i další možnosti, jsou popsány v části úroveň protokolování a možnosti.

`switchValue`Atribut `source` je platný pouze pro trasování. Pokud zadáte `switchValue` atribut pro `System.ServiceModel.MessageLogging` zdroj trasování následujícím způsobem, nemá žádný vliv.

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
</source>
```

Chcete-li zakázat zdroj trasování, použijte `logMessagesAtServiceLevel` `logMalformedMessages` `logMessagesAtTransportLevel` místo toho atributy, a `messageLogging` elementu. Všechny tyto atributy byste měli nastavit na `false` . To lze provést pomocí konfiguračního souboru v předchozím příkladu kódu, prostřednictvím rozhraní Editor konfigurací uživatelského rozhraní nebo pomocí rozhraní WMI. Další informace o nástroji Editor konfigurací najdete v tématu [Nástroj Configuration Editor (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md). Další informace o rozhraní WMI najdete v tématu [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](./wmi/index.md).

## <a name="logging-levels-and-options"></a>Úrovně a možnosti protokolování

Pro příchozí zprávy probíhá protokolování ihned po vytvoření zprávy, bezprostředně před tím, než se zpráva dostane do uživatelského kódu na úrovni služby a při zjištění poškozených zpráv.

U odchozích zpráv probíhá protokolování ihned poté, co zpráva opustí uživatelský kód a hned před tím, než se zpráva dostane na kabel.

WCF protokoluje zprávy na dvou různých úrovních, službách a přenosu. Protokolují se také poškozené zprávy. Tři kategorie jsou vzájemně nezávislé a je možné je aktivovat samostatně v konfiguraci.

Úroveň protokolování můžete řídit nastavením `logMessagesAtServiceLevel` `logMalformedMessages` atributů, a `logMessagesAtTransportLevel` `messageLogging` elementu.

### <a name="service-level"></a>Úroveň služby

Zprávy zaznamenávané v této vrstvě se chystá zadat (při přijetí) nebo nechávají (při odesílání) uživatelský kód. Pokud byly definovány filtry, budou protokolovány pouze zprávy, které odpovídají filtrům. V opačném případě budou všechny zprávy na úrovni služby protokolovány. Zprávy infrastruktury (transakce, rovnocenný kanál a zabezpečení) se protokolují i na této úrovni, s výjimkou zpráv spolehlivého zasílání zpráv. U zpráv v proudu jsou protokolovány pouze hlavičky. Kromě toho se na této úrovni šifrují protokolované zabezpečené zprávy.

### <a name="transport-level"></a>Úroveň transportu

Zprávy zaznamenávané v této vrstvě jsou připravené k kódování nebo dekódování pro nebo po přepravení na drátě. Pokud byly definovány filtry, budou protokolovány pouze zprávy, které odpovídají filtrům. V opačném případě jsou všechny zprávy na transportní vrstvě protokolovány. Všechny zprávy infrastruktury jsou protokolovány v této vrstvě, včetně spolehlivých zpráv o zasílání zpráv. U zpráv v proudu jsou protokolovány pouze hlavičky. Zabezpečené zprávy se navíc protokolují jako šifrované na této úrovni, s výjimkou případů, kdy se používá zabezpečená přeprava, jako je HTTPS.

### <a name="malformed-level"></a>Poškozená úroveň

Poškozené zprávy jsou zprávy, které jsou odmítnuty zásobníkem WCF v jakékoli fázi zpracování. Poškozené zprávy jsou protokolovány tak, jak jsou: šifrované, pokud jsou tak, s nesprávnými XML a tak dále. `maxSizeOfMessageToLog`definuje velikost zprávy, která má být zaznamenána jako CDATA. Ve výchozím nastavení `maxSizeOfMessageToLog` se rovná 256. Další informace o tomto atributu naleznete v části Další možnosti.

### <a name="other-options"></a>Další možnosti

Kromě úrovní protokolování může uživatel zadat následující možnosti:

- Protokolovat celou zprávu ( `logEntireMessage` atribut): Tato hodnota určuje, zda má být zaznamenána celá zpráva (hlavička a tělo zprávy). Výchozí hodnota je `false` , což znamená, že je protokolována pouze hlavička. Toto nastavení má vliv na úrovně protokolování zpráv služby a přenosu.

- Maximální počet zpráv, které se mají protokolovat ( `maxMessagesToLog` atribut): Tato hodnota určuje maximální počet zpráv, které se mají protokolovat. K této kvótě se počítají všechny zprávy (služba, přenos a poškozené zprávy). Po dosažení kvóty je vygenerováno trasování a nebude zaznamenána žádná další zpráva. Výchozí hodnota je 10000.

- Maximální velikost zprávy na protokol ( `maxSizeOfMessageToLog` atribut): Tato hodnota určuje maximální velikost zpráv pro přihlášení v bajtech. Zprávy, které překračují limit velikosti, se neprotokolují a u této zprávy se neprovádí žádná jiná aktivita. Toto nastavení má vliv na všechny úrovně trasování. Pokud je zapnuto trasování ServiceModel, vygeneruje se trasování úrovně upozornění v prvním bodu protokolování (ServiceModelSend * nebo TransportReceive), které uživatele upozorní. Výchozí hodnota pro zprávy na úrovni služby a na úrovni přenosu je 256, zatímco výchozí hodnota pro poškozené zprávy je 4K.

  > [!CAUTION]
  > Velikost zprávy, která je vypočítána pro porovnání, `maxSizeOfMessageToLog` je velikost zprávy v paměti před serializací. Tato velikost se může lišit od skutečné délky zaznamenaného řetězce zprávy a v mnoha případech je větší než skutečná velikost. V důsledku toho nemusí být zprávy protokolovány. K tomuto faktu se můžete přihlédnout zadáním `maxSizeOfMessageToLog` atributu, který bude větší než očekávaná velikost zprávy: 10%. Kromě toho, pokud jsou poškozené zprávy protokolovány, skutečné místo na disku využité protokoly zpráv může být až o 5 časů velikosti hodnoty určené parametrem `maxSizeOfMessageToLog` .

Pokud v konfiguračním souboru není definován naslouchací proces trasování, negeneruje se výstup protokolování bez ohledu na zadanou úroveň protokolování.

Možnosti protokolování zpráv, například atributy popsané v této části, lze změnit za běhu pomocí rozhraní WMI (Windows Management Instrumentation) (WMI). To lze provést přístupem k instanci [AppDomainInfo](./wmi/appdomaininfo.md) , která zpřístupňuje tyto logické vlastnosti: `LogMessagesAtServiceLevel` , `LogMessagesAtTransportLevel` a `LogMalformedMessages` . Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale tyto možnosti nastavíte na `false` v konfiguraci, můžete je později změnit na, `true` Pokud je aplikace spuštěná. To efektivně povoluje protokolování zpráv za běhu. Podobně platí, že pokud povolíte protokolování zpráv v konfiguračním souboru, můžete ho za běhu zakázat pomocí rozhraní WMI. Další informace najdete v tématu [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](./wmi/index.md).

`source`Pole v protokolu zpráv určuje, v němž kontextu je zpráva zaznamenána: při odesílání/přijímání zprávy požadavku, pro požadavek-odpověď nebo na jednosměrnou žádost, v modelu služby nebo transportní vrstvě nebo v případě poškozené zprávy.

Pro poškozené zprávy `source` se rovná `Malformed` . V opačném případě má zdroj následující hodnoty na základě kontextu.

Pro požadavek nebo odpověď

||Odeslat žádost|Žádost o přijetí|Odeslat odpověď|Přijmout odpověď|
|-|------------------|---------------------|----------------|-------------------|
|Vrstva modelu služby|Služba<br /><br /> Úroveň<br /><br /> Odeslat<br /><br /> Žádost|Služba<br /><br /> Úroveň<br /><br /> Přijmout<br /><br /> Žádost|Služba<br /><br /> Úroveň<br /><br /> Odeslat<br /><br /> Odpovědět|Služba<br /><br /> Úroveň<br /><br /> Přijmout<br /><br /> Odpovědět|
|Transportní vrstva|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijmout|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijmout|

Jednosměrná žádost

||Odeslat žádost|Žádost o přijetí|
|-|------------------|---------------------|
|Vrstva modelu služby|Služba<br /><br /> Úroveň<br /><br /> Odeslat<br /><br /> Pohybuje|Služba<br /><br /> Úroveň<br /><br /> Přijmout<br /><br /> Pohybuje|
|Transportní vrstva|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijmout|

## <a name="message-filters"></a>Filtry zpráv

Filtry zpráv jsou definovány v `messageLogging` konfiguračním elementu `diagnostics` konfiguračního oddílu. Jsou aplikovány na úrovni služby a přenosu. Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů. Pokud není definován žádný filtr, všechny zprávy procházejí.

Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru. Syntakticky nesprávný filtr má za následek výjimku konfigurace.

Filtry také poskytují bezpečnostní funkci s použitím `nodeQuota` atributu, který omezuje maximální počet uzlů v modelu DOM elementu XPath, které lze prozkoumat tak, aby odpovídaly filtru.

Následující příklad ukazuje, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.

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

Filtry nelze použít pro tělo zprávy. Filtry, které se pokoušejí manipulovat s textem zprávy, se ze seznamu filtrů odeberou. Vygeneruje se taky událost, která to indikuje. Například následující filtr by byl odebrán z tabulky filtru.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Konfigurace vlastního naslouchacího procesu

Můžete také nakonfigurovat vlastní naslouchací proces s dalšími možnostmi. Vlastní naslouchací proces může být užitečný pro filtrování prvků PII specifických pro aplikaci ze zpráv před přihlášením. Následující příklad ukazuje vlastní konfiguraci naslouchacího procesu.

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

Měli byste si uvědomit, že `type` atribut by měl být nastaven na kvalifikovaný název sestavení typu.

## <a name="see-also"></a>Viz také

- [\<messageLogging>](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Protokolování zpráv](message-logging.md)
- [Doporučené nastavení pro trasování a protokolování zpráv](./tracing/recommended-settings-for-tracing-and-message-logging.md)
