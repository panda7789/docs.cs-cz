---
title: Konfigurace trasování
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: d8b216bf5497cf2a1faa2fa24ba1d8b3102f6f10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185742"
---
# <a name="configuring-tracing"></a>Konfigurace trasování
Toto téma popisuje, jak můžete povolit trasování, konfigurovat zdroje trasování k vyzařování trasování a nastavit úrovně trasování, nastavit trasování aktivity a šíření pro podporu korelace trasování od začátku do konce a nastavit posluchače trasování pro přístup k trasování.  
  
 Doporučení nastavení trasování v produkčním nebo ladicím prostředí naleznete v [části Doporučená nastavení pro trasování a protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
> V systému Windows 8 je nutné spustit aplikaci se zvýšenými oprávněními (Spustit jako správce), aby aplikace generovat protokoly trasování.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 Windows Communication Foundation (WCF) výstupy následující data pro diagnostické trasování:  
  
- Trasování pro milníky procesu ve všech součástech aplikací, jako jsou například volání operací, výjimky kódu, upozornění a další významné události zpracování.  
  
- Chybové události systému Windows při selhání funkce trasování. Viz [Protokolování událostí](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Trasování WCF je postaveno na horní části <xref:System.Diagnostics>. Chcete-li použít trasování, měli byste definovat zdroje trasování v konfiguračním souboru nebo v kódu. WCF definuje zdroj trasování pro každé sestavení WCF. Zdroj `System.ServiceModel` trasování je nejobecnější wcf trasovací zdroj a záznamy zpracování milníků v rámci zásobníku komunikace WCF, od zadání nebo opuštění přenosu na zadání nebo opuštění uživatelského kódu. Zdroj `System.ServiceModel.MessageLogging` trasování zaznamenává všechny zprávy, které procházejí systémem.  
  
 Trasování není ve výchozím nastavení povoleno. Chcete-li aktivovat trasování, musíte vytvořit naslouchací proces trasování a nastavit jinou úroveň trasování než "Vypnuto" pro vybraný zdroj trasování v konfiguraci; v opačném případě WCF negeneruje žádné trasování. Pokud nezadáte naslouchací proces, trasování je automaticky zakázáno. Pokud je definován naslouchací proces, ale není zadána žádná úroveň, je úroveň ve výchozím nastavení nastavena na hodnotu Vypnuto, což znamená, že není vyzařováno žádné trasování.  
  
 Pokud používáte WCF body rozšiřitelnosti, jako jsou vlastní operace vzponiče, měli byste vyzařovat vlastní trasování. Důvodem je, že pokud implementujete bod rozšiřitelnosti, WCF již nelze vyzařovat standardní trasování ve výchozí cestě. Pokud neimplementujete podporu ručního trasování vyzařováním trasování, nemusí se zobrazit trasování, které očekáváte.  
  
 Trasování můžete nakonfigurovat úpravou konfiguračního souboru aplikace – buď Web.config pro web-hostované aplikace, nebo Appname.exe.config pro samoobslužné aplikace. Následuje příklad takové úpravy. Další informace o těchto nastaveních naleznete v části Konfigurace posluchačů trasování ke spotřebě trasování.  
  
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
> Chcete-li upravit konfigurační soubor projektu služby WCF v sadě Visual Studio, klepněte pravým tlačítkem myši na konfigurační soubor aplikace – buď web.config pro webové hostované aplikace, nebo Appname.exe.config pro samoobslužnou aplikaci v **Průzkumníku řešení**. Pak zvolte položku kontextové nabídky **Upravit konfiguraci WCF.** Tím se spustí [nástroj Editor konfigurace (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), který umožňuje měnit nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurace zdrojů trasování pro vyzařování trasování  
 WCF definuje zdroj trasování pro každé sestavení. Trasování generované v rámci sestavení jsou přístupné posluchači definované pro tento zdroj. Jsou definovány tyto zdroje trasování:  
  
- System.ServiceModel: Protokoluje všechny fáze zpracování WCF, při každém čtení konfigurace, zpracování zprávy v přenosu, zpracování zabezpečení, odeslání zprávy v uživatelském kódu a tak dále.  
  
- System.ServiceModel.MessageLogging: Protokoluje všechny zprávy, které procházejí systémem.  
  
- System.IdentityModel.  
  
- System.servicemodel.activation.  
  
- System.IO.Log: Protokolování rozhraní rozhraní .NET Framework do společného systému souborů souborů (CLFS).  
  
- System.Runtime.Serialization: Protokoly při čtení nebo zápisu objektů.  
  
- Cardspace.  
  
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
  
 Kromě toho můžete přidat uživatelem definované zdroje trasování, jak ukazuje následující příklad, k vyzařování trasování kódu uživatele.  
  
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
  
 Další informace o vytváření uživatelem definovaných zdrojů trasování naleznete [v tématu Rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Konfigurace posluchačů trasování ke spotřebě trasování  
 Za běhu WCF kanály data trasování na schytavky, které zpracovávají data. WCF poskytuje několik předdefinovaných naslouchacích procesy pro <xref:System.Diagnostics>, které se liší ve formátu, který používají pro výstup. Můžete také přidat vlastní typy posluchačů.  
  
 Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V naší příkladkonfigurace jsme `traceListener` pojmenovali Listener a přidali`System.Diagnostics.XmlWriterTraceListener`standardní naslouchací proces trasování rozhraní .NET Framework ( ) jako typ, který chceme použít. Pro každý zdroj můžete přidat libovolný počet posluchačů trasování. Pokud posluchač trasování vyzařuje trasování do souboru, musíte zadat umístění výstupního souboru a název v konfiguračním souboru. To se provádí `initializeData` nastavením názvu souboru pro tento naslouchací proces. Pokud nezadáte název souboru, bude na základě použitého typu posluchače vygenerován náhodný název souboru. Pokud <xref:System.Diagnostics.XmlWriterTraceListener> se používá, je generován název souboru bez přípony. Pokud implementujete vlastní naslouchací proces, můžete také tento atribut použít k příjmu inicializačních dat jiných než název souboru. Můžete například zadat identifikátor databáze pro tento atribut.  
  
 Můžete nakonfigurovat vlastní naslouchací proces trasování pro odesílání trasování v síti, například do vzdálené databáze. Jako nasaditelný nástroj aplikace byste měli vynutit správné řízení přístupu v protokolech trasování ve vzdáleném počítači.  
  
 Můžete také nakonfigurovat naslouchací proces trasování programově. Další informace naleznete v [tématu How to: Create and Initialize Trace Listeners](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [Creating a Custom TraceListener](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).  
  
> [!CAUTION]
> Protože `System.Diagnostics.XmlWriterTraceListener` není bezpečný pro přístup z více vláken, zdroj trasování může uzamknout prostředky výhradně při vyřazování trasování. Při mnoho vláken výstup trasování ke zdroji trasování nakonfigurované pro použití tohoto naslouchací proces, může dojít k tvrzení o prostředku, což má za následek významný problém s výkonem. Chcete-li tento problém vyřešit, měli byste implementovat vlastní naslouchací proces, který je bezpečný pro přístup z více vláken.  
  
## <a name="trace-level"></a>Úroveň trasování  
 Úroveň trasování je řízena `switchValue` nastavením zdroje trasování. Dostupné úrovně trasování jsou popsány v následující tabulce.  
  
|Úroveň trasování|Povaha sledovaných událostí|Obsah sledovaných událostí|Sledované události|Cíl uživatele|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Vypnuto|Není dostupné.|Není dostupné.|Nejsou vyzařovány žádné stopy.|Není dostupné.|  
|Kritická|"Negativní" události: události, které označují neočekávané zpracování nebo chybový stav.||Protokolovány jsou neošetřené výjimky včetně následujících:<br /><br /> - Výjimka mimo paměť<br />- ThreadAbortException (CLR vyvolá všechny ThreadAbortExceptionHandler)<br />- StackOverflowException (nelze zachytit)<br />- ConfigurationErrorsException<br />- SEHException<br />- Chyby spuštění aplikace<br />- Failfast události<br />- Systém visí<br />- Poison zprávy: trasování zpráv, které způsobují selhání aplikace.|Správci<br /><br /> Vývojáři aplikací|  
|Chyba|"Negativní" události: události, které označují neočekávané zpracování nebo chybový stav.|Došlo k neočekávanému zpracování. Aplikace nebyla schopna provést úlohu podle očekávání. Aplikace je však stále v provozu.|Všechny výjimky jsou protokolovány.|Správci<br /><br /> Vývojáři aplikací|  
|Upozornění|"Negativní" události: události, které označují neočekávané zpracování nebo chybový stav.|Došlo k možnému problému nebo může dojít, ale aplikace stále funguje správně. Však nemusí nadále pracovat správně.|- Aplikace přijímá více požadavků, než její nastavení omezení umožňuje.<br />- Přijímací fronta se blíží maximální nakonfigurované kapacitě.<br />- Časový limit byl překročen.<br />- Pověření jsou odmítnuta.|Správci<br /><br /> Vývojáři aplikací|  
|Informace|"Pozitivní" události: události, které označují úspěšné milníky|Důležité a úspěšné milníky spuštění aplikace, bez ohledu na to, zda aplikace pracuje správně nebo ne.|Obecně platí, že jsou generovány zprávy užitečné pro sledování a diagnostiku stavu systému, měření výkonu nebo profilování. Tyto informace můžete použít pro plánování kapacity a řízení výkonu:<br /><br /> - Kanály jsou vytvořeny.<br />- Jsou vytvořeny naslouchací procesy koncového bodu.<br />- Zpráva zadává/opouští dopravu.<br />- Bezpečnostní token je načten.<br />- Nastavení konfigurace je přečteno.|Správci<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktů.|  
|Verbose|"Pozitivní" události: události, které označují úspěšné milníky.|Jsou emitovány události nízké úrovně pro uživatelský kód i obsluhu.|Obecně lze tuto úroveň použít pro ladění nebo optimalizaci aplikací.<br /><br /> - Rozumím záhlaví zprávy.|Správci<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktů.|  
|Aktivitatrasuje||Tok událostí mezi aktivitami zpracování a součástmi.|Tato úroveň umožňuje správcům a vývojářům korelovat aplikace ve stejné doméně aplikace:<br /><br /> - Stopy pro hranice aktivity, jako je například start/stop.<br />- Stopy pro převody.|Všechny|  
|Všechny||Aplikace může fungovat správně. Všechny události jsou emitovány.|Všechny předchozí události.|Všechny|  
  
 Úrovně od Verbose na kritické jsou skládané nad sebou, to znamená, že každá úroveň trasování zahrnuje všechny úrovně nad ní kromě úrovně Off. Například naslouchací proces naslouchání na úrovni upozornění obdrží kritické, chyby a upozornění trasování. Úroveň All zahrnuje události od verbose až po kritické události a události trasování aktivity.  
  
> [!CAUTION]
> Informace, podrobné a ActivityTracing úrovně generovat velké trasování, které mohou negativně ovlivnit propustnost zprávy, pokud jste použili všechny dostupné prostředky v počítači.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurace trasování aktivity a šíření pro korelaci  
 Hodnota `activityTracing` zadaná `switchValue` pro atribut se používá k povolení trasování aktivity, která vydává trasování pro hranice aktivity a přenosy v rámci koncových bodů.  
  
> [!NOTE]
> Při použití určitých funkcí rozšiřitelnosti v WCF, může získat při <xref:System.NullReferenceException> sledování aktivity je povolena. Chcete-li tento problém vyřešit, zkontrolujte konfigurační soubor aplikace a ujistěte se, že `switchValue` atribut pro zdroj trasování není nastavena na `activityTracing`.  
  
 Atribut `propagateActivity` označuje, zda by měla být aktivita rozšířena do jiných koncových bodů, které se účastní výměny zpráv. Nastavením této `true`hodnoty na , můžete trvat trasovací soubory generované libovolnými dvěma koncovými body a sledovat, jak sada trasování na jednom koncovém bodu tokovala do sady trasování na jiném koncovém bodu.  
  
 Další informace o trasování aktivit a šíření naleznete [v tématu Šíření](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Obě `propagateActivity` `ActivityTracing` a logické hodnoty platí pro System.ServiceModel TraceSource. Hodnota `ActivityTracing` platí také pro všechny zdroje trasování, včetně WCF nebo uživatelem definované ty.  
  
 `propagateActivity` Atribut nelze použít s uživatelem definovanými zdroji trasování. Pro šíření ID aktivity kódu uživatele se ujistěte, že nenastavujete ServiceModel `ActivityTracing`, zatímco stále máte atribut ServiceModel `propagateActivity` nastavený na `true`.  
  
## <a name="see-also"></a>Viz také

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Postupy: Vytváření a inicializace naslouchacích procesů trasování](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Vytvoření vlastního posluchače tracelisteneru](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
