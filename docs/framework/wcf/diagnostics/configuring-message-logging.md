---
title: "Konfigurace protokolování zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e42b4007d438fbabaf497981b654415ca7eeb415
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-message-logging"></a>Konfigurace protokolování zpráv
Toto téma popisuje, jak můžete nakonfigurovat protokolování zpráv pro různé scénáře.  
  
## <a name="enabling-message-logging"></a>Povolení protokolování zpráv  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]ve výchozím nastavení neprotokoluje zprávy. K aktivaci protokolování zpráv, je nutné přidat naslouchací k `System.ServiceModel.MessageLogging` zdroj trasování a nastavit atributy `<messagelogging>` element v konfiguračním souboru.  
  
 Následující příklad ukazuje, jak povolit protokolování a nastavte další možnosti.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nastavení protokolování zpráv najdete v tématu [doporučená nastavení pro trasování a protokolování zpráv](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Můžete použít `add` a zadat název a typ naslouchací proces, který chcete použít. V konfiguraci příklad naslouchací proces má název "zprávy" a přidá standardní naslouchací proces trasování rozhraní .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ, který má použít. Pokud používáte `System.Diagnostics.XmlWriterTraceListener`, je nutné zadat umístění výstupního souboru a název v konfiguračním souboru. To se provádí nastavením `initializeData` k názvu souboru protokolu. V systému, jinak vyvolá výjimku. Můžete také implementovat vlastní naslouchací proces, který vysílá protokoluje události do souboru výchozí.  
  
> [!NOTE]
>  Protože protokolování zpráv přistupuje k místa na disku, měli byste omezit počet zpráv, které se zapisují na disk pro konkrétní službu. Po dosažení limitu zprávy, se vytvářejí na úrovni informace trasování a zastavit všechny aktivity protokolování zpráv.  
  
 Úroveň protokolování, jakož i další možnosti jsou popsané v části protokolování úroveň a možnosti.  
  
 `switchValue` Atribut `source` je platná pouze pro trasování. Pokud zadáte `switchValue` atribut pro `System.ServiceModel.MessageLogging` zdroj trasování jako následuje, nemá žádný účinek.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 Pokud chcete zakázat zdroj trasování, měli byste použít `logMessagesAtServiceLevel`, `logMalformedMessages`, a `logMessagesAtTransportLevel` atributy `messageLogging` element místo. Měli byste nastavit tyto atributy hodnotu `false`. To můžete provést pomocí konfiguračního souboru v předchozím příkladu kódu, přes rozhraní Editor konfigurací uživatelského rozhraní nebo pomocí rozhraní WMI. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Nástroj Configuration Editor, najdete v části [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Rozhraní WMI, najdete v části [pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Úrovně protokolování a možnosti  
 Pro příchozí zprávy protokolování dojde ihned po zprávy je vytvořen, bezprostředně před zpráva získá kódu uživatele na úrovni služby, a při zjištění poškozených zpráv.  
  
 Odchozí zprávy protokolování se stane ihned po zpráva opustí uživatelského kódu a bezprostředně před zpráva je uložena v drátové síti.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zaznamenává zprávy na dvou různých úrovních, služby a přenosu. Také se protokolují poškozených zpráv. Tři kategorie jsou od sebe navzájem nezávislé a může být aktivovaný nezávisle v konfiguraci.  
  
 Úroveň protokolování lze řídit nastavení `logMessagesAtServiceLevel`, `logMalformedMessages`, a `logMessagesAtTransportLevel` atributy `messageLogging` elementu.  
  
### <a name="service-level"></a>Úrovně služeb  
 Zprávy zaznamenané v této vrstvě se chystáte zadat (na příjem) nebo nechte (při odesílání) uživatelského kódu. Pokud byly definovány filtry, jsou protokolovány jen zprávy, které splňují podmínky filtrů. Jinak jsou protokolovány všechny zprávy na úrovni služby. Na této úrovni, s výjimkou zpráv spolehlivého zasílání zpráv jsou také protokolovány infrastruktury zprávy (transakce, rovnocenného kanálu a zabezpečení). V proudu zpráv jsou protokolovány pouze záhlaví. Kromě toho zabezpečených zpráv jsou protokolovány dešifrovat na této úrovni.  
  
### <a name="transport-level"></a>Transportní  
 Kódování nebo dekódovat pro nebo po Transport přenášený připraveni zprávy zaznamenané v této vrstvě. Pokud byly definovány filtry, jsou protokolovány jen zprávy, které splňují podmínky filtrů. Jinak jsou protokolovány všechny zprávy v přenosové vrstvě. Všechny zprávy infrastruktury jsou protokolovány v této vrstvě, včetně zpráv spolehlivého zasílání zpráv. V proudu zpráv jsou protokolovány pouze záhlaví. Kromě toho zabezpečených zpráv jsou protokolovány jako zašifrovaná na této úrovni, kromě případu, kdy zabezpečený přenos, jako se používá protokol HTTPS.  
  
### <a name="malformed-level"></a>Chybná úroveň  
 Poškozených zpráv jsou zprávy, které jsou odmítnut [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zásobníku v jakékoli fázi zpracování. Chybná zprávy se zaznamenávají jako-se: zašifrované, pokud jsou tedy XML bez správné a tak dále. `maxSizeOfMessageToLog`velikost zprávy, která je zaznamenána jako CDATA definován. Ve výchozím nastavení `maxSizeOfMessageToLog` je rovna 256 kB. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tento atribut, najdete v části Další možnosti.  
  
### <a name="other-options"></a>Další možnosti  
 Kromě úrovně protokolování můžete uživatele určete následující možnosti:  
  
-   Protokolovat celou zprávu (`logEntireMessage` atribut): Tato hodnota určuje, zda je zaznamenána celé zprávy (záhlaví zprávy a text). Výchozí hodnota je `false`, což znamená, že pouze hlavičku protokolu. Toto nastavení má vliv služby a přenosu úrovně protokolování zpráv...  
  
-   Maximální počet zpráv do protokolu (`maxMessagesToLog` atribut): Tato hodnota určuje maximální počet zpráv do protokolu. Všechny zprávy (služby, přenos a poškozených zpráv), se počítají směrem tuto kvótu. Když je dosaženo kvóty, jsou vydávány trasování a je zaznamenána žádná další zpráva. Výchozí hodnota je 10 000.  
  
-   Maximální velikost zprávy do protokolu (`maxSizeOfMessageToLog` atribut): Tato hodnota určuje maximální velikost zprávy do protokolu v bajtech. Zprávy, které překračují limit velikosti se neprotokolují a žádná další aktivita se provádí pro zprávy. Toto nastavení ovlivňuje všechny úrovně trasování. Pokud ServiceModel trasování na, upozornění úrovně trasování jsou vydávány v prvním bodu protokolování (ServiceModelSend * nebo TransportReceive) pro uživatele. Výchozí hodnota pro služby úrovně a přenosu úrovně zprávy je 256 kB, výchozí hodnota pro poškozených zpráv při 4 kB.  
  
    > [!CAUTION]
    >  Velikost zprávy, počítaný pro porovnání `maxSizeOfMessageToLog` je velikost zprávy v paměti před serializace. Tato velikost se může lišit od skutečné délce zpráva řetězec, který je přihlášen a v mnoha případech je větší než skutečná velikost. V důsledku toho nemusí být do protokolu zpráv. Můžete účet pro tento fakt zadáním `maxSizeOfMessageToLog` atributu na 10 % větší než velikost očekávaná zpráva. Kromě toho, pokud se neprotokolují poškozených zpráv, skutečný místa využívaných protokolů zpráv může být až 5 x velikost hodnotu zadanou pomocí `maxSizeOfMessageToLog`.  
  
 Pokud žádné naslouchací proces trasování je definována v konfiguračním souboru, nevygeneruje žádný výstup protokolování bez ohledu na zadanou úroveň.  
  
 Možnosti protokolování zpráv, jako je například atributy popsaných v této části můžete změnit za běhu pomocí služby Windows Management Instrumentation (WMI). To lze provést pomocí přístupu k [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instanci, která zpřístupňuje tyto logická hodnota vlastnosti: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, a `LogMalformedMessages`. Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale nastavit tyto možnosti pro `false` v konfiguraci, můžete později změnit, aby `true` při spuštění aplikace. To umožňuje efektivní protokolování zpráv za běhu. Podobně pokud povolíte protokolování v konfiguračním souboru zpráv, ji můžete vypnout v době běhu pomocí služby WMI. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 `source` Určuje pole v protokolu zpráv v kontextu, která je zaznamenána zpráva: při odesílání nebo přijímání zprávu požadavku pro požadavek odpověď nebo 1 pro dvoucestné žádost, ve model nebo přenos vrstvě služby nebo v případě chybnou zprávu.  
  
 Pro poškozených zpráv `source` rovná `Malformed`. Zdroj, jinak hodnota má následující hodnoty na základě kontextu.  
  
 Pro požadavek nebo odpověď  
  
||Odeslání požadavku|Přijímání požadavků|Odeslání odpovědi|Přijmout odpověď|  
|-|------------------|---------------------|----------------|-------------------|  
|Vrstva modelu služby|Služba<br /><br /> úroveň<br /><br /> Odeslat<br /><br /> Požadavek|Služba<br /><br /> úroveň<br /><br /> Přijímat<br /><br /> Požadavek|Služba<br /><br /> úroveň<br /><br /> Odeslat<br /><br /> odpověď|Služba<br /><br /> úroveň<br /><br /> Přijímat<br /><br /> odpověď|  
|přenosové vrstvy|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijímat|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijímat|  
  
 Jednosměrné požadavku  
  
||Odeslání požadavku|Přijímání požadavků|  
|-|------------------|---------------------|  
|Vrstva modelu služby|Služba<br /><br /> úroveň<br /><br /> Odeslat<br /><br /> Datagram|Služba<br /><br /> úroveň<br /><br /> Přijímat<br /><br /> Datagram|  
|přenosové vrstvy|Přenos<br /><br /> Odeslat|Přenos<br /><br /> Přijímat|  
  
## <a name="message-filters"></a>Filtry zpráv  
 Filtry zpráv jsou definovány v `messageLogging` element konfigurace `diagnostics` konfigurační oddíl. Tato nastavení použijí na úrovni služby a přenosu. Když jsou definovány jeden nebo více filtrů, jsou protokolovány pouze zprávy, které odpovídají alespoň jeden z filtrů. Pokud je definován žádný filtr, všechny zprávy předávat.  
  
 Filtry podporují úplnou syntaxí XPath a aplikují v pořadí, ve kterém se zobrazují v konfiguračním souboru. Správnou syntaxi filtr výsledkem výjimka v konfiguraci.  
  
 Filtry také poskytují funkce zabezpečení pomocí `nodeQuota` atribut, který omezuje maximální počet uzlů v modelu DOM jazyka XPath, který může být prověřen tak, aby odpovídaly filtru.  
  
 Následující příklad ukazuje, jak konfigurovat filtr této zprávy pouze záznamy, které mají oddíl hlavičky SOAP.  
  
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
  
 Filtry nelze použít pro tělo zprávy. Filtry, které se pokoušejí o manipulaci s tělo zprávy, které se odeberou ze seznamu filtrů. Událost je také vygenerované určující to. Například filtr se odeberou z filtru tabulky.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Konfigurace vlastní naslouchací proces  
 Můžete také nakonfigurovat vlastní naslouchací proces s další možnosti. Vlastní naslouchací proces může být užitečné při filtrování specifické pro aplikaci PII elementy ze zprávy před protokolování. Následující příklad ukazuje vlastní naslouchací proces konfigurace.  
  
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
  
 Je třeba si uvědomit, `type` atribut by měl být nastaven na kvalifikovaný název typu.  
  
## <a name="see-also"></a>Viz také  
 [\<messageLogging >](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)  
 [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Doporučená nastavení pro trasování a protokolování zpráv](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
