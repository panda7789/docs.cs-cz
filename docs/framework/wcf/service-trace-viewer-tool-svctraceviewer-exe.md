---
title: Prohlížeč trasování služeb (SvcTraceViewer.exe)
description: Použijte prohlížeč trasování služby ke sloučení, zobrazení a filtrování zpráv trasování v protokolu, abyste mohli diagnostikovat, opravovat a ověřovat problémy se službou WCF.
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 0ad6094965291a965346522688a8334abbd4e6b3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244566"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Prohlížeč trasování služeb (SvcTraceViewer.exe)

Nástroj pro prohlížeč trasování služby Windows Communication Foundation (WCF) pomáhá analyzovat diagnostické trasování, které jsou generovány službou WCF. Prohlížeč trasování služby poskytuje způsob, jak snadno sloučit, zobrazit a filtrovat zprávy trasování v protokolu, abyste mohli diagnostikovat, opravovat a ověřovat problémy se službou WCF.

## <a name="configuring-tracing"></a>Konfigurace trasování

Trasování diagnostiky poskytují informace, které ukazují, co se děje v rámci operace vaší aplikace. Jak název napovídá, můžete sledovat operace z jejich zdroje do cíle a také do mezilehlých bodů.

Trasování můžete nakonfigurovat pomocí konfiguračního souboru aplikace – buď Web.config pro aplikace hostované na webu, nebo *AppName*. config pro aplikace hostované v místním prostředí. Například:

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

V tomto příkladu je zadán název a typ naslouchacího procesu trasování. Naslouchací proces má název `sdt` a jako typ se přidá standardní naslouchací proces trasování .NET Framework (System.Diagnostics.XmlWriterTraceListener). `initializeData`Atribut slouží k nastavení názvu souboru protokolu pro daný naslouchací proces `SdrConfigExample.e2e` . Pro soubor protokolu můžete použít plně kvalifikovanou cestu k jednoduchému názvu souboru.

Příklad vytvoří soubor v kořenovém adresáři s názvem SdrConfigExample. e2e. Když použijete Prohlížeč trasování k otevření souboru, jak je popsáno v části otevření a zobrazení trasovacích souborů WCF, uvidíte všechny zprávy, které byly odeslány.

Úroveň trasování je řízena `switchValue` nastavením. Dostupné úrovně trasování jsou popsány v následující tabulce.

|Úroveň trasování|Description|
|-----------------|-----------------|
|Kritické|– Protokoluje položky protokolu selhání-rychlá a protokol událostí a sleduje informace korelace. Níže jsou uvedeny některé příklady použití kritické úrovně:<br />-Vaše doména AppDomain byla vypnuta z důvodu neošetřené výjimky.<br />– Aplikaci nelze spustit.<br />– Zpráva, která způsobila selhání, pochází z procesu MyApp.exe.|
|Chyba|– Protokoluje všechny výjimky. Úroveň chyby můžete použít v následujících situacích:<br />– Došlo k chybě kódu z důvodu neplatné výjimky přetypování.<br />– Výjimka vytvoření koncového bodu, která selhala při spuštění, způsobuje selhání aplikace.|
|Upozornění|-Existuje stav, který může následně způsobit chybu nebo kritickou chybu. Tuto úroveň můžete použít v následujících situacích:<br />-Aplikace přijímá více požadavků, než umožňuje nastavení omezení.<br />-Fronta příjmu je 98% své nakonfigurované kapacity.|
|Informace|– Zprávy užitečné pro monitorování a diagnostiku stavu systému, měření výkonu nebo profilování se generují. Tyto informace můžete využít k plánování kapacity a správě výkonu. Tuto úroveň můžete použít v následujících situacích:<br />– Došlo k chybě poté, co zpráva dosáhla aplikace AppDomain a byla deserializována.<br />– Při vytváření vazby HTTP došlo k chybě.|
|Verbose|– Trasování na úrovni ladění pro uživatelský kód i obsluhu. Nastavte tuto úroveň v těchto případech:<br />Nejste si jistí, která metoda ve vašem kódu byla volána, když došlo k chybě.<br />– Máte nakonfigurovaný nesprávný koncový bod a službu se nepovedlo spustit, protože položka v úložišti rezervací je zamčená.|
|ActivityTracing|Flow události mezi aktivitami zpracování a komponentami.<br /><br /> Tato úroveň umožňuje správcům a vývojářům korelovat aplikace ve stejné doméně aplikace.<br /><br /> -Trasování pro hranice aktivity: Spustit/zastavit.<br />– Trasování pro přenosy.|

 Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V ukázkové konfiguraci se naslouchací proces nazývá `sdt` a `System.Diagnostics.XmlWriterTraceListener` jako typ se přidá standardní naslouchací proces trasování () .NET Framework. Slouží `initializeData` k nastavení názvu souboru protokolu pro daný naslouchací proces. Kromě toho můžete použít plně kvalifikovanou cestu k jednoduchému názvu souboru.

Počínaje .NET Framework 4,8 se v některých motivech s vysokým kontrastem zobrazují ovládací prvky ComboBox ve správné barvě. Tuto změnu můžete zakázat odebráním následujícího nastavení ze souboru *svcTraceViewer.exe.config* :

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

## <a name="using-the-service-trace-viewer-tool"></a>Použití nástroje pro prohlížeč trasování služby

### <a name="opening-and-viewing-wcf-trace-files"></a>Otevírání a zobrazování sledovacích souborů WCF

Prohlížeč trasování služby podporuje tři typy souborů:

- Trasovací soubor WCF (. svcLog)

- Soubor trasování událostí (. ETL)

- Trasovací soubor Crimson

 Prohlížeč trasování služby umožňuje otevřít libovolný podporovaný trasovací soubor, přidat a integrovat další trasovací soubory nebo otevřít a sloučit skupinu trasovacích souborů současně.

##### <a name="to-open-a-trace-file"></a>Otevření trasovacího souboru

1. Spusťte prohlížeč trasování služby pomocí příkazového řádku a přejděte do umístění instalace WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) a pak zadejte `SvcTraceViewer.exe` .

> [!NOTE]
> Nástroj pro prohlížeč trasování služby může přidružit dva typy souborů:. svclog a. stvproj. Pomocí dvou parametrů na příkazovém řádku můžete zaregistrovat a zrušit registraci přípon souborů.
>
> /Register: Zaregistrujte přidružení přípon souborů ". svclog" a ". stvproj" s SvcTraceViewer.exe
>
> /Unregister: zrušte registraci přidružení přípon souborů ". svclog" a ". stvproj" s SvcTraceViewer.exe

1. Po spuštění prohlížeče trasování služby klikněte na položku **soubor** a pak na položku **otevřít**. Přejděte do umístění, kde jsou uloženy vaše trasovací soubory.

2. Dvakrát klikněte na trasovací soubor, který chcete otevřít.

    > [!NOTE]
    > Stiskněte klávesu SHIFT a kliknutím na více trasovacích souborů je vyberte a otevřete současně. Prohlížeč trasování služby sloučí obsah všech souborů a prezentuje jedno zobrazení. Můžete například otevřít trasovací soubory klienta i služby. To je užitečné v případě, že jste povolili protokolování zpráv a šíření aktivit v konfiguraci. Tímto způsobem můžete ověřit výměnu zpráv mezi klientem a službou. Do prohlížeče lze také přetáhnout více souborů nebo použít kartu **projekt** . Další podrobnosti najdete v části Správa projektu.

3. Chcete-li přidat další trasovací soubory do kolekce, která je otevřena, klikněte na položku **soubor** a pak na položku **Přidat**. V okně, které se otevře, přejděte do umístění trasovacích souborů a dvakrát klikněte na soubor, který chcete přidat.

> [!CAUTION]
> Nedoporučujeme načítat soubor protokolu trasování větší než 200 MB. Pokud se pokusíte načíst soubor větší než tento limit, proces načítání může trvat dlouhou dobu v závislosti na prostředku počítače. Nástroj pro prohlížeč trasování služby nemusí reagovat po dlouhou dobu nebo může vyčerpat paměť vašeho počítače. Doporučuje se nakonfigurovat částečné načítání, abyste tomu předešli. Další informace o tom, jak to provést, naleznete v části "načítání velkých souborů trasování".

#### <a name="event-tracing-and-crimson-tracing"></a>Trasování událostí a trasování Crimson

Nativní formát prohlížeče je formát trasování aktivity, který WCF emituje. Trasování, která jsou generována v jiném formátu, musí být převedena předtím, než je prohlížeč zobrazí. V současné době kromě formátu trasování aktivit prohlížeč podporuje trasování událostí a trasování Crimson.

Když otevřete soubor, který neobsahuje trasování aktivity, prohlížeč se pokusí soubor převést. Je nutné zadat název a umístění souboru, který bude obsahovat převedená data trasování. Po převedení dat prohlížeč zobrazí obsah nového souboru.

> [!NOTE]
> Při převodu se vyžaduje místo na disku pro uložení převedených dat trasování. Ujistěte se, že máte dostatek místa na disku pro uložení dat před zahájením převodu. V opačném případě se převod nezdařil.

### <a name="managing-projects"></a>Správa projektů

Prohlížeč podporuje projekty pro usnadnění prohlížení více trasovacích souborů. Například pokud máte trasovací soubor klienta a trasovací soubor služby, můžete je přidat do projektu. Pak při každém otevření projektu se všechny trasovací soubory v projektu načtou současně.

Existují dva způsoby, jak spravovat projekty:

- V nabídce **soubor** můžete otevřít, Uložit a zavřít projekty.

- Na kartě **projekt** můžete přidat soubory do projektu.

### <a name="viewing-wcf-traces"></a>Zobrazení trasování WCF

WCF generuje trasování pomocí formátu trasování aktivit. V modelu trasování aktivit se jednotlivá trasování seskupují do aktivit podle jejich účelu. Logický tok řízení se přenáší mezi aktivitami. Například během životnosti aplikace se zobrazí mnoho "aktivity odeslání zprávy" a zmizí. Další informace o tom, jak zobrazit trasování a aktivity a také uživatelské rozhraní prohlížeče trasování služby, najdete v tématu [použití prohlížeče trasování služby pro zobrazení korelačních trasování a odstraňování potíží](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).

#### <a name="switching-to-different-views"></a>Přechod do různých zobrazení

Prohlížeč trasování služby poskytuje následující různá zobrazení. Zobrazují se jako karty v levém podokně prohlížeče a je možné k nim také přicházet z nabídky **zobrazení** .

- Zobrazení aktivity

- Zobrazení projektu

- Zobrazení zpráv

- Zobrazení grafu

##### <a name="activity-view"></a>Zobrazení aktivity

Po otevření trasovacích souborů uvidíte trasování seskupené do aktivit a zobrazí se v zobrazení **aktivita** v levém podokně.

Zobrazení **aktivity** zobrazuje názvy aktivit, počet trasování v aktivitě, čas trvání, čas spuštění a čas ukončení.

Kliknutím na některou z uvedených aktivit se trasování v této aktivitě zobrazí v podokně trasování na pravé straně. Pak můžete vybrat trasování a zobrazit jeho podrobnosti.

Stisknutím klávesy **CTRL** nebo **SHIFT** a kliknutím na požadované aktivity můžete vybrat více aktivit. V podokně trasování se zobrazí všechna trasování vybraných aktivit.

Můžete dvakrát kliknout na aktivitu a zobrazit ji v zobrazení **grafu** . Alternativním způsobem je výběr aktivity a přepnutí do zobrazení **grafu** .

> [!NOTE]
> Aktivita "000000000000" je zvláštní aktivita, kterou nelze zobrazit v zobrazení grafu. Vzhledem k tomu, že se k němu vztahují všechny ostatní aktivity, má zobrazení této aktivity závažný dopad na výkon.

Seznam aktivit můžete seřadit kliknutím na název sloupce. Aktivity, které obsahují trasování upozornění, mají žluté pozadí a ty, které obsahují trasování chyb, mají červenou barvu.

Existují různé typy aktivit a každý typ odpovídá ikoně na levé straně každé aktivity. Pro svůj význam se můžete podívat na oddíl porozumění Ikonaem trasování.

##### <a name="project-view"></a>Zobrazení projektu

Toto zobrazení umožňuje spravovat trasovací soubory v aktuálním projektu. Další podrobnosti najdete v části Správa projektu.

##### <a name="message-view"></a>Zobrazení zpráv

Toto zobrazení umožňuje zobrazit všechna trasování protokolu zpráv, včetně akcí, data a času, procesu, aktivit a z/do a přejít k podrobnostem o přidruženém trasování protokolu zpráv. Můžete seskupovat trasování protokolu zpráv podle hranice aktivity, procesu/vlákna nebo odeslat & přijmout pro snazší navigaci toku zprávy.

##### <a name="graph-view"></a>Zobrazení grafu

Toto zobrazení zobrazuje data trasování pro danou aktivitu ve formuláři grafu. Formulář grafu umožňuje zobrazit stupňovaný provádění událostí a vztahy mezi několika aktivitami při přesunu dat mezi nimi.

Chcete-li přepnout do zobrazení **grafu** , vyberte aktivitu v zobrazení **aktivity** a klikněte na kartu **aktivita** nebo na trasování protokolu zpráv v zobrazení **zprávy** . Pokud je načteno více trasovacích souborů a aktivita zahrnuje trasování z více než jednoho souboru, zobrazí se v zobrazení grafu všechna relevantní trasování. Dvojím kliknutím na aktivity a trasování protokolu zpráv vás zavedete do zobrazení **grafu** .

V zobrazení **grafu** každý svislý sloupec představuje aktivitu a každý blok ve sloupci představuje trasování. Aktivity jsou seskupeny podle procesu (nebo vlákna). Malé šipky mezi aktivitami reprezentují přenosy. Velké šipky mezi procesy představují výměnu zpráv. Aktivita v výběru je vždy žlutá.

###### <a name="selecting-traces-in-the-graph"></a>Výběr trasování v grafu

1. Klikněte na blok v grafu.

2. Pomocí kláves nahoru a dolů vyberte své sousední trasování.

3. Sledujte informace o trasování v podokně trasování a podokně podrobností.

###### <a name="expanding-or-collapsing-activity-transfers"></a>Rozbalení nebo sbalení přenosů aktivit

Přenosy aktivity můžete rozbalit, pokud aktivita ve výběru přenese přenos na jinou aktivitu. Umožňuje vám postupovat podle přenosů.

Chcete-li rozbalit nebo sbalit přenosy aktivit,

1. Na levé straně ikony přenosu vyhledejte trasování pro přenos pomocí znaku "+".

2. Klikněte na tlačítko "+" nebo stiskněte klávesy **CTRL** a "+" pomocí klávesnice.

3. Další aktivita se zobrazí v grafu.

4. Na levé straně ikony přenosu se zobrazí znak "-". Klikněte na symbol "-" nebo stiskněte klávesu CTRL a "-", tím se migrace aktivity sbalí.

> [!NOTE]
> Pokud se do ní v aktivitě nachází více přenosů a rozšíříte jeden z přenosů, zobrazí se aktivity, které se zavedou k nové aktivitě z kořenové aktivity. Tyto nové aktivity se zobrazí ve sbaleném formátu. Pokud chcete zobrazit podrobnosti o těchto činnostech, rozbalte je svisle kliknutím na ikonu rozbalení v záhlaví grafu.

###### <a name="expanding-or-collapsing-activities-vertically"></a>Svislé rozbalení nebo sbalení aktivit

Prohlížeč skryje nepotřebné podrobnosti v grafu aktivity sbalením aktivit. Ve sbalené aktivitě nejsou jednotlivá trasování zobrazena. Zobrazí se pouze trasování. Pokud chcete zobrazit všechna trasování v aktivitě, rozbalte aktivitu svisle kliknutím na symbol rozbalení aktivity v záhlaví grafu.

Pokud chcete aktivity rozbalit nebo sbalit svisle,

1. Kliknutím na ikonu "+" v hlavičce aktivity rozbalíte aktivitu svisle.

2. Všimněte si, že všechna trasování jsou zobrazena v grafu.

3. Kliknutím na ikonu-v záhlaví aktivity můžete aktivitu sbalit vertikálně.

4. Všimněte si, že v aktivitě se zobrazují jenom důležité přenosy, protokoly zpráv, upozornění a trasování výjimek.

###### <a name="options"></a>Možnosti

V nabídce **možností** v zobrazení grafu můžete vybrat dvě možnosti.

- Zobrazit trasování hranice aktivity, které když není zaškrtnuto, ignoruje trasování hranice aktivity v grafu.

- Zobrazit trasování bez zpráv, které nezaškrtnutoy, ignorují trasování na úrovni podrobností, s výjimkou trasování zpráv. Ve většině případů jsou trasování podrobné úrovně pro analýzu méně důležitá. Tato možnost je užitečná v případě, že nechcete analyzovat trasování na úrovni podrobností a chcete se zaměřit pouze na důležitější trasování.

###### <a name="layout-mode"></a>Režim rozložení

Prohlížeč má dva režimy rozložení: **proces** a **vlákno**. Toto nastavení definuje největší jednotku organizace. Výchozím režimem rozložení je **proces**, což znamená, že aktivity jsou seskupeny podle procesů v grafu.

###### <a name="execution-list"></a>Seznam spuštění

V tomto rozevíracím seznamu můžete vybrat proces nebo vlákno, které se má zobrazit v grafu. Například pokud máte trasovací soubory dvou klientů (a a B) a jednu službu otevřeli a chcete zobrazit pouze službu a klienta a v grafu, můžete zrušit výběr klienta B ze seznamu.

#### <a name="viewing-trace-details"></a>Zobrazení podrobností trasování

Chcete-li zobrazit podrobnosti trasování, vyberte trasování v podokně trasování. Podrobnosti se zobrazí v podokně podrobností.

##### <a name="trace-pane"></a>Podokno trasování

V pravém horním podokně v prohlížeči trasování služby je podokno trasování. Obsahuje seznam všech trasování ve vybrané aktivitě s dalšími informacemi, například úroveň trasování, ID vlákna a název procesu.

Nezpracovaný kód XML trasování můžete zkopírovat do schránky tak, že kliknete pravým tlačítkem na trasování a vyberete **Kopírovat trasování do schránky**.

##### <a name="detail-pane"></a>Podokno podrobností

Dolní levé podokno v prohlížeči trasování služby je podokno podrobností. Poskytuje tři karty k zobrazení podrobností trasování.

**Formátované** zobrazení zobrazuje tyto informace lépe uspořádaným způsobem. Obsahuje seznam všech známých prvků XML v tabulkách a stromech, což usnadňuje čtení a pochopení informací.

Zobrazení **XML** zobrazuje XML odpovídající vybranému trasování. Podporuje zvýraznění a barvu syntaxe. Když použijete **find** k hledání řetězců, zvýrazní se výsledky hledání.

V zobrazení **zprávy** se zobrazí část zprávy XML v trasování protokolu zpráv. Je neviditelná, když vyberete trasování, které není zprávy.

### <a name="filtering-wcf-traces"></a>Filtrování trasování WCF

Aby bylo možné analýzu sledovat snadněji, můžete je filtrovat následujícími způsoby:

- Panel nástrojů filtru poskytuje přístup k předem definovaným a vlastním filtrům. Dá se povolit v nabídce **zobrazení** .

- Předem definovaný filtr prohlížeče lze použít k selektivnímu filtrování částí trasování WCF. Ve výchozím nastavení je nastaveno, aby bylo možné projít všechna trasování infrastruktury. Nastavení tohoto filtru jsou definována v podnabídce **Možnosti filtru** v nabídce **zobrazení** .

- Vlastní filtry XPath poskytují uživatelům úplnou kontrolu nad filtrováním. Můžou být definované ve **vlastním filtru** v nabídce **zobrazení** .

Zobrazí se pouze trasování, které projde všemi filtry.

#### <a name="using-the-filter-toolbar"></a>Použití panelu nástrojů filtru

Panel nástrojů filtru se zobrazí v horní části nástroje. Pokud není k dispozici, můžete ji aktivovat v nabídce **zobrazení** . Pruh obsahuje tři komponenty:

- Hledat **: vyhledá se** text definující předmět, který se má hledat v operaci filtru. Například pokud chcete najít všechna trasování, která byla vygenerována v kontextu procesu X, nastavte toto pole na hodnotu X a pole **Hledat v** poli název procesu. Toto pole se změní na ovládací prvek selektor data a času, pokud je vybrán filtr založený na čase.

- Hledat v: Toto pole definuje typ filtru, který se má použít.

- Level: nastavení úrovně definuje minimální úroveň trasování povolenou filtrem. Například pokud je úroveň nastavena na Error a up, zobrazí se pouze trasování na úrovni chyba a kritická úroveň. Tento filtr kombinuje s kritérii určenými pro hledání a vyhledávání v.

Tlačítko **filtrovat nyní** spustí operaci filtrování. Některé filtry, zejména pokud jsou aplikovány na velkou datovou sadu, mohou trvat dlouhou dobu. Operaci filtrování můžete zrušit stisknutím tlačítka **zastavit** , které se zobrazí na stavovém řádku v nabídce **operace** .

Tlačítko **clear** obnoví předdefinované a vlastní filtry, aby bylo možné projít všechna trasování.

#### <a name="filter-options"></a>Možnosti filtru

Prohlížeč může ze zobrazení automaticky odebrat trasování WCF. Může selektivně odebrat trasování emitované konkrétními oblastmi služby WCF, například odebrat trasování související s transakcí ze zobrazení.

Nastavení tohoto filtru jsou definována v podnabídce **Možnosti filtru** v nabídce **zobrazení** .

#### <a name="custom-filters"></a>Vlastní filtry

Pokud znáte jazyk XML Path (XPath), můžete ho použít k vytvoření vlastních filtrů pro vyhledávání dat trasování pro jakýkoli XML element zájmu. Filtry jsou přístupné prostřednictvím panelu nástrojů filtru.

Vlastní filtry můžou zahrnovat parametry. Můžete také importovat již existující vlastní filtry.

##### <a name="creating-a-custom-filter"></a>Vytvoření vlastního filtru

Filtry je možné vytvořit dvěma způsoby:

###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Vytvoření vlastního filtru pomocí Průvodce šablonou

Můžete kliknout na existující trasování a vytvořit filtr na základě struktury trasování. Tento příklad vytvoří vlastní filtr na základě ID vlákna.

1. V podokně trasování v pravém horním rohu prohlížeče vyberte trasování, které obsahuje prvek, pro který chcete filtrovat.

2. Klikněte na tlačítko **vytvořit vlastní filtr** nacházející se v horní části podokna trasování.

3. V dialogovém okně, které se zobrazí, zadejte název filtru. V tomto příkladu zadejte `Thread ID` . Můžete také zadat popis filtru.

4. Stromové zobrazení na levé straně zobrazuje strukturu záznamu trasování, kterou jste vybrali v kroku 1. Vyhledejte prvek, pro který chcete vytvořit podmínku. V tomto příkladu přejděte na IDvlákna, který se nachází v uzlu XPath: /E2ETraceEvent/System/Execution/@ThreadID . Dvakrát klikněte na atribut IDvlákna ve stromovém zobrazení. Tím se vytvoří výraz pro atribut na pravé straně dialogového okna.

5. Změňte pole parametru pro podmínku IDvlákna z None na ' {0} '. Tento krok umožňuje nakonfigurovat hodnotu IDvlákna při použití filtru. (Viz část použití filtru) Můžete definovat až čtyři parametry. Podmínky jsou kombinovány pomocí operátoru OR.

6. Kliknutím na tlačítko **OK** vytvořte filtr.

> [!NOTE]
> Po vytvoření filtru pomocí Průvodce šablonou ho lze upravit pouze ručně. Není možné aktivovat Průvodce pro filtr, který byl vytvořen dříve. Kromě toho podmínky filtru XPath vytvořeného v Průvodci šablonou jsou kombinovány pomocí operátoru OR. Pokud budete potřebovat operaci a, můžete upravit výraz filtru po jeho vytvoření.

###### <a name="creating-a-custom-filter-manually"></a>Ruční vytvoření vlastního filtru

Nabídka vlastní filtry umožňuje ruční zadání filtrů XPath.

1. V nabídce zobrazení klikněte na položku nabídky **vlastní filtry** .

2. V dialogovém okně, které se zobrazí, klikněte na **Nový.**

3. V poli minimální zadejte název filtru a výraz XPath.

4. Klikněte na **OK**.

###### <a name="applying-a-custom-filter"></a>Použití vlastního filtru

Po vytvoření vlastního filtru ho budete mít k dispozici i na panelu nástrojů filtru. V poli **Hledat v** panelu nástrojů filtru vyberte filtr, který chcete použít. V předchozím příkladu vyberte možnost ID vlákna.

1. V poli **Najít** , zadejte hledanou hodnotu. V našem příkladu zadejte ID vlákna, které chcete vyhledat.

2. Klikněte na **Filter Now (filtrovat**) a sledujte výsledek operace.

Pokud váš filtr používá více parametrů, zadejte je jako oddělovač v poli **najít, které** používá znak '; '. Například následující řetězec definuje 3 parametry: ' 1; findValue; text '. Prohlížeč použije ' 1 ' na {0} parametr filtru. hodnoty findValue a text jsou aplikovány na {1} a {2} v uvedeném pořadí.

###### <a name="sharing-custom-filters"></a>Sdílení vlastních filtrů

Vlastní filtry je možné sdílet mezi různými relacemi a různými uživateli. Filtry můžete exportovat do souboru definice a importovat tento soubor do jiného umístění.

 Import vlastního filtru:

1. V nabídce **zobrazení** klikněte na **vlastní filtry**.

2. V dialogovém okně, které se otevře, klikněte na tlačítko **Import** .

3. Přejděte do souboru vlastního filtru (. stvcf), klikněte na soubor a klikněte na tlačítko **otevřít** .

Export vlastního filtru:

1. V nabídce zobrazení klikněte na **vlastní filtry**.

2. V dialogovém okně, které se otevře, vyberte filtr, který chcete exportovat.

3. Klikněte na tlačítko **exportovat** .

4. Zadejte název a umístění souboru definice vlastního filtru (. stvcf) a klikněte na tlačítko **Uložit** .

> [!NOTE]
> Tyto vlastní filtry je možné importovat a exportovat jenom z prohlížeče trasování služby. Nelze je číst pomocí jiných nástrojů.

### <a name="finding-data"></a>Hledání dat

Prohlížeč poskytuje následující způsoby, jak najít data:

- Panel nástrojů najít poskytuje rychlý přístup k nejběžnějším možnostem hledání.

- Dialog najít nabízí více možností hledání. Je přístupná prostřednictvím nabídky **Upravit** nebo pomocí krátké klávesy CTRL + F.

V horní části prohlížeče se zobrazí panel nástrojů najít. Pokud není k dispozici, můžete ji aktivovat v nabídce **zobrazení** . Pruh má dvě komponenty:

- Najít: umožňuje zadat klíčové slovo vyhledávání.

- Oblast hledání: umožňuje zadat obor vyhledávání. Můžete vybrat, jestli se mají prohledávat všechny aktivity, nebo jenom aktuální aktivita.

Dialog najít nabízí dvě další možnosti:

- Najít cíl:

  - Možnost "nezpracovaná data protokolu" vyhledává klíčové slovo ve všech nezpracovaných datech.

  - Možnosti "text XML" a "Attribute XML" hledají pouze prvky XML.

  - Možnost "zpráva protokolu" vyhledává klíčové slovo pouze ve zprávách.

- Ignorovat kořenovou aktivitu: hledání ignoruje trasování v aktivitě "000000000000". To zlepšuje výkon u velkých trasovacích souborů, když má kořenová aktivita tisíce trasování, z nichž většinu přenáší.

### <a name="navigating-traces"></a>Navigace v Trasováních

Vzhledem k tomu, že trasování jsou zaznamenávány během běhu aplikace krok za krokem, navigace trasování vám může pomáhat při ladění aplikace. Prohlížeč trasování služby poskytuje různé způsoby navigace v trasování.

#### <a name="step-forward-or-backward"></a>Krok dopředu nebo dozadu

Pokud považujete každé trasování za řádek kódu v programu, krokování předá v integrovaném vývojovém prostředí (IDE) sady Visual Studio je velmi podobné řetězci "Krokovat s". Rozdíl je, že můžete také krokovat zpět v trasování. Krokování znamená přechod k dalšímu trasování v aktivitě.

- Krok nahoru: použijte nabídku **aktivita** nebo stiskněte klávesu F10. V podokně trasování můžete také použít klávesu šipka dolů.

- Krok zpět: použijte nabídku **aktivita** nebo stiskněte F9. V podokně trasování můžete také použít klávesu šipka nahoru.

> [!NOTE]
> To může mít za následek aktivitu, ke které dochází v jiném procesu, nebo dokonce i v jiném počítači, protože zprávy WCF mohou přenášet ID aktivit, která jsou na počítačích.

#### <a name="follow-transfer"></a>Sledovat přenos

Trasování přenosů jsou speciální trasování v trasovacím souboru. Aktivita se může přenášet do jiné aktivity trasováním přenosu. Například "aktivita A" může přenášet do "Activity B". V takovém případě je k dispozici trasování přenosu v "Activity" a "s názvem" to: Activity "a" ikona přenosu ". Toto trasování přenosu je propojení mezi dvěma trasováními. V "aktivitě B" může být také trasování přenosu na konci aktivity pro přenos zpět do "Activity A". Toto je podobné volání funkcí v programech: volání B, a B vrátí.

"Sledování přenosu" se podobá "Krokovat s" v ladicím programu. Sleduje přenos z A do B. Nemá žádný vliv na další trasování.

Existují dva způsoby, jak přenos sledovat: pomocí myši nebo pomocí klávesnice:

- Pomocí myši: dvakrát klikněte na trasování přenosu v podokně trasování.

- Podle klávesnice: Vyberte přenosové trasování a v nabídce **aktivita** použijte příkaz sledovat přenos, nebo stiskněte klávesu F11.

> [!NOTE]
> V mnoha případech, když aktivita A přenáší na aktivitu B, aktivita A počká, dokud aktivita B nepřevede zpět do aktivity A. To znamená, že aktivita A nemá žádné zaznamenané trasování v průběhu období, kdy se aktivita B aktivně sleduje. Nicméně je také možné, že aktivita A nečeká a pokračuje protokolem trasování. Je také možné, že aktivita B nepřenáší zpět do aktivity A. Proto se přenosy aktivit stále liší od volání funkcí v tomto smyslu. V zobrazení grafu můžete pochopit převody aktivit lépe.

#### <a name="jump-to-next-or-previous-transfer"></a>Přejít na další nebo předchozí přenos

Pokud analyzujete aktuální aktivitu nebo vybrané aktivity, pokud je vybráno více aktivit, můžete chtít rychle vyhledat aktivity, na které se přenáší. Možnost přejít na další přenos vám umožní vyhledat další trasování přenosu v aktivitě. Jakmile najdete trasování přenosů, můžete ke krokování další aktivity použít "sledování přenosu".

- Přejít na další přenos: použijte nabídku **aktivita** nebo stiskněte klávesy CTRL + F10.

- Přejít na předchozí přenos: použijte nabídku **aktivita** nebo stiskněte klávesy CTRL + F9.

#### <a name="navigate-in-graph-view"></a>Navigace v zobrazení grafu

I když se navigace v podokně aktivity a podokno trasování podobá ladění, použití zobrazení **grafu** poskytuje mnohem lepší možnosti navigace. Další informace najdete v části "zobrazení grafu".

### <a name="loading-large-trace-files"></a>Načítání velkých trasovacích souborů

Soubory trasování můžou být velmi velké. Pokud například zapnete trasování na úrovni "podrobného", výsledný soubor trasování pro spuštění několika minut může být v závislosti na rychlosti sítě a způsobu komunikace snadno velký.

Když v prohlížeči trasování služby otevřete velmi velký trasovací soubor, může to mít negativní vliv na výkon systému. Rychlost načítání a doba odezvy po načtení může být pomalá. Skutečná rychlost se od času od času liší v závislosti na konfiguraci hardwaru. Ve většině počítačů je načtení trasovacího souboru většího než 200M vážným dopadem na výkon. V případě trasování souborů větších než 1G může nástroj využít veškerou dostupnou paměť, nebo po velmi dlouhou dobu přestat reagovat.

Aby nedošlo k pomalému načítání a době odezvy při analýze velkých trasovacích souborů, prohlížeč trasování služby poskytuje funkci s názvem "částečné načítání", která v daném okamžiku načítá pouze malou část trasování. Můžete mít například trasovací soubor větší než 1 GB, který běží na serveru několik dní. Pokud dojde k nějakým chybám a chcete analyzovat trasování, není nutné otevřít celý trasovací soubor. Místo toho můžete načíst trasování během určité doby, kdy k chybě mohlo dojít. Vzhledem k tomu, že je rozsah menší, může nástroj Prohlížeč trasování služby načíst soubor rychleji a identifikovat chyby pomocí menší sady dat.

#### <a name="enabling-partial-loading"></a>Povolení částečného načítání

Nemusíte ručně povolit částečné načítání. Pokud celková velikost trasovacích souborů, které se pokoušíte načíst, přesáhne 40MB, prohlížeč trasování služby automaticky zobrazí dialogové okno částečného načítání, ve kterém můžete vybrat součást, kterou chcete načíst.

> [!NOTE]
> Vzhledem k tomu, že trasování nelze rovnoměrně rozmístit v časovém intervalu, Délka časového období, které zadáte v panelu nástrojů částečného načítání, nemusí být úměrná zobrazené velikosti načítání. Skutečná velikost načtení může být menší než odhadovaná velikost v dialogovém okně částečné načítání.

#### <a name="adjusting-partial-loading"></a>Úprava částečného načítání

Po částečném načtení trasovacího souboru můžete chtít změnit načtenou datovou sadu. Můžete to udělat tak, že upravíte částečný panel nástrojů načítání v horní části okna prohlížeče.

1. Přesuňte panel nástrojů pomocí myši nebo zadejte čas zahájení a ukončení.

2. Klikněte na tlačítko **Upravit** .

## <a name="understanding-trace-icons"></a>Principy trasovacích ikon

Následující seznam obsahuje ikony, které nástroj pro prohlížeč trasování služby používá v podokně zobrazení **aktivity** , zobrazení **grafu** a **trasování** pro reprezentaci různých položek.

> [!NOTE]
> Některá trasování, která nejsou zařazená do kategorií (například zpráva "zpráva je uzavřená") nemají žádnou ikonu.

### <a name="activity-tracing-traces"></a>Trasování trasování aktivity

|Ikona|Description|
|----------|-----------------|
|![Trasování upozornění](./media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Trasování upozornění: trasování, které je vygenerováno na úrovni upozornění|
|![Trasování chyb](./media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Trasování chyb: trasování, které je vygenerováno na úrovni chyby.|
|![Trasování zahájení aktivity:](./media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Spustit trasování aktivity: trasování, které označuje začátek aktivity. Obsahuje název aktivity. Jako návrhář aplikace nebo vývojář byste měli definovat jednu aktivitu spustit trasování podle ID aktivity na proces nebo vlákno.<br /><br /> Pokud je ID aktivity šířeno napříč zdroji trasování pro korelaci trasování, můžete zobrazit více spuštění pro stejné ID aktivity (jeden na zdroj trasování). Je-li ActivityTracing povolen pro zdroj trasování, je vygenerováno počáteční trasování.|
|![Trasování zastavení aktivity](./media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Trasování zastavení aktivity: trasování, které označuje konec aktivity. . Obsahuje název aktivity. Jako návrhář aplikace nebo vývojář byste měli definovat jednu aktivitu zastavit trasování podle ID aktivity na zdroj trasování. Po zastavení aktivity vygenerovaného tímto zdrojem trasování se nezobrazí žádná trasování z daného zdroje trasování, s výjimkou případů, kdy není členit čas trasování dostatečně malý. Pokud k tomu dojde, mohou být při zobrazení provedená dvě trasování se stejnou časem, včetně stop. Pokud je ID aktivity šířeno napříč zdroji trasování pro korelaci trasování, můžete zobrazit více zarážek pro stejné ID aktivity (jeden pro každý zdroj trasování). Trasování stop je vygenerováno, pokud je pro zdroj trasování povoleno ActivityTracing.|
|![Trasování pozastavení aktivity](./media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Trasování pozastavení aktivity: trasování, které označuje čas pozastavení aktivity. Žádná trasování nejsou vygenerována v pozastavené aktivitě, dokud aktivita nebude pokračovat. Pozastavená aktivita znamená, že v této aktivitě není v oboru zdroje trasování probíhají žádné zpracování. Trasování pozastavení/obnovení je užitečné pro profilaci. Trasování pozastavení je vygenerováno, pokud je pro zdroj trasování povoleno ActivityTracing.|
|![Trasování obnovení aktivity](./media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4E0A-9988-cdc2f7030f17")|Trasování obnovení aktivity: trasování, které označuje čas, po který je aktivita obnovena po pozastavení. Trasování lze v této aktivitě vygenerovat znovu. Trasování pozastavení/obnovení je užitečné pro profilaci. Trasování pokračování je vygenerováno, pokud je pro zdroj trasování povoleno ActivityTracing.|
|![Přenos](./media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Přenos: trasování, které je vygenerováno při přenosu logického toku řízení z jedné aktivity do druhé. Aktivita, ze které pochází přenos, může i nadále provádět práci paralelně s aktivitou, na kterou přenos směřuje. Trasování přenosu je vygenerováno, pokud je pro zdroj trasování povoleno ActivityTracing.|
|![Přenos z](./media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Přenos z: trasování, které definuje přenos z jiné aktivity do aktuální aktivity.|
|![Přenést do](./media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Přenos do: trasování, které definuje přenos logického toku řízení z aktuální aktivity do jiné aktivity.|

### <a name="wcf-traces"></a>Trasování WCF

|Ikona|Description|
|----------|-----------------|
|![Trasování protokolu zpráv](./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Trasování protokolu zpráv: trasování, které je generováno při zaprotokolování zprávy WCF funkcí protokolování zpráv, když `System.ServiceModel.MessageLogging` je povolen zdroj trasování. Kliknutím na toto trasování se zobrazí zpráva. Existují čtyři konfigurovatelné body protokolování pro zprávu: ServiceLevelSendRequest, TransportSend, TransportReceive a ServiceLevelReceiveRequest, které lze také určit pomocí `messageSource` atributu v trasování protokolu zpráv.|
|![Trasování přijalo zprávu](./media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Trasování přijalo zprávu: trasování, které je vygenerováno při přijetí zprávy WCF, pokud `System.ServiceModel` je zdroj trasování povolen na úrovni informací nebo podrobností. Toto trasování je nezbytné pro zobrazení šipky korelace zprávy v zobrazení **grafu** aktivity.|
|![Trasování odeslaných zpráv](./media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Trasování odeslaných zpráv: trasování, které je generováno při odeslání zprávy WCF, pokud je `System.ServiceModel` zdroj trasování povolen na úrovni informací nebo podrobností. Toto trasování je nezbytné pro zobrazení šipky korelace zprávy v zobrazení **grafu** aktivity.|

### <a name="activities"></a>Aktivity

|Ikona|Description|
|----------|-----------------|
|![Aktivita](./media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Activity: označuje, že aktuální aktivita je obecná aktivita.|
|![Kořenová aktivita](./media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Kořenová aktivita: označuje kořenovou aktivitu procesu.|

### <a name="wcf-activities"></a>Aktivity WCF

|Ikona|Description|
|----------|-----------------|
|![Aktivita prostředí](./media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Aktivita prostředí: aktivita, která vytvoří, otevře nebo uzavře hostitele nebo klienta služby WCF. V této aktivitě se objeví chyby, ke kterým došlo během těchto fází.|
|![Aktivita naslouchání](./media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Aktivita naslouchání: aktivita, která protokoluje trasování týkající se naslouchacího procesu. V rámci této aktivity můžeme zobrazit informace o naslouchacího procesu a žádosti o připojení.|
|![Aktivita příjmu bajtů](./media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Aktivita příjmu bajtů: aktivita, která seskupuje všechna trasování související s přijímáním příchozích bajtů v připojení mezi dvěma koncovými body. Tato aktivita je zásadní ve vztahu k dopravním činnostem, které šíří své ID aktivity, například http.sys. V této aktivitě se zobrazí chyby připojení, například přerušení.|
|![Aktivita zpracování zprávy](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Aktivita zpracování zprávy: aktivita, která seskupuje trasování související s vytvořením zprávy WCF. V této aktivitě se zobrazí chyby z důvodu chybné obálky nebo poškozené zprávy. V rámci této aktivity můžeme zkontrolovat záhlaví zpráv, abyste zjistili, jestli se od volajícího rozšířilo ID aktivity. Pokud je to pravda, můžeme při přenosu na aktivitu akce procesu (další ikona) přiřadit k této aktivitě ID šířené aktivity pro korelaci volajícího a volaného trasování.|
|![Trasování protokolu zpráv](./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Aktivita zpracování akce: aktivita, která seskupuje všechna trasování související se žádostí WCF napříč dvěma koncovými body. Pokud `propagateActivity` je nastaveno na hodnotu `true` u obou koncových bodů v konfiguraci, jsou všechna trasování z obou koncových bodů sloučena do jedné aktivity pro přímou korelaci. Tato aktivita bude obsahovat chyby z důvodu přenosu nebo zpracování zabezpečení, rozšíření na hranice uživatelského kódu a zpět (pokud existuje odpověď).|
|![Aktivita zpracování zprávy](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Aktivita spustit kód uživatele: aktivita, která seskupuje trasování uživatelských kódů pro zpracování požadavku.|

## <a name="troubleshooting"></a>Odstraňování potíží

Pokud nemáte oprávnění k zápisu do registru, zobrazí se tato chybová zpráva "při použití `svctraceviewer /register` příkazu k registraci nástroje se v systému nezaregistruje Microsoft Service Trace Viewer. Pokud k tomu dojde, měli byste se přihlásit pomocí účtu, který má k registru přístup pro zápis.

Kromě toho nástroj Prohlížeč trasování služby zapisuje některá nastavení (například vlastní filtry a možnosti filtru) do souboru SvcTraceViewer.exe. Settings ve složce sestavení. Pokud nemáte oprávnění ke čtení tohoto souboru, můžete ho přesto spustit, ale nastavení nemůžete načíst.

Pokud se zobrazí chybová zpráva "při zpracování jednoho nebo více trasování" při otevírání souboru. ETL došlo k neznámé chybě, znamená to, že formát souboru. ETL je neplatný.

Pokud otevřete protokol trasování vytvořený pomocí arabského operačního systému, můžete si všimnout, že filtr času nefunguje. Například rok 2005 odpovídá roku 1427 ve arabském kalendáři. Časový rozsah podporovaný filtrem nástroje Service Trace Viewer však nepodporuje datum starší než 1752. To může znamenat, že ve filtru nemůžete vybrat správné datum. Chcete-li tento problém vyřešit, můžete vytvořit vlastní filtr (**zobrazení a vlastní filtry**) pomocí výrazu XPath pro zahrnutí konkrétního časového rozsahu.

## <a name="see-also"></a>Viz také

- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Konfigurace trasování](./diagnostics/tracing/configuring-tracing.md)
- [Komplexní trasování](./diagnostics/tracing/end-to-end-tracing.md)
