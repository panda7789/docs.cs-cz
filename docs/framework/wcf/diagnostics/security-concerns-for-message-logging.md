---
title: Zajištění zabezpečení pro protokolování zpráv
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: 679975be44244f10232b805a6cc2776b48ed6058
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935772"
---
# <a name="security-concerns-for-message-logging"></a>Zajištění zabezpečení pro protokolování zpráv
Toto téma popisuje, jak můžete chránit citlivá data před zveřejněním v protokolech zpráv a také v případě událostí generovaných protokolováním zpráv.  
  
## <a name="security-concerns"></a>Problematika zabezpečení  
  
### <a name="logging-sensitive-information"></a>Protokolování citlivých informací  
 Windows Communication Foundation (WCF) neupravuje žádná data v záhlavích a textech specifických pro danou aplikaci. WCF také nesleduje osobní údaje v záhlavích nebo textech specifických pro danou aplikaci.  
  
 Pokud je povoleno protokolování zpráv, osobní informace v hlavičkách specifických pro danou aplikaci, například řetězec dotazu; a informace o textu, jako je číslo platební karty, se můžou v protokolech zobrazit. Nástroj pro nasazení aplikace zodpovídá za vynucování řízení přístupu pro konfigurační soubory a soubory protokolů. Pokud nechcete, aby se tento druh informací zobrazoval, měli byste zakázat protokolování nebo odfiltrovat část dat, pokud chcete protokoly sdílet.  
  
 Následující tipy vám pomůžou zabránit neúmyslnému zpřístupnění obsahu souboru protokolu:  
  
- Zajistěte, aby byly soubory protokolu chráněné Access Control seznamy (ACL) ve scénářích Web-Host a samoobslužné hostování.  
  
- Vyberte příponu souboru, kterou nelze snadno zpracovat pomocí webové žádosti. Například Přípona souboru. XML není bezpečná volba. Seznam přípon, které se dají obsluhovat, najdete v příručce pro právu Internetové informační služby (IIS).  
  
- Zadejte absolutní cestu k umístění souboru protokolu, který by měl být mimo veřejný adresář webového hostitele webhost, aby k němu externí strana nezískala přes webový prohlížeč.  
  
 Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII), jako je uživatelské jméno a heslo, se v trasování a zprávách protokolu neprotokolují. Správce počítače však může použít atribut `enableLoggingKnownPII` v prvku `machineSettings` souboru Machine. config, aby umožnil aplikacím běžícím na počítači protokolovat známé identifikovatelné osobní údaje (PII). Následující konfigurace ukazuje, jak to provést:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Nástroj pro nasazení aplikace může potom pomocí atributu `logKnownPii` v souboru App. config nebo Web. config povolit protokolování PII následujícím způsobem:  
  
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
  
 Pouze v případě, že obě nastavení jsou `true` je povoleno protokolování PII. Kombinace dvou přepínačů umožňuje pružně protokolovat známé PII pro každou aplikaci.  
  
> [!IMPORTANT]
> V [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] musí být příznaky `logEntireMessage` a `logKnownPii` také nastaveny na `true` v souboru Web. config nebo souboru App. config, aby bylo možné povolit protokolování PII, jak je znázorněno v následujícím příkladu `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
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
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` element existuje mimo soubor Machine. config, systém vyvolá <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Změny jsou platné pouze v případě, že je aplikace spuštěna nebo restartována. Při spuštění se protokoluje událost, když jsou oba atributy nastavené na `true`. Pokud je `logKnownPii` nastavená na `true`, ale `enableLoggingKnownPii` je `false`, zaprotokoluje se taky událost.  
  
 Při použití těchto dvou přepínačů by měl správce počítače a nástroj pro nasazení aplikace velmi opatrní. Pokud je povolené protokolování PII, zaprotokolují se bezpečnostní klíče a PII. Pokud je zakázaná, citlivá a data specifická pro aplikaci se pořád přihlásí k hlavičkám a institucím zpráv. Důkladnější diskuzi o ochraně osobních údajů a ochraně PII, které se zveřejňují, najdete v tématu [Ochrana osobních údajů uživatelů](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
> [!CAUTION]
> PII není v poškozených zprávách skryté. Taková zpráva se protokoluje bez jakýchkoli úprav. Výše uvedené atributy nemají žádný vliv na tento parametr.  
  
### <a name="custom-trace-listener"></a>Naslouchací proces vlastního trasování  
 Přidání vlastního naslouchacího procesu trasování ve zdroji trasování protokolování zpráv je oprávnění, které by mělo být omezeno na správce. Je to proto, že škodlivá vlastní naslouchací procesy je možné nakonfigurovat tak, aby odesílala zprávy vzdáleně, což vede k odhalení citlivých informací. Kromě toho, pokud nakonfigurujete vlastní naslouchací proces tak, aby odesílal zprávy na kabel, například, do vzdálené databáze, měli byste vymáhat správné řízení přístupu v protokolech zpráv ve vzdáleném počítači.  
  
## <a name="events-triggered-by-message-logging"></a>Události aktivované protokolováním zpráv  
 Následující seznam obsahuje všechny události generované protokolováním zpráv.  
  
- Přihlášení k této zprávě: Tato událost je generována, pokud je povoleno protokolování zpráv v konfiguraci nebo prostřednictvím rozhraní WMI. Obsah události je zapnutý protokolování zpráv. Citlivé informace mohou být protokolovány ve formě prostého textu, i když byly zašifrovány na lince, například tělo zprávy.  
  
- Odhlášení z: Tato událost je generována, když je protokolování zpráv zakázáno prostřednictvím rozhraní WMI. Obsah události je "protokolování zpráv bylo vypnuto".  
  
- Zaznamená známou PII: Tato událost se vygeneruje, když je povolené protokolování známého PII. K tomu dojde v případě, že atribut `enableLoggingKnownPii` v prvku `machineSettings` souboru Machine. config je nastaven na hodnotu `true`a atribut `logKnownPii` `source` elementu v souboru App. config nebo Web. config je nastaven na hodnotu `true`.  
  
- Protokolované známé PII nejsou povoleny: Tato událost je generována, pokud není povoleno protokolování známého PII. K tomu dojde, když je atribut `logKnownPii` prvku `source` v souboru App. config nebo Web. config nastaven na hodnotu `true`, ale atribut `enableLoggingKnownPii` v `machineSettings` elementu Machine. config je nastaven na `false`. Žádná výjimka se nevyvolá.  
  
 Tyto události lze zobrazit v nástroji Prohlížeč událostí, který je součástí systému Windows. Další informace najdete v tématu [protokolování událostí](./event-logging/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Protokolování zpráv](message-logging.md)
- [Otázky zabezpečení a užitečné tipy pro trasování](./tracing/security-concerns-and-useful-tips-for-tracing.md)
