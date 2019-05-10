---
title: Zajištění zabezpečení pro protokolování zpráv
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: e1503249d5fd33e320ccb6642eb6e97c3029ba85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651826"
---
# <a name="security-concerns-for-message-logging"></a>Zajištění zabezpečení pro protokolování zpráv
Toto téma popisuje, jak můžete chránit citlivá data před vystaven protokolů zpráv, jakož i události generované modulem protokolování zpráv.  
  
## <a name="security-concerns"></a>Zajištění zabezpečení  
  
### <a name="logging-sensitive-information"></a>Protokolování citlivých informací  
 Windows Communication Foundation (WCF) neprovede žádné změny všechna data v konkrétní aplikaci záhlaví a text. WCF také osobní informace v záhlaví specifické pro aplikaci a data těla nesleduje.  
  
 Pokud je povoleno protokolování zpráv, osobní údaje v hlavičkách specifické pro aplikace, jako je řetězec dotazu; a základní informace, jako je číslo platební karty, může být viditelné v protokolech. Nástroje pro nasazení aplikace je zodpovědná za řízení přístupu na soubory konfigurace a protokolu. Pokud nechcete, aby tento druh informací viditelný, by měl volitelný zákaz protokolování nebo odfiltrovat část dat, pokud chcete sdílet protokoly.  
  
 Následující tipy vám mohou pomoci při zabránit neúmyslnému zveřejnění obsahu souboru protokolu:  
  
- Ujistěte se, že v protokolu, které soubory jsou chráněné pomocí řízení přístupu uvádí (ACL) ve webového hostitele i scénáře hostování na vlastním serveru.  
  
- Zvolte příponu souboru, která nelze zpracovat v snadno pomocí nějaké webové žádosti. Například přípona souboru .xml není bezpečná volba. Příručka věnovaná Internetové informační služby (IIS) Chcete-li zobrazit seznam rozšíření, která se dají obsluhovat, můžete zkontrolovat.  
  
- Zadejte absolutní cestu k umístění souboru protokolu, který by měla být mimo hostitele vroot veřejné složky webu tak, aby přistupuje pomocí webového prohlížeče třetí strana.  
  
 Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII) jako je například uživatelské jméno a heslo nejsou protokolovány v trasování a nezpůsobuje protokolování zpráv. Správce počítače, ale můžete použít `enableLoggingKnownPII` atribut `machineSettings` element tak, aby povolovala aplikace spuštěné na počítači pro přihlášení známého identifikovatelné osobní údaje (PII) v souboru Machine.config. Následující konfigurace ukazuje, jak to udělat:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Pak můžete použít nástroje pro nasazení aplikace `logKnownPii` atributu v souboru App.config nebo Web.config povolení protokolování identifikovatelné osobní údaje následujícím způsobem:  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
```  
  
 Pouze, pokud jsou obě nastavení `true` je povoleno protokolování identifikovatelné osobní údaje. Kombinací dvou přepínače umožňuje flexibilitu pro přihlášení známého PII pro každou aplikaci.  
  
> [!IMPORTANT]
>  V [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` a `logKnownPii` příznaky musí být také nastavena na `true` v souboru Web.config nebo App.config souboru povolení protokolování identifikovatelné osobní údaje, tak, jak zobrazit v následujícím příkladu `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Byste měli vědět, že pokud zadáte dvě nebo více vlastních zdrojů v konfiguračním souboru, se čtou jenom atributy první zdroj. Další se ignorují. To znamená, že pro následující App.config soubor, identifikovatelné osobní údaje se neprotokolují pro oba zdroje i v případě, že je explicitně povoleno protokolování identifikovatelné osobní údaje pro druhý zdroj.  
  
```xml  
<system.diagnostics>  
   <sources>  
      <source name="System.ServiceModel.MessageLogging"  
              logKnownPii="false">  
              <listeners>  
                 <add name="messages"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\messages.svclog" />  
              </listeners>  
            </source>  
      <source name="System.ServiceModel"   
              logKnownPii="true">  
              <listeners>  
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` existuje element mimo souboru Machine.config, systém vyvolá <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Změny jsou platné pouze při spuštění nebo restartování aplikace. Událost se protokoluje při spuštění oba atributy jsou nastavena na hodnotu `true`. Pokud je také zaznamenána událost `logKnownPii` je nastavena na `true` ale `enableLoggingKnownPii` je `false`.  
  
 Správce počítače a nástroje pro nasazení aplikace by měly využít extrémně opatrní při používání těchto dvou přepínače. Pokud je povoleno protokolování identifikovatelné osobní údaje, jsou protokolovány zabezpečení klíčů a identifikovatelné osobní údaje. Pokud je zakázaná, specifické pro aplikaci a citlivá data zaprotokolována v záhlaví zprávy a texty. Podrobnější informace o ochranu osobních údajů a o ochraně před vystavením identifikovatelné osobní údaje, najdete v části [ochrana osobních údajů uživatelů](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  PII není skryté v špatně vytvořené zprávy. Například messaged jsou protokolovány jako – bez jakékoli změny. Atributy uvedené dříve nemají žádný vliv na to.  
  
### <a name="custom-trace-listener"></a>Vlastní naslouchací  
 Přidání vlastní naslouchací na protokolování zpráv je zdroj trasování oprávnění, které by měly být omezené na správce. Důvodem je, že škodlivý vlastní naslouchání lze nastavit pro odesílání zpráv vzdáleně, což vede k citlivým informacím. Kromě toho pokud nakonfigurujete vlastní naslouchací proces pro odesílání zpráv na lince, jako je třeba do vzdálené databáze by měl vynutit vhodné řízení přístupu na protokoly zpráv ve vzdáleném počítači.  
  
## <a name="events-triggered-by-message-logging"></a>Události aktivované protokolování zpráv  
 Následující seznam obsahuje všechny události, protože ho vygeneroval protokolování zpráv.  
  
- Přihlášení se zobrazí zpráva: Tato událost je vygenerován při protokolování zpráv je povolená v konfiguraci nebo prostřednictvím rozhraní WMI. Obsah události je "zprávy bylo zapnuto protokolování. Citlivá informace může být přihlášena v podobě prostého textu, i v případě, že byly šifrované na lince, například zpráv."  
  
- Zpráva o odhlášení: Tato událost je vygenerován při protokolování zpráv je zakázán prostřednictvím rozhraní WMI. Obsah události je "Zpráva protokolování vypnuté."  
  
- Přihlášení známého PII: Tato událost je vygenerován, pokud je povoleno přihlášení známého PII. K tomu dojde při `enableLoggingKnownPii` atribut `machineSettings` prvek souboru Machine.config je nastaven na `true`a `logKnownPii` atribut `source` je prvek v souboru App.config nebo Web.config nastaven na `true`.  
  
- Přihlášení známého PII není povoleno: Tato událost je vygenerován při přihlášení známého PII není povoleno. K tomu dojde při `logKnownPii` atribut `source` je prvek v souboru App.config nebo Web.config nastaven na `true`, ale `enableLoggingKnownPii` atribut `machineSettings` prvek souboru Machine.config je nastaven na `false`. Není vyvolána žádná výjimka.  
  
 Tyto události můžete zobrazit v nástroji Prohlížeč událostí, který je součástí Windows. Další informace najdete v části [protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Otázky zabezpečení a užitečné tipy pro trasování](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
