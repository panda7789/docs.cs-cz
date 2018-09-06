---
title: Konfigurace trasování
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: c5064d90c8601ee44be593446b0fd5ad483e57f2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785437"
---
# <a name="configuring-tracing"></a>Konfigurace trasování
Toto téma popisuje, jak můžete povolit trasování, konfigurovat zdroje trasování generoval trasování a úrovně trasování sady, trasování sady aktivit a šíření pro podporu korelace trasování začátku do konce a nastavit naslouchacích procesů trasování pro přístup k trasování.  
  
 Doporučení pro nastavení trasování v produkčním prostředí nebo prostředí ladění, najdete v tématu [doporučené nastavení pro trasování a protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  V systému Windows 8 je nutné spustit vaše aplikace se zvýšenými oprávněními (Spustit jako správce) v pořadí pro vaši aplikaci k vygenerování protokoly trasování.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 Windows Communication Foundation (WCF) následující výstupní data odesílá do pro diagnostické trasování:  
  
-   Trasování pro proces milníky pro všechny součásti aplikace, jako je volání operace kód výjimky, upozornění a dalších operací zpracování událostí.  
  
-   Události chyb Windows při trasování funkce nepracuje správně. Zobrazit [protokolování událostí](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Trasování WCF je postavený na <xref:System.Diagnostics>. Chcete-li použít trasování, byste měli definovat zdroje trasování v konfiguračním souboru nebo v kódu. Zdroj trasování WCF definuje pro každé sestavení WCF. `System.ServiceModel` Zdroj trasování je nejobecnější zdroj trasování WCF a zaznamenává milníky zpracování napříč celým zásobníkem komunikace WCF, z zadáním/opuštění přenosu k zadávání/opuštění uživatelského kódu. `System.ServiceModel.MessageLogging` Zdroj trasování zaznamenává všechny zprávy, které budou plout prostřednictvím systému.  
  
 Ve výchozím nastavení není povoleno trasování. Aktivujte trasování, musíte vytvořit naslouchací proces trasování a nastaví úroveň trasování než "Off" pro zdroj trasování vybrané v konfiguraci. v opačném případě WCF negeneruje žádné trasování. Pokud nezadáte naslouchací proces, bude trasování automaticky zakázáno. Pokud je definován naslouchací proces, ale není zadána žádná úroveň, na úrovni nastavená na "Off" ve výchozím nastavení, což znamená, že je vygenerován bez trasování.  
  
 Pokud používáte bodů rozšiřitelnosti WCF, jako je vlastní operace invokers, by měly vydávat vlastní trasy. Je to proto, že pokud se rozhodnete implementovat bod rozšiřitelnosti, WCF můžete už negeneruje standardní trasování ve výchozí cestě. Pokud není implementujete podporu ruční trasování generování trasování, nemusíte vidět trasování, které očekáváte.  
  
 Trasování můžete nakonfigurovat úpravou souboru konfigurace aplikace – buď soubor Web.config pro hostované webové aplikace nebo Appname.exe.config pro aplikace v místním prostředí. Následuje příklad takové úpravy. Další informace o těchto nastaveních naleznete v části "Konfigurace trasování naslouchacích procesů k využívání trasování".  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Chcete-li upravit konfigurační soubor projektu služby WCF v sadě Visual Studio, klikněte pravým tlačítkem na konfigurační soubor aplikace – buď soubor Web.config pro hostované webové aplikace nebo Appname.exe.config aplikace v místním prostředí v **Průzkumníka řešení** . Klikněte na tlačítko **upravit konfiguraci WCF** položka kontextové nabídky. Tím se spustí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), což vám umožní změnit nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurace zdrojů trasování generovat trasování  
 Zdroj trasování WCF definuje pro každé sestavení. Trasování vygenerované v rámci sestavení přistupují naslouchacích procesů definované pro tento zdroj. Jsou definovány následující zdroje trasování:  
  
-   System.ServiceModel: Protokoly všech fázích zpracování WCF, vždy, když je konfigurace pro čtení, zpráva se zpracuje v přenosu, zpracování, bezpečnostní zprávy odesílá v uživatelském kódu a tak dále.  
  
-   System.ServiceModel.MessageLogging: Protokoluje všechny zprávy, které budou plout prostřednictvím systému.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Protokolování pro rozhraní .NET Framework do Common Log File System (CLFS).  
  
-   System.Runtime.Serialization: Pokud jsou objekty čteným nebo zapsaným protokoly.  
  
-   Služba CardSpace.  
  
 Každý zdroj trasování používat stejné (sdílené) naslouchacího procesu, můžete nakonfigurovat, jak je uvedeno v následujícím příkladu konfigurace.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 Kromě toho můžete přidat zdroje trasování definovaný uživatelem, jak je ukázáno v následujícím příkladu, pro generování trasování v kódu uživatele.  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 Další informace o vytváření zdrojů trasování uživatelem definované, najdete v části [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Chcete-li využívají trasování konfiguraci naslouchacích procesů trasování  
 Za běhu informační kanály WCF data trasování naslouchacím procesům, které zpracovávají data. WCF obsahuje několik předdefinovaných naslouchacích procesů pro <xref:System.Diagnostics>, která se liší ve formátu používají pro výstup. Můžete také přidat vlastní naslouchací proces typy.  
  
 Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V konfiguraci našeho příkladu jsme pojmenovali naslouchací proces `traceListener` a přidat standardní naslouchací proces trasování rozhraní .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ chceme použít. Můžete přidat libovolný počet naslouchacích procesů trasování pro každý zdroj. Pokud naslouchací služby stopy vysílá trasování do souboru, musíte zadat název a umístění souboru výstupu v konfiguračním souboru. To se provádí nastavením `initializeData` k názvu souboru pro tuto naslouchací proces. Pokud nezadáte název souboru, náhodného názvu souboru generován na základě typu naslouchací proces používá. Pokud <xref:System.Diagnostics.XmlWriterTraceListener> je použit, název souboru bez přípony generuje. Pokud se rozhodnete implementovat vlastní naslouchací proces, můžete také použít tento atribut pro příjem dat inicializace než název souboru. Můžete například zadat identifikátor databáze pro tento atribut.  
  
 Můžete nakonfigurovat vlastní naslouchací k odesílání trasování na lince, například ke vzdálené databázi. Jako občasným aplikace měla vynutit, vhodné řízení přístupu na protokoly trasování ve vzdáleném počítači.  
  
 Můžete také nakonfigurovat naslouchací proces trasování prostřednictvím kódu programu. Další informace najdete v tématu [postupy: vytváření a inicializace naslouchacích procesů trasování](https://go.microsoft.com/fwlink/?LinkId=94648) a [vytvořením Custom TraceListener](https://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Protože `System.Diagnostics.XmlWriterTraceListener` není bezpečná pro vlákno, zdroj trasování může zamknutí prostředků, výhradně při výstupu trasování. Po několika vlákny výstup trasování do zdroje trasování konfigurován pro použití tímto naslouchacím procesem, může dojít k sporu prostředků, výsledkem problému s výkonem významné. Chcete-li vyřešit tento problém, měli byste implementovat vlastní naslouchací proces, který je bezpečná pro vlákno.  
  
## <a name="trace-level"></a>Úroveň trasování  
 Úroveň trasování řídí `switchValue` nastavení zdroje trasování. K dispozici trasování úrovně jsou popsány v následující tabulce.  
  
|Úroveň trasování|Povaha sledovaných událostí|Obsah sledovaných událostí|Sledovaných událostí|Cílový uživatel|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|Není k dispozici|Není k dispozici|Žádné trasování jsou emitovány.|Není k dispozici|  
|Kritická|"Záporné" události: událostí, které označují neočekávané zpracování nebo chybový stav.||Protokolují se neošetřené výjimky, včetně následujících:<br /><br /> – OutOfMemoryException<br />-Výjimka ThreadAbortException (CLR volá všechny ThreadAbortExceptionHandler)<br />-StackOverflowException –, (nemůže být zachycena)<br />– ConfigurationErrorsException –<br />– SEHException –<br />-Chyby spuštění aplikací<br />– Režim Failfast události<br />– System. program přestane reagovat<br />-Nezpracovatelné zprávy: zpráva trasování, které způsobí selhání aplikace.|Správci<br /><br /> Vývojáři aplikací|  
|Chyba|"Záporné" události: událostí, které označují neočekávané zpracování nebo chybový stav.|Došlo k neočekávané zpracování. Aplikace nebyla schopna provést úlohu podle očekávání. Aplikace je však stále zprovozněný.|Všechny výjimky jsou protokolovány.|Správci<br /><br /> Vývojáři aplikací|  
|Upozornění|"Záporné" události: událostí, které označují neočekávané zpracování nebo chybový stav.|Možný problém došlo k chybě nebo může dojít, ale stále funkce aplikace správně. Nemusí ale dál správně fungovat.|-Aplikace přijímá více požadavků než umožní její nastavení omezení šířky pásma.<br />-Přijímající fronty se blíží maximální kapacitě nakonfigurované.<br />– Byla překročena časový limit.<br />-Credentials odmítají.|Správci<br /><br /> Vývojáři aplikací|  
|Informace o|"Pozitivní" události: událostí, které označují úspěšné milníky|Důležité a úspěšné milníky spuštění aplikace, bez ohledu na to, zda aplikace funguje správně.|Obecně platí zprávy, které jsou užitečné pro monitorování a diagnostiku stavu systému, měření výkonu nebo profilování jsou generovány. Tyto informace můžete použít pro správu výkon a plánování kapacity:<br /><br /> -Kanály jsou vytvořeny.<br />-Koncového bodu naslouchací procesy jsou vytvořeny.<br />-Zpráva zadá/ponechá přenosu.<br />-Načte token zabezpečení.<br />– Nastavení konfigurace je pro čtení.|Správci<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktu.|  
|verbose|"Pozitivní" události: událostí, které označují úspěšné milníky.|Jsou emitovány nízké událostí na úrovni pro uživatelský kód a údržbu.|Obecně platí můžete použít tuto úroveň optimalizace pro ladění nebo aplikace.<br /><br /> -Záhlaví zprávy bylo porozuměno.|Správci<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktu.|  
|ActivityTracing||Tok událostí mezi zpracování aktivit a komponent.|Tato úroveň umožňuje vývojářům a správcům ke korelaci aplikací ve stejné doméně aplikace:<br /><br /> -Trasování pro hranice aktivity, jako je například spuštění/zastavení.<br />-Trasování pro přenosy.|Všechny|  
|Všechny||Aplikace může fungovat správně. Všechny události se vysílají.|Všechny předchozí události.|Všechny|  
  
 Úrovně z Verbose na hodnotu kritický jsou sebe, to znamená, každou úroveň trasování zahrnuje všechny úrovně nad ním s výjimkou na úrovni Off. Například naslouchací proces naslouchá na úroveň pro upozornění obdrží trasování kritické chyby a upozornění. Všechny úrovně zahrnuje události z Verbose na kritický a aktivity události trasování.  
  
> [!CAUTION]
>  Úrovně informace, podrobný nebo ActivityTracing generovat velké množství trasování, které mohou negativně ovlivnit propustnost zpráv, pokud jste využili všechny dostupné prostředky na počítači.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurace trasování činnosti a šíření pro korelaci  
 `activityTracing` Hodnota zadaná pro omezení `switchValue` atribut se používá k povolení trasování činnosti, které vysílá trasování aktivity hranic a přenosy v rámci koncových bodů.  
  
> [!NOTE]
>  Při použití určitých funkcí rozšíření ve službě WCF, může se zobrazit <xref:System.NullReferenceException> když je povoleno trasování činnosti. Chcete-li tento problém vyřešit, zkontrolujte konfigurační soubor vaší aplikace a ujistěte se, že `switchValue` atribut pro zdroj trasování není nastaven na hodnotu `activityTracing`.  
  
 `propagateActivity` Atribut označuje, zda by mělo být předáno aktivity ostatní koncové body, které jsou součástí zprávy exchange. Nastavením této hodnoty na `true`, můžete provést trasování soubory generované záznamem pro jakékoli dva koncové body služby a sledovat, jak sadu stopy na jeden koncový bod byly převedeny do sady trasování na jiný koncový bod.  
  
 Další informace o trasování činnosti a šíření najdete v tématu [šíření](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Obě `propagateActivity` a `ActivityTracing` logické hodnoty použít na třídy System.ServiceModel TraceSource. `ActivityTracing` Hodnota platí také pro všechny zdroje trasování, včetně WCF nebo uživatelem definované balíčky.  
  
 Nelze použít `propagateActivity` atribut s uživatelem definované trasování zdrojů. Pro šíření ID aktivity uživatele kódu, ujistěte se, že nenastavíte ServiceModel `ActivityTracing`, přitom stále má ServiceModel `propagateActivity` atribut nastaven na `true`.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Postupy: Vytváření a inicializace naslouchacích procesů trasování](https://go.microsoft.com/fwlink/?LinkId=94648)  
 [Vytváření vlastních TraceListener](https://go.microsoft.com/fwlink/?LinkId=96239)
