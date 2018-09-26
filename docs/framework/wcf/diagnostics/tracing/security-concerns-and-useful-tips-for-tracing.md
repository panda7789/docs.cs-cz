---
title: Otázky zabezpečení a užitečné tipy pro trasování
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
author: BrucePerlerMS
ms.openlocfilehash: 51db352913999d5527ead5273e6488cd09d88670
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207796"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Otázky zabezpečení a užitečné tipy pro trasování
Toto téma popisuje, jak můžete chránit citlivé informace z vystaven i užitečné tipy při použití webového hostitele.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Vlastní naslouchací pomocí webového hostitele  
 Pokud vytváříte vlastní naslouchací proces trasování, byste měli vědět o možnosti, že trasování může dojít ke ztrátě v případě hostované webové služby. Dojde k recyklování WebHost vypne živý proces při má duplicitní. Však dva procesy však musí mít přístup ke stejným prostředkům nechystáte nějakou dobu, což závisí na typu naslouchacího procesu. V tomto případě, `XmlWriterTraceListener` vytvoří nový soubor trasování pro druhý proces; zatímco spravuje více procesů v rámci stejné relace trasování událostí pro Windows a poskytuje přístup ke stejnému souboru. Pokud vlastní naslouchací proces neposkytuje podobné funkce, když je soubor uzamčen dva procesy může dojít ke ztrátě trasování.  
  
 Jste měli také něco vědět, že vlastní naslouchací můžete trasování a posílání zpráv na lince, například vzdálenou databázi. Jako modul pro nasazení aplikace měli byste nakonfigurovat vlastní naslouchací procesy s ovládacím prvkem odpovídající přístup. Také byste měli použít ovládací prvek zabezpečení v žádné osobní údaje, které mohou být zveřejněny ve vzdáleném umístění.  
  
## <a name="logging-sensitive-information"></a>Protokolování citlivých informací  
 Trasování neobsahovala záhlaví zpráv, když je zpráva v oboru. Když je povoleno trasování, osobní údaje v hlavičkách specifické pro aplikace, jako je řetězec dotazu; a základní informace, jako je číslo platební karty, může být viditelné v protokolech. Nástroje pro nasazení aplikace je zodpovědná za řízení přístupu na soubory konfigurace a sledování. Pokud nechcete, aby tento druh informací viditelný, měli zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokoly trasování.  
  
 Následující tipy vám mohou pomoci při zabránit neúmyslnému zveřejnění obsahu souboru trasování:  
  
-   Ujistěte se, že v protokolu, které soubory jsou chráněné pomocí řízení přístupu obsahuje seznam (ACL) ve webového hostitele i scénáře hostování na vlastním serveru.  
  
-   Zvolte příponu souboru, která nelze zpracovat v snadno pomocí nějaké webové žádosti. Například přípona souboru .xml není bezpečná volba. Příručka věnovaná IIS zobrazíte seznam přípon, které se dají obsluhovat můžete zkontrolovat.  
  
-   Zadejte absolutní cestu k umístění souboru protokolu, který by měla být mimo virtuální kořenový adresář webového hostitele veřejného adresáře tak, aby přistupuje pomocí webového prohlížeče třetí strana.  
  
 Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII) jako je například uživatelské jméno a heslo nejsou protokolovány v trasování a nezpůsobuje protokolování zpráv. Správce počítače, ale můžete použít `enableLoggingKnownPII` atribut `machineSettings` prvek souboru Machine.config tak, aby povolovala aplikace spuštěné na počítači pro přihlášení známého identifikovatelné osobní údaje (PII) následujícím způsobem:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` existuje element mimo souboru Machine.config, systém vyvolá <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Změny jsou platné pouze při spuštění nebo restartování aplikace. Událost se protokoluje při spuštění oba atributy jsou nastavena na hodnotu `true`. Pokud je také zaznamenána událost `logKnownPii` je nastavena na `true` ale `enableLoggingKnownPii` je `false`.  
  
 Další informace o protokolování identifikovatelné osobní údaje, najdete v části [bezpečnostní uzamčení PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) vzorku.  
  
 Správce počítače a nástroje pro nasazení aplikace by měly využít extrémně opatrní při používání těchto dvou přepínače. Pokud je povoleno protokolování identifikovatelné osobní údaje, jsou protokolovány zabezpečení klíčů a identifikovatelné osobní údaje. Pokud je zakázaná, specifické pro aplikaci a citlivá data zaprotokolována v záhlaví zprávy a texty. Podrobnější informace o ochraně osobních údajů a ochranu identifikovatelné osobní údaje z vystaven, naleznete v tématu [ochrana osobních údajů uživatelů](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Navíc je IP adresa odesílatele zprávy zaprotokolována jednou za připojení pro přenosy tohoto připojení objektově orientovaného a jednou za jinak byla odeslána zpráva. To se provádí bez souhlasu odesílatele. Protokolování se však pouze dochází na úrovni informace nebo podrobné trasování, které nejsou výchozí nebo doporučená úrovní trasování v produkčním prostředí, s výjimkou živé ladění.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
