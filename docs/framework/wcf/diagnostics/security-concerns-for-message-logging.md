---
title: Zajištění zabezpečení pro protokolování zpráv
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c8b2fe3300bacc76e63f9d533c613171d03600d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-concerns-for-message-logging"></a>Zajištění zabezpečení pro protokolování zpráv
Toto téma popisuje, jak můžete chránit citlivá data vystavení v protokolů zpráv, jakož i událostí generovaných protokolování zpráv.  
  
## <a name="security-concerns"></a>Aspekty zabezpečení  
  
### <a name="logging-sensitive-information"></a>Protokolování citlivé informace.  
 Windows Communication Foundation (WCF) nemění žádná data v záhlaví specifické pro aplikaci a text. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] také nesleduje osobní údaje v záhlaví konkrétní aplikace a data textu.  
  
 Když je povoleno protokolování zpráv, osobní údaje v hlavičkách specifické pro aplikace, jako je řetězec dotazu; a body informace, například číslo platební karty, se může stát viditelné v protokolech. Nástroje pro nasazení aplikace je zodpovědná za prosadit řízení přístupu na soubory konfigurace a protokolu. Pokud nechcete, aby tento druh informací viditelný, měli vypnout protokolování nebo odfiltrovat část dat, pokud chcete sdílet v protokolech.  
  
 Následující tipy vám může pomoct zabránit neúmyslnému zveřejnění obsahu souboru protokolu:  
  
-   Zajistěte, aby v protokolu, které soubory jsou chráněné pomocí řízení přístupu jsou uvedené (ACL) v webového hostitele i scénáře hostování na vlastním serveru.  
  
-   Zvolte příponu souboru, který nelze zpracovat snadno pomocí nějaké webové žádosti. Například přípona souboru .xml není bezpečná volba. Můžete zkontrolovat v Průvodci správu Internetové informační služby (IIS) a podívejte se do seznamu přípon, které se dají obsluhovat.  
  
-   Zadejte absolutní cestu k umístění souboru protokolu, které by měla být mimo webového hostitele vroot veřejné adresář, který chcete zabránit přistupuje externí strany pomocí webového prohlížeče.  
  
 Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII), jako je například uživatelské jméno a heslo nejsou protokolovány v trasování a protokolovat zprávy. Správce počítače, ale můžete použít `enableLoggingKnownPII` atribut `machineSettings` element tak, aby povolovala aplikace spuštěna v počítači do protokolu známé identifikovatelné osobní údaje (PII) v souboru Machine.config. Následující konfigurace ukazuje, jak to udělat:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Pak můžete použít modul pro nasazení aplikace `logKnownPii` atribut v souboru App.config nebo Web.config povolení protokolování PII následujícím způsobem:  
  
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
  
 Pouze, pokud jsou obě nastavení `true` je povoleno protokolování PII. Kombinace dva přepínače umožňuje flexibilně protokolu známé PII pro každou aplikaci.  
  
> [!IMPORTANT]
>  V [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` a `logKnownPii` příznaky musí být také nastaven na `true` v souboru Web.config nebo v souboru App.config PII protokolování, tak, jak zobrazit v následujícím příkladu `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Je třeba si uvědomit, že pokud zadáte dva nebo více vlastních zdrojů v konfiguračním souboru, se čtou jenom atributy první zdroje. Další se ignorují. To znamená, že pro následující App.config souboru PII se neprotokolují pro oba zdroje i když druhý zdroj je výslovně povoleno protokolování PII.  
  
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
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` element existuje mimo souboru Machine.config, vyvolá systému <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Změny jsou platné jenom v případě, že spuštění nebo restartování aplikace. Při spuštění se zaprotokoluje událost, když oba atributy jsou nastaveny na `true`. Pokud se taky zaznamená událost `logKnownPii` je nastaven na `true` ale `enableLoggingKnownPii` je `false`.  
  
 Správce počítače a nástroje pro nasazení aplikace by měla vykonávat extrémně opatrní při používání těchto dva přepínače. Pokud je povoleno protokolování PII, jsou protokolovány zabezpečení klíčů a PII. Pokud je zakázaná, specifické pro aplikaci a citlivá data protokolovány v záhlaví zprávy a obsah. Podrobnější informace o ochranu osobních údajů a ochrana PII vystavení, naleznete v [ochraně osobních údajů uživatelů](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  V poškozených zpráv není skryté PII. Například messaged se zaznamenávají jako-je bez nutnosti jakékoli úpravy. Atributy uvedeno dříve mít žádný vliv na to.  
  
### <a name="custom-trace-listener"></a>Vlastní naslouchací  
 Přidání vlastní naslouchací na protokolování zpráv zdroj trasování je oprávnění, která by měla být omezeno na správce. Důvodem je, že škodlivý vlastní naslouchací procesy je možné nakonfigurovat na odesílání zpráv vzdáleně, což vede k citlivým informacím. Kromě toho pokud nakonfigurujete vlastní naslouchací proces pro odesílání zpráv v drátové síti, jako je třeba pro vzdálenou databázi, by měl vynutit řízení správné přístupu na protokolů zpráv ve vzdáleném počítači.  
  
## <a name="events-triggered-by-message-logging"></a>Události aktivované protokolování zpráv  
 V následujícím seznamu uvedeny všechny události vysílaných protokolování zpráv.  
  
-   Zpráva přihlašování: Tato událost je vygenerované, pokud je povoleno protokolování zpráv v konfiguraci, nebo prostřednictvím rozhraní WMI. Obsah této události je "zpráva protokolování je zapnutý. Citlivé informace může být zaznamenána ve formátu prostého textu, i v případě, že byly šifrované v drátové síti, například obsah zpráv."  
  
-   Zpráva odhlašování: Tato událost je vygenerované při protokolování zpráv je zakázán prostřednictvím rozhraní WMI. Obsah této události je "Zpráva protokolování vypnuté."  
  
-   Protokol známé PII na: Tato událost je vygenerované, pokud je povoleno protokolování známé PII. K tomu dojde při `enableLoggingKnownPii` atribut `machineSettings` element souboru Machine.config je nastaven na `true`a `logKnownPii` atribut `source` element v souboru App.config nebo Web.config je nastaven na hodnotu `true`.  
  
-   Protokolu známé PII nejsou povoleny: Tato událost je vygenerované, pokud není povoleno protokolování známé PII. K tomu dojde při `logKnownPii` atribut `source` element v souboru App.config nebo Web.config je nastaven na hodnotu `true`, ale `enableLoggingKnownPii` atribut `machineSettings` element souboru Machine.config je nastaven na `false`. Nedojde k výjimce.  
  
 Tyto události lze zobrazit v nástroji Prohlížeč událostí, která se dodává s Windows. Další informace najdete v tématu [protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Otázky zabezpečení a užitečné tipy pro trasování](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
