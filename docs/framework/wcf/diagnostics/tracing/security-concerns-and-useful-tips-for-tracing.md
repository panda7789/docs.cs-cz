---
title: Otázky zabezpečení a užitečné tipy pro trasování
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 0a09e387a4f964441f11d07a84bd492345d5b691
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578874"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Otázky zabezpečení a užitečné tipy pro trasování
V tomto tématu se dozvíte, jak můžete při použití webhosta chránit citlivé informace, které se zveřejňují, a užitečné tipy.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Použití vlastního naslouchacího procesu trasování s webhostem  
 Při psaní vlastního naslouchacího procesu trasování byste si měli být vědomi možnosti, že trasování mohou být ztracena v případě služby hostované na webu. Když se webhost recykluje, vypne živý proces, zatímco dojde ke zdvojení. Nicméně dva procesy musí mít stále přístup ke stejnému prostředku, který je závislý na typu naslouchacího procesu. V tomto případě `XmlWriterTraceListener` vytvoří nový trasovací soubor pro druhý proces; zatímco trasování událostí systému Windows spravuje více procesů v rámci stejné relace a poskytuje přístup ke stejnému souboru. Pokud váš vlastní naslouchací proces neposkytuje podobné funkce, trasování mohou být ztracena, pokud je soubor uzamčen dvěma procesy.  
  
 Také byste si měli být vědomi, že vlastní naslouchací proces trasování může odesílat trasování a zprávy na lince, například do vzdálené databáze. Jako modul pro nasazení aplikace byste měli nakonfigurovat vlastní naslouchací procesy s odpovídajícím řízením přístupu. Měli byste také použít kontrolu zabezpečení na jakékoli osobní údaje, které mohou být zveřejněny ve vzdáleném umístění.  
  
## <a name="logging-sensitive-information"></a>Protokolování citlivých informací  
 Pokud je zpráva v oboru, trasování obsahují záhlaví zpráv. Pokud je povoleno trasování, osobní informace v hlavičkách specifických pro danou aplikaci, například řetězec dotazu; a informace o textu, jako je číslo platební karty, se můžou v protokolech zobrazit. Nástroj pro nasazení aplikace zodpovídá za vynucování řízení přístupu pro konfigurační a trasovací soubory. Pokud nechcete, aby se tyto informace zobrazovaly, měli byste zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokoly trasování.  
  
 Následující tipy vám pomůžou zabránit neúmyslnému zpřístupnění obsahu trasovacího souboru:  
  
- Zajistěte, aby byly soubory protokolu chráněny seznamem Access Control (seznam ACL) jak v hostování webhost, tak i v samostatných hostitelských scénářích.  
  
- Vyberte příponu souboru, kterou nelze snadno zpracovat pomocí webové žádosti. Například Přípona souboru. XML není bezpečná volba. Seznam rozšíření, která je možné zpracovat, najdete v příručce pro správu služby IIS.  
  
- Zadejte absolutní cestu pro umístění souboru protokolu, který by měl být mimo veřejný adresář website vroot, aby k němu externí strana nezískala přes webový prohlížeč.  
  
 Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII), jako je uživatelské jméno a heslo, se v trasování a zprávách protokolu neprotokolují. Správce počítače však může použít `enableLoggingKnownPII` atribut v `machineSettings` prvku souboru Machine. config, aby umožňoval aplikacím běžícím na počítači protokolovat známé identifikovatelné osobní údaje (PII) následujícím způsobem:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
  
 Pouze v případě, že jsou obě nastavení `true` povolena protokolování PII. Kombinace dvou přepínačů umožňuje pružně protokolovat známé PII pro každou aplikaci.  
  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` element existuje mimo soubor Machine. config, vyvolá systém <xref:System.Configuration.ConfigurationErrorsException> .  
  
 Změny jsou platné pouze v případě, že je aplikace spuštěna nebo restartována. Při spuštění se protokoluje událost, když jsou oba atributy nastavené na `true` . Událost je také zaznamenána v případě `logKnownPii` , že je nastavena na, `true` ale `enableLoggingKnownPii` je `false` .  
  
 Další informace o přihlašování PII najdete v ukázce [zabezpečení PII](../../samples/pii-security-lockdown.md) – ukázka.  
  
 Při použití těchto dvou přepínačů by měl správce počítače a nástroj pro nasazení aplikace velmi opatrní. Pokud je povolené protokolování PII, zaprotokolují se bezpečnostní klíče a PII. Pokud je zakázaná, citlivá a data specifická pro aplikaci se pořád přihlásí k hlavičkám a institucím zpráv. Podrobnější diskuzi o ochraně osobních údajů a ochraně PII, která se zveřejňují, najdete v tématu [Ochrana osobních údajů uživatele](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
 Kromě toho se IP adresa odesílatele zprávy zaznamenává jednou za připojení pro přenosy orientované na připojení a jednou pro každou zprávu se poslalo jinak. To se provádí bez souhlasu odesílatele. Nicméně k tomuto protokolování dochází pouze na úrovních informace nebo podrobné trasování, které nejsou výchozí ani Doporučené úrovně trasování v produkčním prostředí, s výjimkou živého ladění.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
