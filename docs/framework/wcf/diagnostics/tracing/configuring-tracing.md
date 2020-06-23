---
title: Konfigurace trasování
description: Naučte se, jak povolit trasování, konfigurovat zdroje trasování, nastavit trasování a šíření aktivity a nastavit naslouchací procesy trasování pro přístup k trasováním ve službě WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 55d701ee6769099698d2fd869a1502d94237b5a8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245346"
---
# <a name="configuring-tracing"></a>Konfigurace trasování
Toto téma popisuje, jak lze povolit trasování, nakonfigurovat zdroje trasování pro generování trasování a nastavení úrovní trasování, nastavení trasování a šíření aktivit pro podporu komplexní korelace trasování a nastavení posluchačů trasování pro přístup k trasování.  
  
 Doporučení pro trasování nastavení v produkčním nebo ladicím prostředí najdete v tématu [Doporučené nastavení pro trasování a protokolování zpráv](recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
> V systému Windows 8 musíte spustit zvýšené oprávnění aplikace (Spustit jako správce), aby vaše aplikace generovala protokoly trasování.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 Windows Communication Foundation (WCF) vytvoří výstup pro diagnostické trasování následující data:  
  
- Trasování pro milníky procesů napříč všemi komponentami aplikací, například volání operací, výjimky kódu, upozornění a další významné události zpracování.  
  
- Chybové události systému Windows, pokud funkce trasování nepracuje správně. Viz [protokolování událostí](../event-logging/index.md).  
  
 Trasování WCF je postaveno na začátku <xref:System.Diagnostics> . Chcete-li použít trasování, je třeba definovat zdroje trasování v konfiguračním souboru nebo v kódu. WCF definuje zdroj trasování pro každé sestavení WCF. `System.ServiceModel`Zdroj trasování je nejobecnější zdroj trasování WCF a zaznamenává milníky zpracování v rámci komunikačního zásobníku WCF, od vstupu a výstupu do přenosu za účelem zadání nebo ukončení uživatelského kódu. `System.ServiceModel.MessageLogging`Zdroj trasování zaznamenává všechny zprávy, které procházejí systémem.  
  
 Trasování není ve výchozím nastavení povolené. Chcete-li aktivovat trasování, je nutné pro vybraný zdroj trasování v konfiguraci vytvořit naslouchací proces trasování a nastavit úroveň trasování jinou než "vypnuto". v opačném případě WCF negeneruje žádná trasování. Pokud neurčíte naslouchací proces, trasování se automaticky zakáže. Pokud je definován naslouchací proces, ale není zadána žádná úroveň, úroveň je ve výchozím nastavení nastavena na "off", což znamená, že není vygenerováno žádné trasování.  
  
 Pokud používáte body rozšiřitelnosti WCF, jako je například vlastní operace invokers, měli byste vygenerovat vlastní trasování. Důvodem je, že pokud implementujete bod rozšiřitelnosti, WCF již nemůže generovat standardní trasování ve výchozí cestě. Pokud neimplementujete podporu ručního trasování tím, že vygenerujete trasování, možná neuvidíte trasování, které očekáváte.  
  
 Trasování můžete nakonfigurovat úpravou konfiguračního souboru aplikace – buď Web.config pro aplikace hostované na webu, nebo Appname.exe.config pro samoobslužné aplikace. Následuje příklad takového úprav. Další informace o těchto nastaveních najdete v části Konfigurace naslouchacího procesu trasování pro využívání trasování.  
  
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
> Chcete-li upravit konfigurační soubor projektu služby WCF v aplikaci Visual Studio, klikněte pravým tlačítkem myši na konfigurační soubor aplikace, buď Web.config pro aplikace hostované na webu, nebo Appname.exe.config pro samoobslužnou aplikaci v **Průzkumník řešení**. Pak zvolte položku **Upravit konfiguraci služby WCF** v kontextové nabídce. Tím se spustí [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md), který umožňuje změnit nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurace zdrojů trasování pro vygenerování trasování  
 WCF definuje zdroj trasování pro každé sestavení. Trasování generovaná v rámci sestavení jsou k dispozici pro naslouchací procesy definované pro tento zdroj. Jsou definovány následující zdroje trasování:  
  
- System. ServiceModel: protokoluje všechny fáze zpracování služby WCF, kdykoli se načte konfigurace, zpráva se zpracuje při přenosu, zpracování zabezpečení, zpráva se odešle v uživatelském kódu a tak dále.  
  
- System. ServiceModel. MessageLogging: protokoluje všechny zprávy, které procházejí systémem.  
  
- System. IdentityModel.  
  
- System. ServiceModel. Activation.  
  
- System. IO. log: protokolování .NET Framework rozhraní do Common Log File System (CLFS).  
  
- System. Runtime. Serialization: protokoluje se při čtení nebo zápisu objektů.  
  
- Službu.  
  
 Každý zdroj trasování můžete nakonfigurovat tak, aby používal stejný (sdílený) naslouchací proces, jak je uvedeno v následujícím příkladu konfigurace.  
  
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
  
 Kromě toho můžete přidat uživatelem definované zdroje trasování, jak je znázorněno v následujícím příkladu, k vygenerování trasování uživatelského kódu.  
  
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
  
 Další informace o vytváření uživatelem definovaných zdrojů trasování naleznete v tématu [rozšíření trasování](../../samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Konfigurace naslouchacího procesu trasování pro využívání trasování  
 V době běhu kanály WCF sleduje data do posluchačů, které zpracovávají data. WCF poskytuje několik předdefinovaných posluchačů pro <xref:System.Diagnostics> , které se liší ve formátu používaném pro výstup. Můžete také přidat vlastní typy naslouchacího procesu.  
  
 Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V našem příkladu konfigurace jsme pojmenovali naslouchací proces `traceListener` a přidali jsme standardní .NET Framework trasování trasování ( `System.Diagnostics.XmlWriterTraceListener` ), jako typ, který chceme použít. Můžete přidat libovolný počet posluchačů trasování pro každý zdroj. Pokud naslouchací proces trasování vysílá trasování do souboru, je nutné zadat umístění a název výstupního souboru do konfiguračního souboru. To se provádí nastavením `initializeData` na název souboru pro tento naslouchací proces. Pokud název souboru nezadáte, vygeneruje se náhodný název souboru na základě používaného typu naslouchacího procesu. Pokud <xref:System.Diagnostics.XmlWriterTraceListener> se použije, název souboru bez přípony se vygeneruje. Pokud implementujete vlastní naslouchací proces, můžete také použít tento atribut pro příjem jiných inicializačních dat než filename. Můžete například zadat identifikátor databáze pro tento atribut.  
  
 Můžete nakonfigurovat vlastní naslouchací proces trasování pro odesílání trasování na lince, například do vzdálené databáze. Jako modul pro nasazení aplikace byste měli vynutilit správné řízení přístupu na protokolech trasování ve vzdáleném počítači.  
  
 Můžete také programově nakonfigurovat naslouchací proces trasování. Další informace naleznete v tématu [How to: Create and Initialize Listener Traces](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and a Create a [Custom TraceListener](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).  
  
> [!CAUTION]
> Vzhledem `System.Diagnostics.XmlWriterTraceListener` k tomu, že není bezpečná pro přístup z více vláken, může zdroj trasování uzamknout prostředky výhradně při výstupu trasování. Když mnoho vláken výstupuje trasování do zdroje trasování nakonfigurovaného pro použití tohoto naslouchacího procesu, může dojít k kolizí prostředků, což vede k významnému problému s výkonem. Chcete-li vyřešit tento problém, měli byste implementovat vlastní naslouchací proces, který je bezpečný pro přístup z více vláken.  
  
## <a name="trace-level"></a>Úroveň trasování  
 Úroveň trasování je řízena `switchValue` nastavením zdroje trasování. Dostupné úrovně trasování jsou popsány v následující tabulce.  
  
|Úroveň trasování|Povaha sledovaných událostí|Obsah sledovaných událostí|Sledované události|Cíl uživatele|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Vypnout|–|–|Žádná trasování nejsou vygenerována.|–|  
|Kritické|"Záporné" události: události, které indikují neočekávané zpracování nebo chybový stav.||Neošetřené výjimky, včetně následujících, jsou protokolovány:<br /><br /> – OutOfMemoryException<br />-ThreadAbortException (CLR vyvolá všechny ThreadAbortExceptionHandler)<br />-StackOverflowException (nelze zachytit)<br />– ConfigurationErrorsException<br />– SEHException –<br />– Chyby spuštění aplikace<br />– FailFast – události<br />– Systém přestane reagovat.<br />-Poškozené zprávy: trasování zpráv, které způsobí selhání aplikace.|Administrators<br /><br /> Vývojáři aplikací|  
|Chyba|"Záporné" události: události, které indikují neočekávané zpracování nebo chybový stav.|Došlo k neočekávanému zpracování. Aplikace nebyla schopna provést úlohu podle očekávání. Aplikace je však stále v provozu.|Všechny výjimky jsou protokolovány.|Administrators<br /><br /> Vývojáři aplikací|  
|Upozornění|"Záporné" události: události, které indikují neočekávané zpracování nebo chybový stav.|Je možné, že došlo k potížím nebo se může vyskytnout, ale aplikace pořád funguje správně. Nemusí však nadále fungovat správně.|-Aplikace přijímá více požadavků, než umožňuje nastavení omezení.<br />– Fronta pro příjem se blíží své maximální nakonfigurované kapacitě.<br />– Byl překročen časový limit.<br />-Pověření byla zamítnuta.|Administrators<br /><br /> Vývojáři aplikací|  
|Informace|"Kladné" události: události, které označují úspěšné milníky|Důležité a úspěšné milníky provádění aplikace bez ohledu na to, jestli aplikace funguje správně nebo ne.|Obecně platí, že zprávy, které jsou užitečné pro monitorování a diagnostiku stavu systému, jsou vygenerovány při měření výkonu nebo profilace. Tyto informace můžete použít k plánování kapacity a správě výkonu:<br /><br /> – Kanály se vytvoří.<br />– Vytvoří se naslouchací proces koncového bodu.<br />-Zpráva se zadává nebo opouští přenosů.<br />-Byl načten token zabezpečení.<br />-Konfigurační nastavení je přečteno.|Administrators<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktů.|  
|Verbose|"Kladné" události: události, které označují úspěšné milníky.|Generují se události nízké úrovně pro uživatelský kód i obsluhu.|Obecně můžete použít tuto úroveň pro ladění nebo optimalizaci aplikace.<br /><br /> -Srozumitelná Hlavička zprávy|Administrators<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktů.|  
|ActivityTracing||Flow události mezi aktivitami zpracování a komponentami.|Tato úroveň umožňuje správcům a vývojářům korelovat aplikace ve stejné doméně aplikace:<br /><br /> – Trasování pro hranice aktivity, například spustit/zastavit.<br />– Trasování pro přenosy.|Vše|  
|Vše||Aplikace může fungovat správně. Budou vygenerovány všechny události.|Všechny předchozí události.|Vše|  
  
 Úrovně z podrobných na kritickou jsou navrstveny nad sebou, to znamená, že každá úroveň trasování zahrnuje všechny úrovně nad ní, kromě úrovně off. Například naslouchací proces, který naslouchá na úrovni upozornění, obdrží kritické trasování, chyby a upozornění. Úroveň All zahrnuje události z podrobných na události trasování kritické a aktivity.  
  
> [!CAUTION]
> Úrovně Information, verbose a ActivityTracing generují velké množství trasování, které může negativně ovlivnit propustnost zprávy, pokud jste použili všechny dostupné prostředky v počítači.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurace trasování aktivit a šíření pro korelaci  
 `activityTracing`Hodnota zadaná pro atribut slouží `switchValue` k povolení trasování aktivity, které vysílá trasování pro hranice aktivity a přenos v rámci koncových bodů.  
  
> [!NOTE]
> Při použití určitých funkcí rozšíření v technologii WCF se může zobrazit, <xref:System.NullReferenceException> když je povoleno trasování aktivit. Chcete-li tento problém vyřešit, zkontrolujte konfigurační soubor aplikace a ujistěte se, že `switchValue` atribut pro zdroj trasování není nastaven na hodnotu `activityTracing` .  
  
 `propagateActivity`Atribut určuje, zda má být aktivita šířena do jiných koncových bodů, které se účastní výměny zpráv. Nastavením této hodnoty na `true` můžete převzít trasovací soubory vygenerované libovolnými dvěma koncovými body a sledovat, jak se sada trasování na jednom koncovém bodu přesměruje do sady trasování na jiném koncovém bodu.  
  
 Další informace o trasování a šíření aktivit naleznete v tématu [šíření](propagation.md).  
  
 Obě `propagateActivity` i `ActivityTracing` logické hodnoty se vztahují na typ System. ServiceModel TraceSource. `ActivityTracing`Hodnota platí také pro všechny zdroje trasování, včetně WCF nebo uživatelem definovaných.  
  
 Nelze použít `propagateActivity` atribut s uživatelem definovanými zdroji trasování. Pro šíření ID aktivity uživatelského kódu se ujistěte, že jste nestavili ServiceModel `ActivityTracing` , ale přesto je `propagateActivity` atribut ServiceModel nastavený na `true` .  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Správa a diagnostika](../index.md)
- [Postupy: Vytváření a inicializace naslouchacích procesů trasování](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Vytvoření vlastního TraceListener](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
