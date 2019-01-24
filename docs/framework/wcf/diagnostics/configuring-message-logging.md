---
title: Konfigurace protokolování zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: f57385b930ce533de3ff12b0dbd363690f04082d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636011"
---
# <a name="configuring-message-logging"></a>Konfigurace protokolování zpráv
Toto téma popisuje, jak nakonfigurovat protokolování zpráv pro různé scénáře.  
  
## <a name="enabling-message-logging"></a>Povolení protokolování zpráv  
 Windows Communication Foundation (WCF) protokolu zpráv ve výchozím nastavení. K aktivaci protokolování zpráv, musíte přidat naslouchací proces trasování do `System.ServiceModel.MessageLogging` trasování a nastavte atributy `<messagelogging>` element v konfiguračním souboru.  
  
 Následující příklad ukazuje, jak povolit protokolování a určit další možnosti.  
  
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
  
 Další informace o nastavení protokolování zpráv najdete v tématu [doporučené nastavení pro trasování a protokolování zpráv](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Můžete použít `add` zadat název a typ naslouchací proces, který chcete použít. V konfiguraci příkladu naslouchací proces má název "zprávy" a přidá standardní naslouchací proces trasování rozhraní .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ, který má použít. Pokud používáte `System.Diagnostics.XmlWriterTraceListener`, musíte zadat název a umístění souboru výstupu v konfiguračním souboru. To se provádí nastavením `initializeData` k názvu souboru protokolu. Jinak systém vyvolá výjimku. Můžete také implementovat vlastní naslouchací proces, který vysílá protokoluje události do souboru výchozí.  
  
> [!NOTE]
>  Protože protokolování zpráv přistupuje k místa na disku, byste měli omezit počet zpráv, které se zapisují na disk pro konkrétní službu. Při dosažení limitu zprávy trasování na úrovni informace je vytvořen a zastavte všechny aktivity. protokolování zpráv.  
  
 Úroveň protokolování, jakož i další možnosti jsou popsány v části Možnosti a úrovně protokolování.  
  
 `switchValue` Atribut `source` je platná pouze pro trasování. Pokud zadáte `switchValue` atribut pro `System.ServiceModel.MessageLogging` zdroj trasování jako následující, nemá žádný vliv.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 Pokud chcete zakázat zdroj trasování, měli byste použít `logMessagesAtServiceLevel`, `logMalformedMessages`, a `logMessagesAtTransportLevel` atributy `messageLogging` element místo. Tyto atributy byste měli nastavit na `false`. To můžete udělat pomocí konfiguračního souboru v předcházejícím příkladu, přes uživatelské rozhraní editoru konfigurace rozhraní nebo pomocí rozhraní WMI. Další informace o nástroji pro Editor konfigurace najdete v tématu [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Další informace o rozhraní WMI najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Možnosti a úrovně protokolování  
 Pro příchozí zprávy se stane protokolování ihned poté, co je vytvořen zprávy, okamžitě předtím, než získá zprávu do uživatelského kódu na úrovni služby, a když se zjistí špatně vytvořené zprávy.  
  
 Odchozí zprávy protokolování se stane hned po zpráva opustí uživatelský kód a bezprostředně před zprávy přejde na lince.  
  
 Zprávy ve dvou různých úrovních, služby a přenosu protokolu WCF. Špatně vytvořené zprávy jsou také zaznamenána. Tři kategorie jsou na sobě nezávislé a může být aktivováno zvlášť v konfiguraci.  
  
 Úroveň protokolování můžete řídit tak, že nastavíte `logMessagesAtServiceLevel`, `logMalformedMessages`, a `logMessagesAtTransportLevel` atributy `messageLogging` elementu.  
  
### <a name="service-level"></a>Úrovně služeb  
 Chystáte se aktivovalo (přijímání) nebo ponechat (odesílání) jsou zprávy zaprotokolované v této vrstvě uživatelského kódu. Pokud filtry jste definovali, budou protokolovány jen zprávy, které odpovídají filtrům. V opačném případě se protokolují všechny zprávy na úrovni služby. Na této úrovni, s výjimkou zpráv spolehlivého zasílání zpráv jsou také zaznamenány infrastruktury zprávy (transakce, protokolu peer channel a zabezpečení). U zpráv s datovým proudem se protokolují pouze záhlaví. Kromě toho zabezpečených zpráv jsou protokolovány dešifrovat na této úrovni.  
  
### <a name="transport-level"></a>Úroveň přenosu  
 Zprávy zaprotokolované v této vrstvě připraveni být kódován nebo dekódován pro nebo po letenky na lince. Pokud filtry jste definovali, budou protokolovány jen zprávy, které odpovídají filtrům. V opačném případě se protokolují všechny zprávy v přenosové vrstvě. Všechny zprávy infrastruktury jsou protokolovány v této vrstvě, včetně zpráv spolehlivého zasílání zpráv. U zpráv s datovým proudem se protokolují pouze záhlaví. Kromě toho zabezpečených zpráv jsou protokolovány jako zašifrovaná na této úrovni, kromě případu, kdy zabezpečeného přenosu, jako se používá protokol HTTPS.  
  
### <a name="malformed-level"></a>Poškozená úroveň  
 Špatně vytvořené zprávy jsou zpráv, které jsou odmítnuty zásobníkem WCF v jakékoli fázi zpracování. Jsou špatně vytvořené zprávy zaznamenány jako-se: šifrovaná, pokud jsou, bez správných XML a tak dále. `maxSizeOfMessageToLog` definovaná velikost zprávy, která se zaznamená jako CDATA. Ve výchozím nastavení `maxSizeOfMessageToLog` je rovna 256 kB. Další informace o tomto atributu naleznete v části Další možnosti.  
  
### <a name="other-options"></a>Další možnosti  
 Kromě úrovní protokolování může uživatel zadat následující možnosti:  
  
-   Protokolovat celá zpráva (`logEntireMessage` atribut): Tato hodnota určuje, zda je zaznamenána celá zpráva (hlavička a tělo zprávy). Výchozí hodnota je `false`, což znamená, že je zaznamenána pouze záhlaví. Toto nastavení má vliv na služby a přenosu úrovně protokolování zpráv...  
  
-   Maximální počet zaznamenavaných zpráv (`maxMessagesToLog` atribut): Tato hodnota určuje maximální počet zaznamenavaných zpráv. Všechny zprávy (služba, přenos a špatně vytvořené zprávy) se započítává této kvóty. Po dosažení kvóty trasování je vygenerován a je zaznamenána žádná další zpráva. Výchozí hodnota je 10000.  
  
-   Maximální velikost zaznamenávané zprávy (`maxSizeOfMessageToLog` atribut): Tato hodnota určuje maximální velikost zprávy do protokolu v bajtech. Nejsou zaznamenána zprávy, které překračují omezení velikosti a žádná další aktivita se provádí pro tuto zprávu. Toto nastavení ovlivňuje všechny úrovně trasování. Je-li ServiceModel trasování na, úroveň trasování varování je vygenerován v prvním bodu protokolování (ServiceModelSend * nebo TransportReceive) a upozorňovaly uživatele. Výchozí hodnota pro služby úrovně a přenosu úrovně zprávy je 256 kB, výchozí hodnota pro špatně vytvořené zprávy je 4 kB.  
  
    > [!CAUTION]
    >  Velikost zprávy, které je vypočítán nímž bude porovnáváno `maxSizeOfMessageToLog` je velikosti zprávy v paměti před serializací. Tato velikost se může lišit od skutečná délka řetězce zprávy, která není přihlašováno a v mnoha případech je větší než skutečná velikost. V důsledku toho nemusí zaznamenávané zprávy. Můžete pro tuto skutečnost tak, že zadáte účet `maxSizeOfMessageToLog` atribut 10 % je větší než velikost očekávaná zpráva. Kromě toho, pokud jsou špatně vytvořené zprávy zaznamenány, místo na disku skutečné využívaných protokolů zpráv může být až 5krát velikost hodnotu zadanou pomocí `maxSizeOfMessageToLog`.  
  
 Pokud v konfiguračním souboru není definován žádný naslouchací proces trasování, nebude vygenerován žádný výstup protokolování bez ohledu na zadanou úroveň.  
  
 Možnosti protokolování zprávy, jako je například atributy popsané v této části můžete změnit za běhu pomocí Windows Management Instrumentation (WMI). To můžete udělat přechodem k [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instanci, která poskytuje tyto logické vlastnosti: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, a `LogMalformedMessages`. Proto pokud nakonfigurovat naslouchací proces trasování pro protokolování zpráv, ale nastavit tyto možnosti na `false` v konfiguraci, můžete později změnit jejich `true` při spouštění aplikace. To umožňuje efektivní protokolování zpráv za běhu. Podobně pokud povolíte protokolování. v konfiguračním souboru, můžete ho zakázat za běhu pomocí rozhraní WMI. Další informace najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 `source` Určuje pole v protokolu zpráv v daném kontextu se protokoluje zprávy: při odesílání nebo přijímání zprávu požadavku pro požadavek odpověď nebo způsob 1 žádost, ve vrstvě služeb modelu nebo přenosu nebo v případě poškozená zpráva.  
  
 Pro špatně vytvořené zprávy `source` rovná `Malformed`. V opačném případě zdroj má následující hodnoty na základě kontextu.  
  
 Pro žádost odpověď  
  
||Odeslání požadavku|Požadavku přijetí|Odeslání odpovědi|Přijmout odpověď|  
|-|------------------|---------------------|----------------|-------------------|  
|Vrstva modelu služby|Služba<br /><br /> úroveň<br /><br /> Odeslat<br /><br /> Žádost|Služba<br /><br /> úroveň<br /><br /> Zobrazit<br /><br /> Žádost|Služba<br /><br /> úroveň<br /><br /> Odeslat<br /><br /> Odpověď|Služba<br /><br /> úroveň<br /><br /> Zobrazit<br /><br /> Odpověď|  
|přenosové vrstvy|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Zobrazit|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Zobrazit|  
  
 Pro jednosměrný požadavek  
  
||Odeslání požadavku|Požadavku přijetí|  
|-|------------------|---------------------|  
|Vrstva modelu služby|Služba<br /><br /> úroveň<br /><br /> Odeslat<br /><br /> Datagram|Služba<br /><br /> úroveň<br /><br /> Zobrazit<br /><br /> Datagram|  
|přenosové vrstvy|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Zobrazit|  
  
## <a name="message-filters"></a>Filtry zpráv  
 Filtry zpráv jsou definovány v `messageLogging` element konfigurace `diagnostics` konfigurační oddíl. Tato nastavení použijí na úrovni služby a přenosu. Když jsou definovány jeden nebo více filtrů, jsou protokolovány jen zprávy, které odpovídají alespoň jeden z filtrů. Pokud není definován žádný filtr, všechny zprávy předávání.  
  
 Filtry podporuje úplnou syntaxi XPath a nastavení se použijí v pořadí, ve kterém se zobrazují v konfiguračním souboru. Filtr syntakticky nesprávný výsledkem výjimka v konfiguraci.  
  
 Také poskytnout filtry, pomocí funkci bezpečnosti `nodeQuota` atribut, který omezí maximální počet uzlů v modelu DOM jazyka XPath, které se dají prozkoumat tak, aby odpovídaly filtru.  
  
 Následující příklad ukazuje, jak konfigurovat filtr pouze zprávy této záznamy, které mají záhlaví SOAP.  
  
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
  
 Filtry nelze použít pro text zprávy. Filtry, které se pokoušejí k manipulaci s text zprávy se odeberou ze seznamu filtrů. Událost je také vygenerován, která označuje to. Například následující filtr se odeberou ze tabulce filtrů.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Konfigurace vlastní naslouchací proces  
 Můžete také nakonfigurovat vlastní naslouchací proces s dalšími možnostmi. Vlastní naslouchací proces může být užitečné při filtrování elementy identifikovatelné osobní údaje specifické pro aplikace ze zprávy před přihlášením. Následující příklad ukazuje vlastní naslouchací proces konfigurace.  
  
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
  
 Byste měli vědět, `type` atribut by měl být nastaven na kvalifikovaný název typu.  
  
## <a name="see-also"></a>Viz také:
- [\<messageLogging>](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
- [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Doporučené nastavení pro trasování a protokolování zpráv](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
