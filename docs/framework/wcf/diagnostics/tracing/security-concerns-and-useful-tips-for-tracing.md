---
title: "Otázky zabezpečení a užitečné tipy pro trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 07ac814253a563a0cbdad1014970af3d18c6fdde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Otázky zabezpečení a užitečné tipy pro trasování
Toto téma popisuje, jak můžete chránit citlivé informace před vystavením i užitečné tipy, při použití webového hostitele.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Vlastní naslouchací pomocí webového hostitele  
 Pokud píšete vlastní naslouchací proces trasování, byste měli vědět o možnosti, že trasování může dojít ke ztrátě v případě hostované webové služby. Recyklování tomuto webovému hostiteli vypne proces za provozu při převezme duplicitní. Však dva procesy však musí mít přístup do stejného zdroje nějakou dobu, což závisí na typu naslouchací proces. V takovém případě, `XmlWriterTraceListener` vytvoří nový soubor trasování pro proces druhý; při trasování událostí pro Windows spravuje více procesy v rámci stejné relace a poskytuje přístup ke stejnému souboru. Pokud vlastní naslouchací proces neposkytuje podobné funkce, trasování může být ztracena, pokud je soubor uzamčen dva procesy.  
  
 Byste měli taky vědět, že vlastní naslouchací může poslat trasování a zprávy v drátové síti, například ke vzdálené databázi. Jako modul pro nasazení aplikace měli byste nakonfigurovat vlastní naslouchací procesy s ovládacím prvkem odpovídající přístup. Také byste měli použít řízení zabezpečení na všechny osobní informace, které mohou být zpřístupněny ve vzdáleném umístění.  
  
## <a name="logging-sensitive-information"></a>Protokolování citlivé informace.  
 Trasování obsahovat hlavičky zpráv, pokud zpráva je v oboru. Pokud je trasování povoleno, osobní údaje v hlavičkách specifické pro aplikace, jako je řetězec dotazu; a body informace, například číslo platební karty, se může stát viditelné v protokolech. Nástroje pro nasazení aplikace je zodpovědná za prosadit řízení přístupu na soubory konfigurace a trasování. Pokud nechcete, aby tento druh informací viditelný, si zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokolů trasování.  
  
 Následující tipy vám může pomoct zabránit neúmyslnému zveřejnění obsahu souboru trasování:  
  
-   Zajistěte, aby v protokolu, které soubory jsou chráněné pomocí řízení přístupu jsou uvedené (ACL) v webového hostitele i scénáře hostování na vlastním serveru.  
  
-   Zvolte příponu souboru, který nelze zpracovat snadno pomocí nějaké webové žádosti. Například přípona souboru .xml není bezpečná volba. Můžete zkontrolovat v Průvodci správy služby IIS najdete v části Seznam přípon, které se dají obsluhovat.  
  
-   Zadejte absolutní cestu k umístění souboru protokolu, které by měla být mimo adresář veřejné vroot webového hostitele, který chcete zabránit přistupuje externí strany pomocí webového prohlížeče.  
  
 Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII), jako je například uživatelské jméno a heslo nejsou protokolovány v trasování a protokolovat zprávy. Správce počítače, ale můžete použít `enableLoggingKnownPII` atribut `machineSettings` element souboru Machine.config tak, aby povolovala aplikace spuštěna v počítači do protokolu známé identifikovatelné osobní údaje (PII) následujícím způsobem:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` element existuje mimo souboru Machine.config, vyvolá systému <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Změny jsou platné jenom v případě, že spuštění nebo restartování aplikace. Při spuštění se zaprotokoluje událost, když oba atributy jsou nastaveny na `true`. Pokud se taky zaznamená událost `logKnownPii` je nastaven na `true` ale `enableLoggingKnownPii` je `false`.  
  
 Další informace o protokolování PII najdete v tématu [bezpečnostní uzamčení PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) ukázka.  
  
 Správce počítače a nástroje pro nasazení aplikace by měla vykonávat extrémně opatrní při používání těchto dva přepínače. Pokud je povoleno protokolování PII, jsou protokolovány zabezpečení klíčů a PII. Pokud je zakázaná, specifické pro aplikaci a citlivá data protokolovány v záhlaví zprávy a obsah. Podrobnější informace o ochraně osobních údajů a ochrana PII vystavení, naleznete v [ochraně osobních údajů uživatelů](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Kromě toho je IP adresa odesílatele zprávy protokolována jednou za připojení pro přenosy orientovaná na připojení a jednou za zprávou odeslanou v opačném případě. To se provádí bez souhlasu odesílatele. Však protokolování dochází pouze na nebo podrobné informace o úrovních trasování, které nejsou výchozí nebo doporučená úrovní trasování v produkčním prostředí, s výjimkou live ladění.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
