---
title: Zajištění zabezpečení pro protokolování zpráv
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: b635591b7a3b07385ed48c6b1ea556139c6d77c5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044257"
---
# <a name="security-concerns-for-message-logging"></a>Zajištění zabezpečení pro protokolování zpráv
Toto téma popisuje, jak můžete chránit citlivá data před zveřejněním v protokolech zpráv a také v případě událostí generovaných protokolováním zpráv.  
  
## <a name="security-concerns"></a>Problematika zabezpečení  
  
### <a name="logging-sensitive-information"></a>Protokolování citlivých informací  
 Windows Communication Foundation (WCF) neupravuje žádná data v záhlavích a textech specifických pro danou aplikaci. WCF také nesleduje osobní údaje v záhlavích nebo textech specifických pro danou aplikaci.  
  
 Pokud je povoleno protokolování zpráv, osobní informace v hlavičkách specifických pro danou aplikaci, například řetězec dotazu; a informace o textu, jako je číslo platební karty, se můžou v protokolech zobrazit. Nástroj pro nasazení aplikace zodpovídá za vynucování řízení přístupu pro konfigurační soubory a soubory protokolů. Pokud nechcete, aby se tento druh informací zobrazoval, měli byste zakázat protokolování nebo odfiltrovat část dat, pokud chcete protokoly sdílet.  
  
 Následující tipy vám pomůžou zabránit neúmyslnému zpřístupnění obsahu souboru protokolu:  
  
- Zajistěte, aby byly soubory protokolu chráněné Access Control seznamy (ACL) ve scénářích Web-Host a samoobslužné hostování.  
  
- Vyberte příponu souboru, kterou nelze snadno zpracovat pomocí webové žádosti. Například Přípona souboru. XML není bezpečná volba. Seznam rozšíření, která je možné zpracovat, najdete v příručce pro správu služby Internetová informační služba (IIS).  
  
- Zadejte absolutní cestu k umístění souboru protokolu, který by měl být mimo veřejný adresář webového hostitele webhost, aby k němu externí strana nezískala přes webový prohlížeč.  
  
 Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII), jako je uživatelské jméno a heslo, se v trasování a zprávách protokolu neprotokolují. Správce počítače však může použít `enableLoggingKnownPII` atribut `machineSettings` v prvku souboru Machine. config, aby umožnil aplikacím běžícím na počítači protokolovat známé identifikovatelné osobní údaje (PII). Následující konfigurace ukazuje, jak to provést:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Nástroj pro nasazení aplikace může potom pomocí `logKnownPii` atributu v souboru App. config nebo Web. config povolit protokolování PII následujícím způsobem:  
  
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
  
 Pouze v případě, že `true` jsou obě nastavení povolena protokolování PII. Kombinace dvou přepínačů umožňuje pružně protokolovat známé PII pro každou aplikaci.  
  
> [!IMPORTANT]
> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `true` V příznacích `logKnownPii` `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`a musí být také nastaveno na hodnotu v souboru Web. config nebo App. config, aby bylo možné povolit protokolování PII, jak je znázorněno v následujícím příkladu. `logEntireMessage`  
  
 Měli byste si uvědomit, že pokud v konfiguračním souboru zadáte dva nebo více vlastních zdrojů, budou čteny pouze atributy prvního zdroje. Ostatní jsou ignorovány. To znamená, že pro následující soubor App. config není k dispozici protokol PII pro oba zdroje, i když je protokolování PII pro druhý zdroj explicitně povoleno.  
  
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
  
 Pokud element existuje mimo soubor Machine. config, <xref:System.Configuration.ConfigurationErrorsException>vyvolá systém. `<machineSettings enableLoggingKnownPii="Boolean"/>`  
  
 Změny jsou platné pouze v případě, že je aplikace spuštěna nebo restartována. Při spuštění se protokoluje událost, když jsou oba atributy nastavené na `true`. Událost je také zaznamenána v `logKnownPii` případě, že `true` je nastavena `false`na, ale `enableLoggingKnownPii` je.  
  
 Při použití těchto dvou přepínačů by měl správce počítače a nástroj pro nasazení aplikace velmi opatrní. Pokud je povolené protokolování PII, zaprotokolují se bezpečnostní klíče a PII. Pokud je zakázaná, citlivá a data specifická pro aplikaci se pořád přihlásí k hlavičkám a institucím zpráv. Důkladnější diskuzi o ochraně osobních údajů a ochraně PII, které se zveřejňují, najdete v tématu [Ochrana osobních údajů uživatelů](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
> PII není v poškozených zprávách skryté. Taková zpráva se protokoluje bez jakýchkoli úprav. Výše uvedené atributy nemají žádný vliv na tento parametr.  
  
### <a name="custom-trace-listener"></a>Naslouchací proces vlastního trasování  
 Přidání vlastního naslouchacího procesu trasování ve zdroji trasování protokolování zpráv je oprávnění, které by mělo být omezeno na správce. Je to proto, že škodlivá vlastní naslouchací procesy je možné nakonfigurovat tak, aby odesílala zprávy vzdáleně, což vede k odhalení citlivých informací. Kromě toho, pokud nakonfigurujete vlastní naslouchací proces tak, aby odesílal zprávy na kabel, například, do vzdálené databáze, měli byste vymáhat správné řízení přístupu v protokolech zpráv ve vzdáleném počítači.  
  
## <a name="events-triggered-by-message-logging"></a>Události aktivované protokolováním zpráv  
 Následující seznam obsahuje všechny události generované protokolováním zpráv.  
  
- Přihlašování zprávy: Tato událost je generována, pokud je povoleno protokolování zpráv v konfiguraci nebo prostřednictvím rozhraní WMI. Obsah události je zapnutý protokolování zpráv. Citlivé informace mohou být protokolovány ve formě prostého textu, i když byly zašifrovány na lince, například tělo zprávy.  
  
- Odhlášení zprávy: Tato událost je generována, když je protokolování zprávy zakázáno prostřednictvím rozhraní WMI. Obsah události je "protokolování zpráv bylo vypnuto".  
  
- Zaprotokolujte známou PII na: Tato událost je generována, když je povoleno protokolování známého PII. K tomu dojde, `enableLoggingKnownPii` když je atribut `machineSettings` v prvku souboru Machine. config `logKnownPii` nastaven na `true`hodnotu a atribut `source` elementu v souboru App. config nebo Web. config je nastaven na hodnotu `true`.  
  
- Známý PII není povolený: Tato událost je generována, pokud není povoleno protokolování známého PII. K tomu dojde v `logKnownPii` případě, že `source` atribut prvku v souboru App. config nebo Web. config je `enableLoggingKnownPii` nastaven na `true`hodnotu, ale atribut v `machineSettings` prvku souboru Machine. config je nastaven na hodnotu `false`. Není vyvolána žádná výjimka.  
  
 Tyto události lze zobrazit v nástroji Prohlížeč událostí, který je součástí systému Windows. Další informace najdete v tématu [protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Otázky zabezpečení a užitečné tipy pro trasování](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
