---
title: Otázky zabezpečení a užitečné tipy pro trasování
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185711"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Otázky zabezpečení a užitečné tipy pro trasování
Toto téma popisuje, jak můžete chránit citlivé informace před vystavením, stejně jako užitečné tipy při používání WebHost.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Použití vlastního naslouchací procestras s WebHost  
 Pokud píšete vlastní naslouchací proces trasování, měli byste si být vědomi možnosti, že trasování může dojít ke ztrátě v případě služby hostované na webu. Když WebHost recykluje, vypne živý proces, zatímco duplicitní převezme. Oba procesy však musí mít stále přístup ke stejnému prostředku po určitou dobu, což je závislé na typu naslouchací proces. V tomto případě `XmlWriterTraceListener` , vytvoří nový soubor trasování pro druhý proces; zatímco trasování událostí systému Windows spravuje více procesů v rámci stejné relace a poskytuje přístup ke stejnému souboru. Pokud vlastní naslouchací proces neposkytuje podobné funkce, trasování může být ztracena, když je soubor uzamčen dvěma procesy.  
  
 Měli byste si také být vědomi toho, že vlastní naslouchací proces trasování můžete odesílat trasování a zprávy na lince, například do vzdálené databáze. Jako nasazovač aplikací byste měli nakonfigurovat vlastní naslouchací procesy s příslušným řízením přístupu. Měli byste také použít ovládací prvek zabezpečení pro všechny osobní informace, které mohou být vystaveny na vzdáleném místě.  
  
## <a name="logging-sensitive-information"></a>Protokolování citlivých informací  
 Trasování obsahují záhlaví zpráv, pokud je zpráva v oboru. Je-li vektorizace povolena, osobní informace v záhlavích specifických pro aplikaci, například v řetězci dotazu; a informace o těle, jako je číslo kreditní karty, mohou být viditelné v protokolech. Nasazovač aplikací je zodpovědný za vynucení řízení přístupu na konfigurační a trasovací soubory. Pokud nechcete, aby byl tento druh informací viditelný, měli byste zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokoly trasování.  
  
 Následující tipy vám mohou pomoci zabránit neúmyslnému vystavení obsahu trasovacího souboru:  
  
- Ujistěte se, že soubory protokolu jsou chráněny seznamy řízení přístupu (ACL) ve scénářích WebHost i self-host.  
  
- Zvolte příponu souboru, kterou nelze snadno obsluhovat pomocí webového požadavku. Například přípona souboru XML není bezpečnou volbou. V průvodci správou iis najdete seznam rozšíření, která lze obsluhovat.  
  
- Zadejte absolutní cestu pro umístění souboru protokolu, která by měla být mimo veřejný adresář WebHost vroot, aby se zabránilo jeho přístupu externí stranou pomocí webového prohlížeče.  
  
 Ve výchozím nastavení nejsou klíče a osobní údaje (PII), jako je uživatelské jméno a heslo, zaznamenány v trasování a protokolovaných zprávách. Správce počítače však může `enableLoggingKnownPII` atribut v `machineSettings` elementu souboru Machine.config použít k povolení aplikací spuštěných v počítači k protokolování známých osobně identifikovatelných informací (PII) následujícím způsobem:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 Nasazovač aplikací pak `logKnownPii` může použít atribut v souboru App.config nebo Web.config k povolení protokolování pii následujícím způsobem:  
  
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
  
 Pouze v případě, že obě nastavení jsou `true` pii protokolování povoleno. Kombinace dvou přepínačů umožňuje flexibilitu protokolovat známé pii pro každou aplikaci.  
  
 Měli byste si být vědomi toho, že pokud zadáte dva nebo více vlastních zdrojů v konfiguračním souboru, budou přečteny pouze atributy prvního zdroje. Ostatní jsou ignorovány. To znamená, že pro následující soubor App.config, PII není zaznamenána pro oba zdroje, i když protokolování PII je explicitně povolena pro druhý zdroj.  
  
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
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` prvek existuje mimo soubor Machine.config, systém <xref:System.Configuration.ConfigurationErrorsException>vyvolá .  
  
 Změny jsou účinné pouze při spuštění nebo restartování aplikace. Událost je zaznamenána při spuštění, pokud `true`jsou oba atributy nastaveny na . Událost je také zaznamenána, `logKnownPii` pokud je nastavena na, `true` ale `enableLoggingKnownPii` je `false`.  
  
 Další informace o protokolování pii naleznete v tématu [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.  
  
 Správce počítače a nasazovač aplikací by měli být při použití těchto dvou přepínačů velmi opatrní. Pokud je povoleno protokolování PII, jsou zaznamenány bezpečnostní klíče a pii. Pokud je zakázána, citlivá data a data specifická pro aplikaci jsou stále protokolována v záhlavích a tělech zpráv. Podrobnější diskusi o ochraně osobních údajů a ochraně osobních údajů před odhalením naleznete [v tématu Ochrana osobních údajů uživatelů](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
 Kromě toho ip adresa odesílatele zprávy je zaznamenána jednou za připojení pro přenosy orientované na připojení a jednou za zprávu odeslanou jinak. To se provádí bez souhlasu odesílatele. K tomuto protokolování však dochází pouze na úrovních informace nebo podrobné trasování, které nejsou výchozí nebo doporučené úrovně trasování v produkčním prostředí, s výjimkou živéladění.  
  
## <a name="see-also"></a>Viz také

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
