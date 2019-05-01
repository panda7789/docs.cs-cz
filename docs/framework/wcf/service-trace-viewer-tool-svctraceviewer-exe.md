---
title: Prohlížeč trasování služeb (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: dd00b72396fe40a7577fabd5704a240f91d1e268
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051755"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Prohlížeč trasování služeb (SvcTraceViewer.exe)
Nástroj Prohlížeč trasování služeb Windows Communication Foundation (WCF) pomáhá analyzovat diagnostické trasování, které se vygenerovaly WCF. Prohlížeče trasování služeb poskytuje způsob, jak snadno sloučení, zobrazení a filtrování trasovací zprávy v protokolu, takže můžete diagnostikovat, opravit a ověřit problémy se službou WCF.  
  
## <a name="configuring-tracing"></a>Konfigurace trasování  
 Diagnostická trasování poskytují informace o tom, co se děje v průběhu operace vaší aplikace. Jak již název napovídá, můžete sledovat operace z jejich zdroje do cíle a také zprostředkující body.  
  
 Můžete nakonfigurovat trasování pomocí konfiguračního souboru aplikace – buď soubor Web.config pro hostované webové aplikace nebo *Appname*.config pro aplikace v místním prostředí. Následuje příklad:  
  
```xml  
<system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="sdt"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "SdrConfigExample.e2e" />  
            </listeners>  
         </source>  
    </sources>  
</system.diagnostics>  
```  
  
 V tomto příkladu je zadaný název a typ naslouchací služby stopy. Naslouchací proces se nazývá `sdt` a standardní naslouchací služby stopy rozhraní .NET Framework (System.Diagnostics.XmlWriterTraceListener) se přidá jako typ. `initializeData` Atribut se používá k nastavení názvu souboru protokolu pro tuto naslouchací proces bude `SdrConfigExample.e2e`. Pro soubor protokolu můžete nahradit úplná cesta k souboru jednoduchý název.  
  
 Tento příklad vytvoří soubor v kořenovém adresáři volá SdrConfigExample.e2e. Při použití prohlížeče trasování pro otevření souboru, jak je popsáno v části "Levou a zobrazení WCF trasovací soubory", zobrazí se všechny zprávy, které byly odeslány.  
  
 Úroveň trasování řídí `switchValue` nastavení. K dispozici trasování úrovně jsou popsány v následující tabulce.  
  
|Úroveň trasování|Popis|  
|-----------------|-----------------|  
|Kritická|-Protokoly položky typu Fail-Fast a protokol událostí a informace pro korelaci trasování. Následující jsou některé příklady, kdy můžete použít kritická úroveň:<br />-AppDomain bylo ukončeno z důvodu neošetřené výjimky.<br />– Aplikace se nespustí.<br />– Zpráva, která způsobila selhání procesu MyApp.exe pochází.|  
|Chyba|– Protokoluje všechny výjimky. Můžete použít úroveň chyb v těchto situacích:<br />-Kódu došlo k chybě z důvodu výjimky neplatné přetypování.<br />– S výjimkou "nepovedlo se vytvořit koncový bod" je příčinou selhání při spuštění aplikace.|  
|Upozornění|-Existuje podmínku, která může následně vést chybě nebo kritické chyby. Můžete použít tuto úroveň v následujících situacích:<br />-Aplikace přijímá více požadavků než povoluje jeho nastavení omezení šířky pásma.<br />-Přijímající fronta je v 98 procent společností z žebříčku jeho konfigurovanou kapacitu.|  
|Informace o|-Zprávy užitečné pro monitorování a diagnostiku stavu systému, měření výkonu nebo profilování jsou generovány. Můžete využít tyto informace pro správu výkon a plánování kapacity. Můžete použít tuto úroveň v následujících situacích:<br />-Selháním po zprávy bylo dosaženo domény aplikace a byla deserializovat.<br />-K selhání došlo k chybě při vytváření vazby HTTP.|  
|Podrobnosti|Ladění úroveň trasování pro obě uživatelský kód a údržba. Nastavíte úroveň při:<br />-Si nejste jisti, jakou metodu v kódu byla volána, když došlo k chybě.<br />-Máte nesprávné koncový bod nakonfigurovaný a službě se nepovedlo spustit, protože položka v úložišti rezervace je uzamčen.|  
|ActivityTracing|Tok událostí mezi zpracování aktivit a komponent.<br /><br /> Tato úroveň umožňuje vývojářům a správcům ke korelaci aplikací ve stejné doméně aplikace.<br /><br /> – Trasování pro aktivitu hranice: start/stop.<br />-Trasování pro přenosy.|  
  
 Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V konfiguraci příklad je naslouchací proces s názvem `sdt` a standardní naslouchací proces trasování rozhraní .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) se přidá jako typ. Použití `initializeData` nastavit název souboru protokolu pro tuto naslouchací proces. Kromě toho můžete nahradit úplná cesta k souboru jednoduchý název.  

Počínaje verzí .NET Framework 4.8, se zobrazí ovládací prvky pole se seznamem v některých vysokokontrastních motivech správnou barvou. Tato změna můžete zakázat tak, že odeberete toto nastavení z *svcTraceViewer.exe.config* souboru:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

## <a name="using-the-service-trace-viewer-tool"></a>Pomocí nástroje prohlížeče trasování služeb  
  
### <a name="opening-and-viewing-wcf-trace-files"></a>Otevřít a zobrazit soubory trasování WCF  
 Prohlížeče trasování služeb podporuje tři typy souborů:  
  
-   Soubor (.svcLog) trasování WCF  
  
-   Události trasování souboru (.etl)  
  
-   Soubor Crimson trasování  
  
 Prohlížeče trasování služeb můžete otevřít libovolný podporovaný trasovací soubor, přidat a integrovat další trasovací soubory, nebo otevřete a současně sloučit skupiny souborů trasování.  
  
##### <a name="to-open-a-trace-file"></a>Pro otevření souboru trasování  
  
1. Spuštění prohlížeče trasování služeb pomocí okno příkazového řádku a přejděte do umístění instalace WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) a pak zadejte `SvcTraceViewer.exe`.  
  
> [!NOTE]
>  Nástroj prohlížeče trasování služeb můžete přidružit dva typy souborů: .svclog a .stvproj. Dva parametry příkazového řádku můžete vytvářet a rušit registraci přípony souborů.  
>   
>  / register: zaregistrovat SvcTraceViewer.exe přidružení přípony souboru ".svclog" a ".stvproj"  
>   
>  / unregister: zrušit registraci přidružení přípony souboru ".svclog" a ".stvproj" SvcTraceViewer.exe  
  
1. Při spuštění prohlížeče trasování služeb, klikněte na tlačítko **souboru** a přejděte na **otevřít**. Přejděte do umístění, kde jsou uloženy soubory trasování.  
  
2. Poklepejte na soubor trasování, který chcete otevřít.  
  
    > [!NOTE]
    >  Stiskněte klávesu SHIFT a klepnutím na více souborů trasování vyberte a otevřete je současně. Prohlížeče trasování služeb sloučí obsah všech souborů a představuje jedno zobrazení. Můžete například otevřít trasovací soubory klienta a služby. To je užitečné, když jste povolili protokolování a aktivita šíření zpráv v konfiguraci. Tímto způsobem můžete prozkoumat výměnu zpráv mezi klientem a službou. Můžete také přetáhnout více souborů do prohlížeče, nebo použít **projektu** kartu. Další podrobnosti v části Správa projektu.  
  
3. Chcete-li přidat další trasovací soubory do kolekce, která je otevřená, klikněte na tlačítko **souboru** a přejděte na **přidat**. V okně, které se otevře přejděte do umístění souborů trasování a poklikejte na soubor, který chcete přidat.  
  
> [!CAUTION]
>  Nedoporučuje se, že můžete načíst soubor protokolu trasování, která je větší než 200 MB. Při pokusu načíst soubor větší než tento limit, proces načítání může trvat dlouhou dobu, v závislosti na vašich prostředků počítače. Nástroj prohlížeče trasování služeb pravděpodobně responzivní dlouhou dobu, nebo ji může vyčerpat paměti v počítači. Doporučujeme, abyste nakonfigurovali částečné načtení se tomu chcete vyhnout. Další informace o tom, jak to udělat, najdete v části "Trasování načítání velkých souborů".  
  
#### <a name="event-tracing-and-crimson-tracing"></a>Trasování událostí a trasování Crimson  
 Nativní formát v prohlížeči je formát trasování aktivity, který vysílá WCF. Trasování, protože ho v jiném formátu musí být převeden, než je zobrazí v prohlížeči. V současné době kromě formátu trasování aktivity, prohlížeč podporuje trasování událostí a crimson trasování.  
  
 Při otevření souboru, který neobsahuje trasování aktivit v prohlížeči se pokusí převést soubor. Musíte zadat název a umístění, která bude obsahovat data převedený trasovacího souboru. Po převedení dat v prohlížeči zobrazí obsah nový soubor.  
  
> [!NOTE]
>  Převod vyžaduje místo na disku k uložení dat převedený trasovacího. Ujistěte se, že máte dostatek místa na disku k uložení dat, před zahájením převodu. V opačném případě se převod nezdaří.  
  
### <a name="managing-projects"></a>Správa projektů  
 Prohlížeč podporuje projekty usnadňuje zobrazení více souborů trasování. Například pokud máte soubor trasování klienta a trasovací soubor služby, můžete je přidat do projektu. Potom pokaždé, když otevřete projekt, všechny trasovací soubory v projektu jsou načteny současně.  
  
 Existují dva způsoby, jak spravovat projekty:  
  
-   V **souboru** nabídku, můžete otevřít, uložte a zavřete projekty.  
  
-   V **projektu** kartu, můžete přidat soubory do projektu.  
  
### <a name="viewing-wcf-traces"></a>Zobrazení trasování WCF  
 WCF vysílá trasování pomocí formátu trasování aktivity. V modelu trasování aktivity jednotlivých trasování jsou seskupené ve aktivity podle jejich účelu. Tok řízení logické přenášena mezi aktivitami. Během životního cyklu aplikace, například mnoho "aktivity odeslat zprávu" se zobrazí a zmizí. Další informace o příliš zobrazení trasování a aktivity a uživatelské rozhraní prohlížeče trasování služeb najdete v tématu [pomocí prohlížeče trasování služeb k zobrazení korelovaných trasování a řešení potíží](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
#### <a name="switching-to-different-views"></a>Přepnutí na různá zobrazení  
 Prohlížeče trasování služeb poskytuje následující různá zobrazení. Se zobrazí jako karty v levém podokně prohlížeče a můžete také přistupovat z **zobrazení** nabídky.  
  
-   Zobrazení aktivity  
  
-   Zobrazení projektu  
  
-   Zobrazení zpráv  
  
-   Zobrazení grafu  
  
##### <a name="activity-view"></a>Zobrazení aktivity  
 Po otevření souborů trasování, uvidíte trasování seskupeny do aktivity a zobrazí v **aktivity** zobrazení v levém podokně.  
  
 **Aktivity** zobrazení, zobrazí název aktivity, počet trasování v aktivitě, doba trvání spuštění a koncový čas.  
  
 Když kliknete na některý z uvedených aktivit, trasování v rámci této aktivity zobrazují v trasování podokno na pravé straně. Pak můžete vybrat trasování zobrazíte její podrobnosti.  
  
 Více aktivit můžete vybrat stisknutím klávesy **Ctrl** nebo **Shift** klíč a kliknutím na požadovaný aktivity. V podokně trasování se zobrazí všechny stopy po vybrané aktivity.  
  
 Dvojitým kliknutím na aktivitu pro její zobrazení v **grafu** zobrazení. Alternativní způsob je vybrat aktivitu a přepnete do **grafu** zobrazení.  
  
> [!NOTE]
>  Aktivita "000000000000" je speciální aktivitě, se nezobrazí v zobrazení grafu. Protože k němu jsou propojené všechny ostatní aktivity, zobrazuje tato aktivita má vliv výkonu.  
  
 Můžete kliknout na záhlaví sloupce seřadíte seznam aktivit. Aktivity, které obsahují trasování upozornění mají žlutým pozadím a ty, které obsahují trasování chyb mít červenou jeden.  
  
 Existují různé typy aktivit a každý typ odpovídá ikonu na levé straně každé aktivity. Najdete v části Vysvětlení trasování ikony pro jejich význam.  
  
##### <a name="project-view"></a>Zobrazení projektu  
 Toto zobrazení umožňuje spravovat trasovací soubory v aktuálním projektu. Další podrobnosti v části Správa projektu.  
  
##### <a name="graph-view"></a>Zobrazení grafu  
 Jednou z nejúčinnějších funkcí prohlížeče trasování služeb je **grafu** zobrazení, která zobrazuje data trasování pro danou aktivitu v podobě grafu. Formulář graf umožňuje zobrazit podle jednotlivých kroků zpracování událostí a vztahy mezi více aktivit při přesunu dat mezi nimi.  
  
 Přepnout na **grafu** zobrazit, vyberte aktivitu v **aktivity** zobrazení a klikněte na tlačítko **aktivity** kartě nebo v protokolu trasování zprávy **zpráva**Zobrazení. Pokud jsou načteny více souborů trasování a aktivity zahrnuje trasování z více než jeden soubor, všechny relevantní trasování se zobrazí v zobrazení grafu. Dvojitým kliknutím na činnosti a zprávy protokolu trasování také povede k **grafu** zobrazení.  
  
 V **grafu** zobrazení, každý svislý sloupec představuje aktivity a každý blok v sloupci představuje trasování. Aktivity jsou seskupené podle procesu (nebo vlákno). Malé šipky mezi aktivitami představují přenosy. Velké objemy šipky mezi procesy představují výměně zpráv. Aktivita ve výběru je vždy žlutou barvou.  
  
###### <a name="selecting-traces-in-the-graph"></a>Výběr trasování v grafu  
  
1. Klikněte na tlačítko blok v grafu.  
  
2. Nahoru a dolů klíče a vyberte jeho sousedním trasování.  
  
3. Podívejte se na informace o trasování v trasování podokně a v podokně podrobností.  
  
###### <a name="expanding-or-collapsing-activity-transfers"></a>Rozbalení a sbalení přenosy aktivit  
 Můžete rozbalit aktivity přenosy při přenosech aktivity ve výběru navýšení kapacity na jinou aktivitu. Umožňuje sledovat přenosy.  
  
 Chcete-li rozbalit nebo sbalit přenosy aktivit  
  
1. Na levé straně na ikonu přenosu najděte přenos trasování symbolem "+".  
  
2. Klikněte "+", nebo stiskněte klávesu **Ctrl** a "+" pomocí klávesnice.  
  
3. Další aktivity se zobrazí v grafu.  
  
4. A "-" se zobrazí na levé straně na ikonu převodu. Klikněte na tlačítko "-" přihlásit nebo stiskněte klávesu Ctrl a "-", sbalí přenos aktivity.  
  
> [!NOTE]
>  Když aktivity obsahuje několik přenosů do ní a rozbalte jednu z přenosy, zobrazí se aktivity, které vedou novou aktivitu z kořenové aktivity. Tyto nové aktivity se zobrazí ve formuláři sbalený. Pokud chcete zobrazit podrobnosti o těchto činností, svisle rozbalit kliknutím na ikonu rozbalení v záhlaví grafu.  
  
###### <a name="expanding-or-collapsing-activities-vertically"></a>Rozbalení a sbalení aktivity svisle  
 V prohlížeči skryje zbytečné podrobně graf aktivity sbalením aktivity. Sbalený aktivity nejsou zobrazeny jednotlivé trasování. Zobrazí se jenom převody trasování. Pokud chcete zobrazit všechna trasování v aktivitě, rozbalte svisle aktivity klepnutím na symbol rozbalení aktivity v hlavičce tohoto grafu.  
  
 Chcete-li rozbalit nebo sbalit aktivity svisle,  
  
1. Klikněte na ikonu "+" v záhlaví činnosti rozbalte aktivity svisle.  
  
2. Všimněte si, že v grafu se zobrazují všechna trasování.  
  
3. Klikněte "-" ikona v záhlaví činnosti sbalte aktivity svisle.  
  
4. Všimněte si, že zprávy pouze důležité přenosy, zaprotokoluje upozornění a trasování výjimky jsou uvedeny v rámci aktivity.  
  
###### <a name="options"></a>Možnosti  
 Můžete vybrat ze dvou možností **možnost** nabídky v zobrazení grafu.  
  
-   Zobrazit hranice trasování aktivity, které v případě nezaškrtnutí ignorovat hranice trasování aktivit v grafu.  
  
-   Zobrazit podrobné trasování Non zpráv, který v případě nezaškrtnutí ignorovat podrobné úrovně trasování, s výjimkou trasování zprávy. Ve většině případů jsou méně důležité pro analýzu úroveň trasování podrobné. Tato možnost je užitečné, pokud nechcete k analýze podrobné úrovně trasování a pouze chcete se soustředit na důležité trasování.  
  
###### <a name="layout-mode"></a>Režim rozložení  
 Prohlížeč má dva režimy rozložení: **Proces** a **vlákna**. Toto nastavení definuje největší jednotka organizace. Výchozí hodnota je režim rozložení **procesu**, což znamená, že aktivity jsou seskupené podle procesy v grafu.  
  
###### <a name="execution-list"></a>Seznam spuštění  
 Můžete vybrat, který proces nebo vlákno, který se má zobrazit v grafu z tohoto rozevíracího seznamu. Například pokud máte soubory trasování dvou klientů (A a B) a jedna služba otevřít a pouze chcete zobrazit v grafu služby a klient A, můžete zrušit zaškrtnutí klienta B ze seznamu.  
  
#### <a name="viewing-trace-details"></a>Zobrazení Podrobnosti o trasování  
 Chcete-li zobrazit podrobné trasování, vyberte v podokně trasování trasování. Podrobnosti se zobrazí v podokně podrobností.  
  
##### <a name="trace-pane"></a>Podokno trasování  
 Horní pravé podokno v prohlížeče trasování služeb představuje podokně trasování. Zobrazí všechna trasování v vybranou aktivitou s dalšími informacemi, například úroveň trasování, ID vlákna a název procesu.  
  
 Nezpracovaná XML trasování můžete zkopírovat do schránky trasování pravým tlačítkem a výběrem **trasování kopírování do schránky**.  
  
##### <a name="detail-pane"></a>Podokno podrobností  
 Dolní části levého podokna prohlížeče trasování služeb je v podokně podrobností. Poskytuje tři karty, chcete-li zobrazit podrobnosti o trasování.  
  
 **Formátu** zobrazení ukazuje údaje organizovanější způsobem. Zobrazí seznam všech známých elementů XML v tabulkách a stromové struktury, což usnadňuje čtení a seznamte se s informacemi.  
  
 **XML** zobrazení XML odpovídající vybraného trasování. Podporuje barevné zvýrazňování a syntaxe. Při použití **najít** Pokud chcete hledat řetězce, jde zvýraznit výsledky hledání.  
  
 **Zpráva** zobrazení ukazuje část zprávy XML zprávy protokolu trasování. Je neviditelné při výběru bez zprávy trasování.  
  
### <a name="filtering-wcf-traces"></a>Filtrování trasování WCF  
 Abychom usnadnili analýzu trasování, můžete filtrovat následujícími způsoby:  
  
-   Filtr nástrojů poskytuje přístup k předdefinované a vlastní filtry. Povolit prostřednictvím **zobrazení** nabídky.  
  
-   Předdefinované filtru v prohlížeči je možné selektivně filtrovat součástí trasování WCF. Ve výchozím nastavení je nastavena na Povolit všechna trasování infrastruktury předávání. Nastavení tohoto filtru, jsou definovány v **možnosti filtru** dílčí nabídky v části **zobrazení** nabídky.  
  
-   Vlastní filtry XPath uživatelům plnou kontrolu nad filtrování. Je možné definovat v **vlastní filtr** pod **zobrazení** nabídky.  
  
 Zobrazí se pouze trasování, které prochází všechny filtry.  
  
#### <a name="using-the-filter-toolbar"></a>Pomocí panelu filtru  
 Panel nástrojů filtru se zobrazí v horní části nástroje. Pokud tam není, můžete si ji můžou aktivovat v **zobrazení** nabídky. Na panelu má tři komponenty:  
  
-   Hledat: **Vyhledejte** definuje předmět v operaci filtru. Například pokud chcete najít všechna trasování, které byly, protože ho v rámci procesu X, nastavte pole na X a **prohledávat** pole "Název procesu". Je vybrán tohoto pole se změní na ovládací prvek Výběr data a času při filtrování podle času.  
  
-   Hledat v: Toto pole definuje typ filtr.  
  
-   Úroveň: Nastavení úrovně definuje minimální úroveň trasování povolen filtr. Například pokud je nastavena úroveň a novějšími verzemi na chybu, se zobrazují pouze trasování při chybě a kritickou úroveň. Tento filtr kombinuje kritérii zadanými Hledat a prohledávat.  
  
 **Filtr nyní** tlačítko spustí operace filtru. Některé filtry, a to zejména v případě, že se použijí pro velké datové sady, trvat dlouhou dobu pro dokončení. Při zrušení operace filtru stisknutím klávesy **Zastavit** tlačítko, které se zobrazí ve stavovém řádku v rámci **operace** nabídky.  
  
 **Vymazat** tlačítko obnoví předdefinované a vlastní filtry, které povolí všechna trasování předávání.  
  
#### <a name="filter-options"></a>Možnosti filtrování  
 Prohlížeč automaticky odebrat ze zobrazení trasování WCF. Můžete selektivně odebrat, protože ho vygeneroval určité oblasti služby WCF trasování, například odebrání transakce související trasování ze zobrazení.  
  
 Nastavení tohoto filtru, jsou definovány v **možnosti filtru** dílčí nabídky v části **zobrazení** nabídky.  
  
#### <a name="custom-filters"></a>Vlastní filtry  
 Pokud jste se seznámili s jazyk XML Path (XPath), můžete vytvořit vlastní filtry pro hledání dat trasování pro libovolný prvek XML, které vás zajímají. Filtry jsou přístupné prostřednictvím nástrojů filtru.  
  
 Vlastní filtry může obsahovat parametry. Můžete také importovat existující vlastní filtry.  
  
##### <a name="creating-a-custom-filter"></a>Vytvoření vlastního filtru  
 Filtry lze vytvořit dvěma způsoby:  
  
###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Vytváří se vlastní filtr pomocí Průvodce šablony  
 Můžete kliknout stávající trasování a vytvořit filtr na základě struktury trasování. Tento příklad vytvoří vlastní filtr na základě ID vlákna.  
  
1. V podokně trasování v horní pravé části prohlížeče vyberte trasování, který obsahuje element, který chcete filtrovat.  
  
2. Klikněte na tlačítko **vytvořit vlastní filtr** tlačítko umístěné v horní části podokna trasování.  
  
3. V dialogovém okně, které se zobrazí zadejte název filtru. V tomto příkladu zadejte `Thread ID`. Můžete také zadat popis filtru.  
  
4. Zobrazení stromu na levé straně zobrazí strukturu záznam trasování, který jste vybrali v kroku 1. Přejděte k elementu chcete vytvořit podmínku. V tomto příkladu, přejděte na Idvlákna nacházely ve jazyka XPath: /E2ETraceEvent/System/Execution/@ThreadID uzlu. Dvakrát klikněte na atribut Idvlákna ve stromovém zobrazení. Tím se vytvoří výraz atributu na pravé straně dialogového okna.  
  
5. Změňte pole parametru pro podmínku Idvlákna z žádný "{0}". Tento krok povoluje Idvlákna hodnota, která má být nakonfigurováno v případě použití filtru. (Zjistit, jak použít filtr část) Můžete definovat až čtyři parametry. Podmínky jsou kombinované pomocí operátoru OR.  
  
6. Klikněte na tlačítko **Ok** pro vytvoření filtru.  
  
> [!NOTE]
>  Po vytvoření filtru pomocí Průvodce šablonou, je lze upravovat pouze ručně. Není možné aktivovat Průvodce pro filtr, který byl vytvořen dříve. Kromě toho podmínky filtru XPath vytvořené v Průvodci vytvořením šablony jsou kombinované pomocí operátoru OR. Pokud budete potřebovat a operace, můžete upravit výraz filtru, po jejím vytvoření.  
  
###### <a name="creating-a-custom-filter-manually"></a>Ruční vytvoření vlastního filtru  
 Vlastní filtry nabídka umožňuje zadat filtrech XPath ručně.  
  
1. V nabídce Zobrazit, klikněte **vlastní filtry** položky nabídky.  
  
2. V zobrazeném dialogovém okně klikněte na tlačítko **nový.**  
  
3. Na minimum a zadejte název filtru a výraz XPath výrazů.  
  
4. Klikněte na **OK**.  
  
###### <a name="applying-a-custom-filter"></a>Použití vlastního filtru  
 Po vytvoření vlastního filtru, i když byl přístupný panelu filtru. Vyberte filtr, který má být použita v **prohledávat** pole panelu filtru. V předchozím příkladu vyberte "ID vlákna.  
  
1. Zadejte hodnotu v hledáte **najít** pole. V našem příkladu zadejte ID vlákna, které chcete vyhledat.  
  
2. Klikněte na tlačítko **filtr nyní**a podívejte se na výsledek operace.  
  
 Je-li filtr používá více parametry, zadejte je pomocí ";" jako oddělovač v **najít** pole. Například následující řetězec definuje 3 parametry: "1; findValue text". V prohlížeči se vztahuje na '1' {0} parametr filtru. 'findValue' a 'text' se použijí u {1} a {2} v uvedeném pořadí.  
  
###### <a name="sharing-custom-filters"></a>Sdílení vlastní filtry  
 Vlastní filtry lze sdílet mezi různými relacemi a různí uživatelé. Můžete exportovat do souboru definice filtry a importování tohoto souboru v jiném umístění.  
  
 Import vlastního filtru:  
  
1. V **zobrazení** nabídky, klikněte na tlačítko **vlastní filtry**.  
  
2. V dialogovém okně, které se otevře, klikněte na tlačítko **Import** tlačítko.  
  
3. Přejděte k souboru vlastního filtru (.stvcf), klikněte na soubor a klikněte na tlačítko **otevřít** tlačítko.  
  
 Export vlastního filtru:  
  
1. V nabídce Zobrazit, klikněte na tlačítko **vlastní filtry**.  
  
2. V dialogovém okně, které se otevře vyberte filtr, který chcete exportovat.  
  
3. Klikněte na tlačítko **exportovat** tlačítko.  
  
4. Zadejte název a umístění souboru definice vlastního filtru (.stvcf) a klikněte na tlačítko **Uložit** tlačítko.  
  
> [!NOTE]
>  Tyto vlastní filtry lze pouze importovat a exportovat z prohlížeče trasování služeb. Nemůže být přečteny další nástroje.  
  
### <a name="finding-data"></a>Vyhledávání dat  
 V prohlížeči nabízí tyto způsoby vyhledat data:  
  
-   Panel nástrojů najít poskytuje rychlý přístup k nejběžnější možnosti hledání.  
  
-   Dialogové okno hledání nabízí že další možnosti hledání. Je přístupné prostřednictvím **upravit** nabídky, nebo krátké kláves Ctrl + F.  
  
 Panel nástrojů hledání se zobrazí v horní části okna. Pokud tam není, můžete si ji můžou aktivovat v **zobrazení** nabídky. Na panelu má dvě součásti:  
  
-   Najdete: Umožňuje Zadejte hledaná klíčová slova.  
  
-   Oblast hledání: Umožňuje zadat rozsah hledání. Můžete vybrat, jestli se má hledat ve všech aktivitách nebo v rámci aktuální aktivity.  
  
 Dialogové okno hledání poskytuje dvě další možnosti:  
  
-   Naleznete cíl:  
  
    -   Možnost "nezpracovaných dat protokolu" vyhledá klíčového slova ve všech nezpracovaná data.  
  
    -   Možnosti "XML Text" a "Atribut XML" vyhledat pouze v elementů XML.  
  
    -   Možnost "Zaznamenána zpráva" vyhledá klíčové slovo pouze v zprávy.  
  
-   Ignorujte kořenové aktivity: Hledání ignoruje trasování v aktivitě "000000000000". To zvyšuje výkon velké trasovací soubory po tisíce trasování, většina z nich jsou přenosy kořenovou aktivitu.  
  
### <a name="navigating-traces"></a>Navigace trasování  
 Protože trasování se zaznamenávají krok za krokem při spuštění aplikace, navigace trasování vám mohou pomoci při ladění aplikace. Prohlížeče trasování služeb poskytuje různé způsoby, jak vracet se v trasování.  
  
#### <a name="step-forward-or-backward"></a>Krok dopředu nebo dozadu  
 Pokud považujete za každý trasování jako řádek kódu v programu, krokování vpřed je velmi podobný "Krok za" v Visual Studio integrované vývojové prostředí (IDE). Rozdíl je, že můžete také krokovat zpět v trasování. Procházení dopředu znamená přechod na další trasování v rámci aktivity.  
  
-   Krok vpřed: Použití **aktivity** nabídky nebo stisknutím klávesy "F10". V podokně trasování můžete použít i klíč šipka "dolů".  
  
-   Krokovat zpět: Použití **aktivity** nabídky nebo stisknutím klávesy "F9". V podokně trasování můžete použít i klíč šipka "nahoru".  
  
> [!NOTE]
>  To může trvat je k aktivitě, ke kterým dochází v jiném procesu nebo i v jiném počítači, protože zpráv WCF mohou obsahovat ID, které jsou rozmístěny počítače aktivity.  
  
#### <a name="follow-transfer"></a>Postupujte podle přenosu  
 Přenos trasování jsou speciální trasování v trasovacím souboru. Aktivita, mohou předávat na jinou aktivitu metodou přenos trasování. Například "Aktivita A", mohou předávat "Aktivita b". V takovém případě je přenos trasování v "Aktivity A" s názvem "na: Aktivita"a ikonu převodu. Přenos trasování je propojení těchto dvou trasování. V "Aktivita B" můžou být dostupné taky na konci aktivity přenést zpět do "Aktivitě A" přenos trasování. To se podobá volání funkce v programech: Volá B, B a vrátí.  
  
 "Sledovat přenos" je podobný "Krokování s vnořením" ladicího programu. Následující přenos z A B. Nemá žádný vliv na ostatní trasování.  
  
 Postupujte podle přenos dvěma způsoby: pomocí myši nebo klávesnice:  
  
-   Pomocí myši: Klikněte dvakrát na přenos trasování v podokně trasování.  
  
-   Pomocí klávesnice: Přenos trasování vyberte a použijte "Přenos postupujte podle" v **aktivity** nabídky nebo stisknutím klávesy "F11"  
  
> [!NOTE]
>  V mnoha případech po aktivitě A přenese aktivita B, aktivity A počká, dokud aktivita B přenosy zpět na aktivitu A. To znamená, že má aktivita A bez trasování zaznamenána během doby, kdy je aktivita B aktivně trasování. Je však také možné, že aktivity A nečeká a pokračuje do protokolu trasování. Je také možné, že aktivita B nepřenese zpět na aktivitu A. Proto jsou stále neliší od volání funkce v tomto smyslu přenosy aktivit. Rozumíte aktivity přenosů lepších v zobrazení grafu.  
  
#### <a name="jump-to-next-or-previous-transfer"></a>Přejít na další nebo předchozí přenosu  
 Při analýze aktuální aktivitu nebo vybrané aktivity při výběru více aktivit, můžete rychle najít aktivity, které se přenese na. "Přechod na přenos" umožňuje najít další přenos trasování v rámci aktivity. Jakmile najdete přenos trasování, vám pomůže "Sledovat přenos" krokování s vnořením do další aktivity.  
  
-   Přejít na další přenos: Použití **aktivity** nabídky nebo stisknutím klávesy "Ctrl + F10".  
  
-   Přejít na předchozí přenos: Použití **aktivity** nabídky nebo stisknutím klávesy "Ctrl + F9".  
  
#### <a name="navigate-in-graph-view"></a>Přejděte v zobrazení grafu  
 I když přejdete podokna aktivit a trasování je podobné ladění, pomocí **grafu** zobrazení poskytuje mnohem lepší prostředí v navigačním panelu. Další informace jsou uvedeny v části "Zobrazení grafu".  
  
### <a name="loading-large-trace-files"></a>Načítání velkých trasovací soubory  
 Trasovací soubory mohou být značně velké. Pokud zapnete trasování na úrovni "Verbose", výsledný soubor trasování pro spuštění několika minut můžete snadno třeba stovek megabajtů nebo i větší v závislosti na rychlosti a komunikace vzoru sítě.  
  
 Při velmi velké trasovací soubor otevřete v prohlížeče trasování služeb, může negativně ovlivněn výkon systému. Načítací rychlosti a doby odezvy po načtení může být pomalé. Skutečná rychlost se liší od času v závislosti na konfiguraci hardwaru. Ve většině počítačů načítání trasovací soubor, který je větší než 200 milionů má dopad výkonu. Pro soubory trasování je větší než 1G může nástroj použít všechnu dostupnou paměť, nebo přestane reagovat velmi dlouhou dobu.  
  
 Pokud se chcete vyhnout pomalé načítání a dobu odezvy v analýze velkých trasovací soubory, prohlížeče trasování služeb poskytuje funkci s názvem "Částečné načtení", který načte pouze malou část trasování v čase. Například může mít více než 1GB, běží na serveru pro několik dní trasovací soubor. Když chcete analyzovat trasování došlo k chybám, není potřeba celý trasovací soubor otevřete. Místo toho můžete načíst trasování z určitého období čas, kdy pravděpodobně došlo k chybě. Vzhledem k tomu, že obor je menší, nástroj prohlížeče trasování služeb můžete načíst soubor rychleji a vy můžete identifikovat chyby pomocí menší sadu protokolovaných data.  
  
#### <a name="enabling-partial-loading"></a>Povolení částečné načtení.  
 Není nutné ručně povolit částečné načtení. Pokud celková velikost souborů trasování, pokusí se načíst překročí 40 MB, prohlížeče trasování služeb automaticky zobrazí částečné načítání dialogové okno pro výběr součástí, které chcete načíst.  
  
> [!NOTE]
>  Protože trasování není v čase rovnoměrně distribuovaných span, délka zadaná v částečné načtení nástrojů nemusí být přímo úměrná velikosti načítání zobrazené časové období. Načítání skutečná velikost může být menší než odhadované velikosti v dialogovém okně částečné načtení.  
  
#### <a name="adjusting-partial-loading"></a>Úprava částečné načtení.  
 Po částečně načtení souboru trasování můžete změnit sadu dat načítán. Můžete provést úpravou částečné načtení nástrojů v horní části okna.  
  
1. Přesunutí panelu nástrojů pomocí myši nebo zadat počáteční a koncový čas.  
  
2. Klikněte na tlačítko **upravit** tlačítko.  
  
## <a name="understanding-trace-icons"></a>Principy trasování ikony  
 Tady je seznam ikon, které používá nástroj prohlížeče trasování služeb v **aktivity** zobrazení **grafu** zobrazení a **trasování** podokně představují různé položky.  
  
> [!NOTE]
>  Některá trasování, které nejsou zařazených do kategorií (například "zpráva je uzavřena") mají žádná ikona.  
  
### <a name="activity-tracing-traces"></a>Aktivita trasování trasování  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Upozornění trasování](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Upozornění trasování: Trasování, které jsou vydávány na úroveň pro upozornění|  
|![Trasování chyb](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Trasování chyb: Trasování, které jsou vydávány na úrovni chyby.|  
|![Trasování spuštění aktivit:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Trasování spuštění aktivit: Trasování, který označuje začátek aktivity. Obsahuje název aktivity. Jako návrháře aplikaci nebo pro vývojáře byste měli definovat jednu aktivitu zahájení trasování podle id aktivity za procesu nebo vlákna.<br /><br /> Pokud id aktivity se šíří přes zdrojů trasování pro trasování korelace, zobrazí se pak více spuštění pro stejný id aktivity (jeden do každého zdroje trasování). Zahájení trasování je vygenerován, pokud je pro zdroj trasování povoleno ActivityTracing.|  
|![Aktivita zastavení trasování](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Aktivita zastavení trasování: Trasování, který označuje konec aktivity. . Obsahuje název aktivity. Jako návrháře aplikaci nebo pro vývojáře byste měli definovat jednu aktivitu Zastavit trasování podle id aktivity za zdroje trasování. Žádné trasování ze zdroje daného trasování se zobrazí po aktivitě zastavit, protože ho vygeneroval tento zdroj trasování, s výjimkou Pokud časové intervaly trasování není dostatečně malý. Pokud k tomu dojde, může být prokládané dvou trasování se stejným časem, včetně zarážku, při zobrazení. Id aktivity se šíří přes zdrojů trasování pro trasování korelace, zobrazí se více zarážek pro stejné id aktivity (jeden do každého zdroje trasování). Zastavení trasování je vygenerován, pokud je pro zdroj trasování povoleno ActivityTracing.|  
|![Aktivita Suspend trasování](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Aktivita Suspend trasování: Trasování, který označuje dobou, kdy aktivita je pozastavená. Žádné trasování jsou emitovány pozastavené aktivity, dokud aktivita obnoví. Pozastavené aktivity označuje, že žádné zpracování se děje v aktivity v rámci zdroje trasování. Trasování operací pozastavit/pokračovat jsou užitečné pro profilování. Pozastavení trasování je vygenerován, pokud je pro zdroj trasování povoleno ActivityTracing.|  
|![Pokračování aktivity trasování](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|Trasování činnosti obnovení: Trasování, který označuje čas, kdy aktivita obnovení poté, co bylo pozastaveno. Trasování může znovu vygenerován v této aktivitě. Trasování operací pozastavit/pokračovat jsou užitečné pro profilování. Obnovit trasování je vygenerován, pokud je pro zdroj trasování povoleno ActivityTracing.|  
|![Transfer](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Přenos: Trasování, který je vygenerován při převodu logické řízení toku z jedné aktivity do druhé. Aktivity, které mohou být přenos může i nadále provádět práci paralelně na aktivitu, kterou přenos přejde na. Přenos trasování je vygenerován, pokud je pro zdroj trasování povoleno ActivityTracing.|  
|![Transfer From](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Přenos z: Trasování, který definuje přenos z jiné aktivity do aktuální aktivitu.|  
|![Transfer To](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Přenést do: Trasování, který definuje přenos logické řízení toku z aktuální aktivity k jiné aktivitě.|  
  
### <a name="wcf-traces"></a>Trasování WCF  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Zprávy protokolu trasování](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Zprávy trasování protokolu: Trasování, které jsou vydávány, když se zaznamená zprávu WCF funkcí protokolování zpráv, když `System.ServiceModel.MessageLogging` zdroj trasování je povolené. Kliknutím na toto trasování zobrazí zprávu. Existují čtyři body konfigurovat protokolování zprávy: ServiceLevelSendRequest, TransportSend, TransportReceive a ServiceLevelReceiveRequest, což je také možné zadat tak, `messageSource` atribut v protokolu trasování zpráv.|  
|![Zprávy trasování přijaté](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Trasování přijatých zpráv: Trasování, které jsou vydávány při doručení zprávy do WCF, pokud `System.ServiceModel` zdroj trasování je povolené na úrovni informace nebo Verbose. Trasování je nezbytné pro zobrazení šipky korelace zprávu v aktivitě **grafu** zobrazení.|  
|![Zprávy trasování odeslaných](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Trasování odeslaných zpráv: Trasování, které jsou vydávány při odesílání zprávy WCF, pokud `System.ServiceModel` zdroj trasování je povolené na úrovni informace nebo Verbose. Trasování je nezbytné pro zobrazení šipky korelace zprávu v aktivitě **grafu** zobrazení.|  
  
### <a name="activities"></a>Aktivity  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Activity](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Aktivita: Označuje, že je aktuální aktivita Obecná aktivita.|  
|![Kořenová aktivita](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Kořenová aktivita: Označuje kořenové aktivity procesu.|  
  
### <a name="wcf-activities"></a>Aktivity WCF  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Environment activity](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Aktivita prostředí: Aktivita, která vytvoří, otevře se nebo zavře WCF hostitele nebo klienta. Tato aktivita se zobrazí chyby, ke kterým došlo během těchto fází.|  
|![Listen activity](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Naslouchání aktivity: Aktivita, která protokoluje související s naslouchací proces trasování. Uvnitř této aktivity můžeme si prohlédnout žádosti o připojení a informace o naslouchací proces.|  
|![Bajty aktivita příjmu](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Bajty aktivita příjmu: Aktivity, která seskupuje všechna trasování týkající se přijímání Příchozí bajty v připojení mezi dva koncové body. Tato aktivita je nezbytné v korelaci s aktivitami přenosu, které rozšíří své id aktivity, jako je například http.sys. Chyby připojení, jako je například přeruší se zobrazí v rámci této aktivity.|  
|![Zpracování zpráv aktivity](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Zpracování zpráv aktivity: Aktivity, která seskupuje trasování související s vytvořením zprávy WCF. Chyby vzniklé v důsledku chybných obálky nebo poškozená zpráva se zobrazí v této aktivitě. Uvnitř této aktivity jsme mohli prohlédnout záhlaví zprávy zobrazíte, pokud id aktivity byla rozšířena z volající. Pokud je to pravda, pokud jsme přenést do procesu akce aktivity (Další), jsme můžete také přiřadit pro danou aktivitu rozšíří aktivity id korelace mezi volající nebo volaný trasování.|  
|![Zprávy protokolu trasování](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Aktivitu procesu akce: Aktivity, která seskupuje všechna trasování související s WCF žádostí napříč dva koncové body. Pokud `propagateActivity` je nastavena na `true` na oba koncové body v konfiguraci, všechna trasování z oba koncové body jsou sloučeny do jedné aktivity pro přímou spojitost s míněním. Tato aktivita bude obsahovat chyby kvůli přenosu nebo zabezpečení, zpracování, rozšíření na hranici kód uživatele a zpět (pokud existuje odpověď).|  
|![Zpracování zpráv aktivity](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Aktivita uživatelský kód spuštění: Aktivity, která seskupuje uživatele trasování kódu pro zpracování požadavku.|  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Pokud nemáte oprávnění k zápisu do registru, získáte následující chybová zpráva "Microsoft Service prohlížeče trasování nebyl registrován v systému" při použití "`svctraceviewer /register`" příkaz pro registraci nástroje. V tomto případě by měl přihlásit pomocí účtu, který má oprávnění k zápisu do registru.  
  
 Kromě toho nástroj prohlížeče trasování služeb zapisuje některá nastavení (například vlastní filtry a možnosti filtru) SvcTraceViewer.exe.settings souboru ve složce jeho sestavení. Pokud nemáte oprávnění ke čtení souboru, stále můžete spustit nástroj, ale nelze načíst nastavení.  
  
 Pokud se zobrazí chybová zpráva "došlo k neznámé chybě při zpracování trasování na jeden nebo více" při otevírání souboru ETL, znamená to, že formát ETL soubor je neplatný.  
  
 Pokud otevřete protokol trasování vytvořené pomocí arabském operačním systému, můžete si všimnout, který čas, kdy filtr nefunguje. Například roku 2005 odpovídá rok 1427 Arabské kalendáře. Časový rozsah podporovaný filtr nástroje prohlížeče trasování služeb však nepodporuje data starší než 1752. To může znamenat, že zatím nejste schopni vybrat správné datum ve filtru. Chcete-li vyřešit tento problém, můžete vytvořit vlastní filtr (**zobrazení/vlastní filtry**) pomocí výrazu XPath zahrnout konkrétní časové období.  
  
## <a name="see-also"></a>Viz také:

- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Konfigurace trasování](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Komplexní trasování](./diagnostics/tracing/end-to-end-tracing.md)
