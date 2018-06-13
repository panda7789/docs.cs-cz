---
title: Prohlížeč trasování služeb (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 215e34a3e7b075463ceeaa15386d3a347ffff064
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809014"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Prohlížeč trasování služeb (SvcTraceViewer.exe)
Nástroj Prohlížeč trasování služby Windows Communication Foundation (WCF) umožňuje analyzovat diagnostické trasování, které jsou generovány nástrojem WCF. Prohlížeče trasování služeb poskytuje způsob, jak snadno sloučení, zobrazení a filtrovat zprávy trasování v protokolu, aby mohli diagnostikovat, opravit a ověřte problémů služby WCF.  
  
## <a name="configuring-tracing"></a>Konfigurace trasování  
 Diagnostické trasování poskytují informace o tom, co se děje v průběhu operace vaší aplikace. Jak již název napovídá, můžete provést operace z jejich zdroje do cíle a prostřednictvím zprostředkující body také.  
  
 Trasování pomocí konfiguračního souboru aplikace můžete nakonfigurovat – buď soubor Web.config pro Web webové aplikace, nebo *Appname*.config vlastním hostováním aplikací. Následuje příklad:  
  
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
  
 V tomto příkladu je zadaný název a typ naslouchací proces trasování. Naslouchací proces jmenuje `sdt` a standardní naslouchání trasování rozhraní .NET Framework (System.Diagnostics.XmlWriterTraceListener) je přidán jako typ. `initializeData` Atribut slouží k nastavení názvu souboru protokolu pro tento naslouchací proces být `SdrConfigExample.e2e`. Pro soubor protokolu můžete nahradit plně kvalifikovanou cestu pro název jednoduchého souboru.  
  
 Tento příklad vytvoří soubor v kořenovém adresáři názvem SdrConfigExample.e2e. Při použití prohlížeče trasování k otevření souboru, jak je popsáno v části "Otevírání a zobrazení WCF trasovací soubory", zobrazí se všechny zprávy, které byly odeslány.  
  
 Úroveň trasování řídí `switchValue` nastavení. Úrovní trasování k dispozici jsou popsané v následující tabulce.  
  
|Úroveň trasování|Popis|  
|-----------------|-----------------|  
|Kritická|-Zaznamená záznamy Fast selže a v protokolu událostí a informace o trasování korelace. Toto jsou některé příklady, kdy můžete použít kritická úroveň:<br />-Služba AppDomain bylo ukončeno z důvodu neošetřené výjimky.<br />– Aplikace se nespustí.<br />-Zpráva, která způsobila selhání pochází z procesu MyApp.exe.|  
|Chyba|-Zaznamená všechny výjimky. Můžete použít úroveň chyb v těchto situacích:<br />-Kódu došlo k chybě z důvodu neplatné výjimky pro přetypování.<br />-A "Nepodařilo se vytvořit koncový bod" výjimka způsobuje selhání při spuštění aplikace.|  
|Upozornění|-Existuje podmínku, která může následně výsledkem chyba nebo kritické chybě. Můžete použít tuto úroveň v následujících situacích:<br />-Aplikace přijímá více požadavků, než umožní její nastavení omezení.<br />-Přijímající fronta je v 98 procent jeho konfigurovanou kapacitu.|  
|Informace o|-Zprávy užitečné pro monitorování a diagnostice stav systému, měření výkonu nebo profilace jsou generovány. Můžete využít tyto informace pro správu výkon a plánování kapacity. Můžete použít tuto úroveň v následujících situacích:<br />-Došlo k chybě po zpráva dosaženo domény aplikace a byla deserializovat.<br />-A došlo k chybě při vytváření vazby HTTP.|  
|Verbose|Ladění úroveň trasování pro obě uživatelského kódu a údržbu. Nastavte tato úroveň když:<br />-Si nejste jisti, jakou metodu ve vašem kódu byla volána, když došlo k selhání.<br />-Máte nesprávný koncovým bodem nakonfigurovaným a službě se nepodařilo spustit, protože položka v úložišti rezervace je uzamčena.|  
|ActivityTracing|Události toku mezi aktivitami zpracování a součásti.<br /><br /> Tato úroveň umožňuje správci a vývojáři ke korelaci aplikací ve stejné doméně aplikace.<br /><br /> -Trasování pro aktivity hranice: spuštění a zastavení.<br />-Trasování pro přenosy.|  
  
 Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V konfiguraci příklad je naslouchací proces s názvem `sdt` a standardní naslouchací proces trasování rozhraní .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) je přidán jako typ. Použití `initializeData` nastavit název souboru protokolu pro tento naslouchací proces. Kromě toho můžete nahradit plně kvalifikovanou cestu pro název jednoduchého souboru.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Pomocí nástroje prohlížeče trasování služby  
  
### <a name="opening-and-viewing-wcf-trace-files"></a>Otevření a zobrazení souborů trasování WCF  
 Prohlížeče trasování služeb podporuje tři typy souborů:  
  
-   Soubor (.svcLog) trasování WCF  
  
-   Události trasování souboru (ETL)  
  
-   Soubor karmínově trasování  
  
 Prohlížeče trasování služeb můžete otevřít všechny podporované trasovací soubor, přidejte a integrovat další trasovací soubory, nebo otevřete a současně sloučení skupinu trasovací soubory.  
  
##### <a name="to-open-a-trace-file"></a>Otevřete soubor trasování  
  
1.  Spuštění prohlížeče trasování služeb pomocí okno příkazového řádku přejděte do umístění instalace WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) a pak zadejte `SvcTraceViewer.exe`.  
  
> [!NOTE]
>  Nástroj prohlížeče trasování služeb můžete přidružit dva typy souborů: .svclog a .stvproj. Dva parametry na příkazovém řádku slouží k registraci a zrušit přípony souborů.  
>   
>  Register: zaregistrovat přidružení souboru rozšíření ".svclog" a ".stvproj" SvcTraceViewer.exe  
>   
>  / unregister: zrušit registraci přidružení SvcTraceViewer.exe souboru rozšíření ".svclog" a ".stvproj"  
  
1.  Při spuštění prohlížeče trasování služeb, klikněte na tlačítko **soubor** a pak přejděte na **otevřete**. Přejděte do umístění, kde jsou uloženy trasovací soubory.  
  
2.  Poklikejte na soubor trasování, který chcete otevřít.  
  
    > [!NOTE]
    >  Stiskněte klávesu SHIFT a kliknete na několik souborů trasování vyberte a otevřete je současně. Prohlížeče trasování služeb sloučí obsah všech souborů a uvede jedno zobrazení. Například můžete otevřít trasovací soubory klienta a služby. To je užitečné, pokud jste povolili protokolování a aktivity šíření zpráv v konfiguraci. Tímto způsobem můžete zkontrolovat výměnu zpráv mezi klientem a službou. Můžete také přetáhněte více souborů do prohlížeč, nebo použít **projektu** kartě. Najdete v části Správa projekt další podrobnosti.  
  
3.  Chcete-li přidat další trasovací soubory do kolekce, která je otevřený, klikněte na tlačítko **soubor** a pak přejděte na **přidat**. V okně, které se otevře přejděte do umístění souborů trasování a poklikejte na soubor, který chcete přidat.  
  
> [!CAUTION]
>  Nedoporučuje se načíst soubor protokolu trasování, která je větší než 200 MB. Pokud se pokusíte načíst soubor o velikosti větší než tento limit, proces načítání může trvat dlouhou dobu, v závislosti na vaší prostředků počítače. Nástroj prohlížeče trasování služeb pravděpodobně přizpůsobivý po dlouhou dobu, nebo ho může spotřebovávat paměť váš počítač. Doporučujeme nakonfigurovat částečné načítání vyhnete se tomu tak. Další informace o tom, jak to udělat, najdete v tématu "Načtení trasování velké soubory".  
  
#### <a name="event-tracing-and-crimson-tracing"></a>Trasování událostí a karmínově trasování  
 V prohlížeči nativní formát je formát trasování aktivity, který vysílá WCF. Trasování vygenerované v jiném formátu musí být převeden, než je v prohlížeči zobrazí. V současné době kromě formátu trasování aktivity, prohlížeč podporuje trasování událostí a karmínově trasování.  
  
 Otevřete soubor, který neobsahuje trasování aktivity, pokusí se v prohlížeči převeďte soubor. Musíte zadat název a umístění souboru, který bude obsahovat data převedený trasování. Po převedení dat v prohlížeči zobrazí obsah nový soubor.  
  
> [!NOTE]
>  Převod bude vyžadovat místa na disku pro uložení dat převedený trasování. Ujistěte se, že máte k dispozici pro uložení dat, před zahájením převodu z dostatek místa na disku. Převod, jinak selže.  
  
### <a name="managing-projects"></a>Správa projektů  
 Prohlížeč podporuje projekty usnadňuje zobrazení více trasovací soubory. Například pokud máte klienta trasovací soubor a soubor trasování služby, můžete je přidat do projektu. Potom při každém otevření projektu všechny trasovací soubory v projektu se načítají současně.  
  
 Existují dva způsoby, jak spravovat projekty:  
  
-   V **souboru** nabídky, můžete otevřít, uložte a zavřete projekty.  
  
-   V **projektu** kartě, můžete přidat soubory do projektu.  
  
### <a name="viewing-wcf-traces"></a>Zobrazení trasování WCF  
 WCF vysílá trasování pomocí formátu trasování aktivity. V modelu trasování aktivity jednotlivých trasování jsou seskupené v aktivity podle jejich účel. Tok řízení logické přenášena mezi aktivitami. Během životního cyklu aplikace, například mnoho "aktivity odeslat zprávu" zobrazí a zmizí. Další informace o zobrazení trasování a aktivity a uživatelského rozhraní prohlížeče trasování služeb příliš najdete v tématu [pomocí prohlížeče trasování služeb pro zobrazení korelační trasování a Poradce při potížích s](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
#### <a name="switching-to-different-views"></a>Přepnutí na jiný zobrazení  
 Prohlížeče trasování služeb poskytuje následující různá zobrazení. Se zobrazí jako karty v levém podokně prohlížeče a také být přístup z **zobrazení** nabídky.  
  
-   Zobrazení aktivity  
  
-   Zobrazení projektu  
  
-   Zobrazení zpráv  
  
-   Zobrazení grafu  
  
##### <a name="activity-view"></a>Zobrazení aktivity  
 Po otevření souborů trasování, uvidíte trasování seskupeny do aktivity a v zobrazí **aktivity** zobrazení v levém podokně.  
  
 **Aktivity** zobrazení zobrazí aktivity názvy, počet trasování v aktivitě, doba trvání spuštění a koncový čas.  
  
 Kliknutím na některé z uvedených činností, zobrazí se v podokně trasování na pravé straně trasování v této aktivity. Pak můžete vybrat trasování zobrazíte její podrobnosti.  
  
 Můžete vybrat více aktivit stisknutím **Ctrl** nebo **Shift** klíč a kliknutím na požadovanou aktivity. V podokně trasování se zobrazí všechny trasování vybrané aktivity.  
  
 Poklepáním na aktivitu zobrazte jej v **grafu** zobrazení. Alternativní způsob je vyberte aktivitu a přepněte do **grafu** zobrazení.  
  
> [!NOTE]
>  Aktivita "000000000000" je speciální aktivitě, se nezobrazí v zobrazení grafu. Protože jsou na sebe napojenou všechny ostatní aktivity, zobrazení tato aktivita má vliv ovlivňuje výkon.  
  
 Kliknutím na záhlaví sloupce seřadíte seznam aktivit. Aktivity, které obsahují trasování upozornění mít pozadí žluté a ty, které obsahují trasování chyb mít červenou jeden.  
  
 Existují různé typy aktivit a že každý typ odpovídá ikony na levé straně každé aktivity. Najdete v části Principy trasování ikony pro jejich význam.  
  
##### <a name="project-view"></a>Zobrazení projektu  
 Toto zobrazení můžete spravovat trasovací soubory v aktuálním projektu. Najdete v části Správa projekt další podrobnosti.  
  
##### <a name="graph-view"></a>Zobrazení grafu  
 Jedním z nejúčinnějších funkce prohlížeče trasování služeb je **grafu** zobrazení, která zobrazuje data trasování pro danou aktivitu v podobě grafu. Graf formuláře vám umožní zobrazit stupňový spouštění událostí a vzájemné vztahy mezi více aktivit při přesunu dat mezi nimi.  
  
 Přejděte na **grafu** zobrazit, vyberte aktivitu v **aktivity** zobrazení a klikněte na tlačítko **aktivity** kartě nebo v protokolu trasování zpráv **zpráva**Zobrazení. Pokud jsou načteny více trasovacích souborů a aktivitu zahrnuje trasování z více než jeden soubor, všechny relevantní trasování se zobrazí v zobrazení grafu. Poklikáním na aktivity a zprávy protokolu trasování také povede k **grafu** zobrazení.  
  
 V **grafu** zobrazení, každý svislé sloupec představuje aktivitu a každý blok ve sloupci představuje trasování. Aktivity jsou seskupené podle procesu (nebo vlákno). Malé šipky mezi aktivitami představují přenosů. Big šipky mezi procesy představují výměny zpráv. Aktivity v výběr je vždy žlutě.  
  
###### <a name="selecting-traces-in-the-graph"></a>Výběr trasování v grafu  
  
1.  Klikněte na tlačítko blok v grafu.  
  
2.  Pomocí nahoru a dolů klíče a vyberte jeho sousedních trasování.  
  
3.  Sledujte informace trasování v trasování podokně a podokně podrobností.  
  
###### <a name="expanding-or-collapsing-activity-transfers"></a>Rozbalení a sbalení přenosy aktivity  
 Aktivita přenosy můžete rozbalit, pokud aktivity v výběr přenese na jinou aktivitu. Umožňuje podle přenosů.  
  
 Chcete-li rozbalit nebo sbalit přenosy aktivity  
  
1.  Na levé straně na ikonu přenos vyhledejte trasování přenos znakem "+".  
  
2.  Klikněte "+", nebo stiskněte klávesu **Ctrl** a "+" pomocí klávesnice.  
  
3.  V tomto grafu se zobrazí na další aktivitu.  
  
4.  A "-" se zobrazí vlevo na ikonu přenosu. Klikněte na tlačítko "-" přihlášení nebo stiskněte klávesu Ctrl a "-", sbalí přenos aktivity.  
  
> [!NOTE]
>  Když aktivita má více přenosy do ní a jeden přenosů rozbalíte, zobrazí se aktivity, které vést do nové aktivity z kořenové aktivity. Tyto nové aktivity jsou zobrazeny ve sbaleném formátu. Pokud chcete zobrazit podrobnosti o tyto aktivity, rozbalte svisle kliknutím na ikonu rozbalení v hlavičce grafu.  
  
###### <a name="expanding-or-collapsing-activities-vertically"></a>Rozbalení a sbalení aktivity svisle  
 V prohlížeči skryje nepotřebné podrobností v grafu aktivity sbalením aktivity. Ve sbalených aktivitě nejsou zobrazeny jednotlivé trasování. Zobrazí se jenom přenosy trasování. Pokud chcete zobrazit všechny trasování v aktivitě, rozbalte aktivity ve svislém směru, kliknutím na symbol rozbalte aktivity v hlavičce grafu.  
  
 Chcete-li rozbalit nebo sbalit aktivity ve svislém směru  
  
1.  Klikněte na ikonu "+" v hlavičce aktivity rozbalte aktivity svisle.  
  
2.  Všimněte si, že v grafu se zobrazují všechny trasování.  
  
3.  Klikněte "-" ikona v hlavičce aktivity na Sbalit aktivity svisle.  
  
4.  Všimněte si, že zprávy jenom důležité přenosy, zaprotokoluje upozornění a trasování výjimky jsou uvedeny v aktivitě.  
  
###### <a name="options"></a>Možnosti  
 Můžete vybrat dvě možnosti z **možnost** nabídky v zobrazení grafu.  
  
-   Zobrazit hranice trasování aktivity, který v případě nezaškrtnutí ignorovat hranic trasování aktivity v grafu.  
  
-   Zobrazit podrobné trasování Non zpráva, která v případě nezaškrtnutí ignorovat podrobné úrovni trasování, s výjimkou trasování zpráv. Ve většině případů podrobné úrovně trasování jsou méně důležité pro analýzu. Tato možnost je užitečné, pokud nechcete k analýze podrobné úrovni trasování a pouze se chcete zaměřit na důležitější trasování.  
  
###### <a name="layout-mode"></a>Režim rozložení  
 Prohlížeč obsahuje dva režimy rozložení: **proces** a **vláken**. Toto nastavení určuje největší jednotka organizace. Výchozí režim rozložení je **proces**, což znamená, že aktivity jsou seskupené podle procesy v grafu.  
  
###### <a name="execution-list"></a>Provádění seznamu  
 Můžete vybrat, který proces nebo podproces, který se má zobrazit v grafu z tohoto rozevíracího seznamu. Například pokud máte trasovací soubory dvou klientů (A a B) a jedna služba otevřít a můžete pouze chcete zobrazit v grafu služby a klienta A, můžete zrušit zaškrtnutí klienta B ze seznamu.  
  
#### <a name="viewing-trace-details"></a>Zobrazení podrobností trasování  
 Chcete-li zobrazit podrobnosti o trasování, vyberte v podokně trasování trasování. Podrobnosti jsou zobrazeny v podokně podrobností.  
  
##### <a name="trace-pane"></a>Podokno trasování  
 Horním pravém podokně v prohlížeči trasování služby je v podokně trasování. Zobrazí seznam všech trasování v vybranou aktivitou s doplňující informace, například úroveň trasování, vlákno ID a název procesu.  
  
 Nezpracovaná XML trasování můžete zkopírovat do schránky trasování kliknete pravým tlačítkem a výběrem **trasování kopírování do schránky**.  
  
##### <a name="detail-pane"></a>Podokno Podrobnosti.  
 Dolní levé podokno v prohlížeči trasování služby je v podokně podrobností. Nabízí tři karty zobrazíte podrobnosti trasování.  
  
 **Naformátovaný** zobrazení zobrazí informace více uspořádány způsobem. Zobrazí seznam všech známých elementů XML v tabulkách a stromy, usnadnit ke čtení a pochopení informace.  
  
 **XML** zobrazení zobrazí XML odpovídající vybraného trasování. Podporuje barva zvýraznění a syntaxe. Při použití **najít** Pokud chcete hledat řetězce, zvýrazní výsledky hledání.  
  
 **Zpráva** zobrazení zobrazí část zprávy XML v protokolu trasování zpráv. Neviditelná je při výběru trasování bez zpráv.  
  
### <a name="filtering-wcf-traces"></a>Filtrování trasování WCF  
 Pro usnadnění analýzu trasování můžete filtrovat následujícími způsoby:  
  
-   Filtr nástrojů poskytuje přístup k předdefinované a vlastní filtry. Může být povoleno prostřednictvím **zobrazení** nabídky.  
  
-   Předem definovaný filtr prohlížeče umožňuje selektivně filtrování částí trasování WCF. Ve výchozím nastavení je nastavená na všech trasování infrastruktury předávat. Nastavení tohoto filtru, jsou definovány v **možnosti filtrování** dílčí nabídky v části **zobrazení** nabídky.  
  
-   Vlastní filtry XPath uživatelům plnou kontrolu nad filtrování. Lze definovat v **vlastní filtr** pod **zobrazení** nabídky.  
  
 Zobrazí se pouze trasování, které projdou všechny filtry.  
  
#### <a name="using-the-filter-toolbar"></a>Pomocí filtru panelu nástrojů  
 Filtr nástrojů se zobrazí v horní části tohoto nástroje. Pokud není přítomen, můžete si aktivovat ho **zobrazení** nabídky. Na panelu má tři komponenty:  
  
-   Vyhledejte: **vyhledejte** definuje subjektu, jak hledat v operace filtru. Například pokud chcete najít všechny trasování, které byly vygenerované v rámci procesu X, nastavte toto pole na X a **vyhledávání v** pole na "Název procesu". Toto pole změny do ovládacího prvku pro výběr data a času při filtru na základě času je vybrán.  
  
-   Hledání v: Toto pole definuje typ filtr.  
  
-   Úroveň: Nastavení úrovně definuje minimální úroveň trasování povoleno filtr. Například pokud úroveň je nastavená na chybu nebo vyšší, jsou zobrazeny pouze trasování na úrovni kritické a chyby. Tento filtr kombinuje kritérii zadanými Hledat a hledání v.  
  
 **Filtru nyní** tlačítko spustí operace filtru. Některé filtry, zejména v případě, že jsou nastavení použita na velké datové sady, trvat dlouhou dobu pro dokončení. Operace filtru můžete zrušit stisknutím **Zastavit** tlačítko, které se zobrazí ve stavovém řádku pod **Operations** nabídky.  
  
 **Zrušte** tlačítko resetuje předdefinované a vlastní filtry umožňující všech trasování předávat.  
  
#### <a name="filter-options"></a>Možnosti filtru.  
 V prohlížeči můžete automaticky odebrat trasování WCF ze zobrazení. Můžete selektivně odebrat trasování vysílaných určité oblasti služby WCF, například odebrání transakce související trasování ze zobrazení.  
  
 Nastavení tohoto filtru, jsou definovány v **možnosti filtrování** dílčí nabídky v části **zobrazení** nabídky.  
  
#### <a name="custom-filters"></a>Vlastní filtry  
 Pokud jste obeznámeni s XML Path Language (XPath), můžete vytvořit vlastní filtry pro vyhledávání dat trasování pro libovolný element XML, které vás zajímají. Filtry jsou přístupné prostřednictvím nástrojů filtru.  
  
 Vlastní filtry může obsahovat parametry. Můžete také importovat existující vlastní filtry.  
  
##### <a name="creating-a-custom-filter"></a>Vytvoření vlastního filtru  
 Filtry lze vytvořit dvěma způsoby:  
  
###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Vytváření vlastní filtr pomocí Průvodce šablonou  
 Můžete kliknutím na stávající trasování a vytvořit filtr na základě struktury trasování. Tento příklad vytvoří vlastní filtr na základě ID vlákna.  
  
1.  V podokně trasování v horní pravé oblasti prohlížeče vyberte trasování, který obsahuje element, který chcete filtrovat.  
  
2.  Klikněte **vytvořit vlastní filtr** tlačítko nachází v horní části podokna trasování.  
  
3.  V dialogovém okně, které se zobrazí zadejte název filtru. V tomto příkladu zadejte `Thread ID`. Můžete zadat také popis filtru.  
  
4.  Zobrazení stromu vlevo zobrazuje strukturu záznam trasování, který jste vybrali v kroku 1. Přejděte na element, který chcete vytvořit podmínky. V tomto příkladu, vyhledejte ID podprocesu umístěný v jazyka XPath: /E2ETraceEvent/System/Execution/@ThreadID uzlu. Dvakrát klikněte na atribut ID podprocesu ve stromovém zobrazení. Tím se vytvoří výrazu pro atribut na pravé straně dialogového okna.  
  
5.  Změňte parametr pole pro podmínku ID podprocesu od nulové '{0}'. Tento krok povoluje hodnota ID podprocesu, která má nakonfigurované, když se filtr použije. (Viz postup použít filtr část) Můžete definovat až čtyři parametry. Podmínky jsou kombinované pomocí operátoru OR.  
  
6.  Klikněte na tlačítko **Ok** k vytvoření filtru rozhraní.  
  
> [!NOTE]
>  Po vytvoření filtru pomocí Průvodce šablonou, ho můžete upravit pouze ručně. Není možné aktivovat Průvodce pro filtr, který byl vytvořen dříve. Kromě toho podmínky filtr XPath, který je vytvořen v Průvodci vytvořením šablony jsou kombinované pomocí operátoru OR. Pokud budete potřebovat a operace, můžete upravit výraz filtru po jeho vytvoření.  
  
###### <a name="creating-a-custom-filter-manually"></a>Ruční vytvoření vlastního filtru  
 V nabídce vlastní filtry umožňuje zadat filtry XPath ručně.  
  
1.  V nabídce zobrazení, klikněte na **vlastní filtry** položku nabídky.  
  
2.  V dialogovém okně se zobrazí, klikněte na tlačítko **nový.**  
  
3.  Minimálně zadejte název filtru a XPath výraz.  
  
4.  Click **OK**.  
  
###### <a name="applying-a-custom-filter"></a>Použití vlastního filtru  
 Po vytvoření vlastního filtru, když bude přístupný panelu nástrojů filtru. Vyberte filtr, kterou chcete použít v **vyhledávání v** pole panelu nástrojů filtru. Předchozí příklad vyberte Thread ID.  
  
1.  Zadejte hodnotu, kterou hledáte v **najít** pole. V našem příkladu zadejte ID podprocesu, kterou chcete vyhledat.  
  
2.  Klikněte na tlačítko **filtru nyní**a sledovat výsledek operace.  
  
 Pokud filtr používá několik parametrů, zadejte je pomocí ';' jako oddělovač v **najít** pole. Například následující řetězec definuje 3 parametrů: '1; findValue; text'. V prohlížeči se vztahuje na '1' {0} parametr filtru. jsou použity 'findValue' a 'text' {1} a {2} v uvedeném pořadí.  
  
###### <a name="sharing-custom-filters"></a>Sdílení vlastní filtry  
 Vlastní filtry lze sdílet mezi různé relace a jiné uživatele. Můžete exportovat do souboru definice filtry a importování tohoto souboru v jiném umístění.  
  
 Import vlastního filtru:  
  
1.  V **zobrazení** nabídky, klikněte na tlačítko **vlastní filtry**.  
  
2.  V dialogovém okně, které se otevře, klikněte **Import** tlačítko.  
  
3.  Přejděte k souboru vlastního filtru (.stvcf), klikněte na soubor a klikněte **otevřete** tlačítko.  
  
 Export vlastního filtru:  
  
1.  V nabídce zobrazení, klikněte na tlačítko **vlastní filtry**.  
  
2.  V dialogovém okně, které se otevře vyberte filtr, který chcete exportovat.  
  
3.  Klikněte **exportovat** tlačítko.  
  
4.  Zadejte název a umístění souboru definice vlastního filtru (.stvcf) a klikněte na **Uložit** tlačítko.  
  
> [!NOTE]
>  Tyto vlastní filtry lze pouze importovat a exportovat z prohlížeče trasování služeb. Nemůže být číst jiných nástrojů.  
  
### <a name="finding-data"></a>Vyhledávání dat  
 Prohlížeč nabízí tyto způsoby hledání dat:  
  
-   Panel nástrojů najít umožňuje rychlý přístup k nejběžnější možnosti najít.  
  
-   Dialogové okno hledání poskytuje možnosti pro že další možnosti hledání. Je přístupný prostřednictvím **upravit** nabídky, nebo krátké klíč Ctrl + F.  
  
 Najít nástrojů se zobrazí v horní části v prohlížeči. Pokud není přítomen, můžete si aktivovat ho **zobrazení** nabídky. Na panelu má dvě součásti:  
  
-   Najít: Umožňuje Zadejte hledaná klíčová slova.  
  
-   Podívejte se v: Umožňuje zadejte obor vyhledávání. Můžete vybrat, jestli se má hledat ve všech aktivit nebo v rámci aktuální aktivity.  
  
 Dialogové okno hledání poskytuje další dvě možnosti:  
  
-   Nalezen element target:  
  
    -   Možnost "nezpracovaných dat protokolu" vyhledá klíčové slovo v všechny nezpracovaná data.  
  
    -   Možnosti "XML Text" a "XML atribut" vyhledávat pouze v elementů XML.  
  
    -   Možnost "Protokolovat zprávu" vyhledá klíčové slovo pouze ve zprávách.  
  
-   Ignorovat kořenové aktivity: vyhledávání ignoruje trasování v "000000000000" aktivity. To zvyšuje výkon v velké trasovací soubory, když má aktivita kořenové tisíce trasování, většina z nich přenosů.  
  
### <a name="navigating-traces"></a>Navigace trasování  
 Protože trasování se zaznamenávají krok za krokem během doba spuštění aplikace, můžete k ladění aplikace navigace trasování. Prohlížeče trasování služeb poskytuje různé způsoby, jak se orientovat v trasování.  
  
#### <a name="step-forward-or-backward"></a>Krok nebo předchozí  
 Pokud uvažujete o každé trasování jako řádek kódu v programu, předat dál krokování je velmi podobné "Krok přes" v prostředí Visual Studio integrované vývoj prostředí (IDE). Rozdíl je, že je můžete taky krok zpátky v trasování. Krokování s dál znamená přechod na další trasování v aktivitě.  
  
-   Předat dál krok: Použití **aktivity** nabídky, nebo klikněte na tlačítko "F10". V podokně trasování můžete také pomocí klávesy ŠIPKA "dolů".  
  
-   Zpětně krok: Pomocí **aktivity** nabídky, nebo klikněte na tlačítko "F9". Můžete také pomocí klávesy ŠIPKA "nahoru" v podokně trasování.  
  
> [!NOTE]
>  To může trvat můžete aktivitu, ke kterým došlo v jiném procesu nebo i na jiném počítači, protože WCF zprávy mohou přenášet aktivity ID, které jsou rozmístěny počítače.  
  
#### <a name="follow-transfer"></a>Postupujte podle přenosu  
 Přenos trasování jsou speciální trasování v trasovacím souboru. Aktivita může pro jinou aktivitu přenáší přenos trasování. Například "Aktivita A", mohou předávat "Aktivity b". V takovém případě není na ikonu "Aktivity A" s název "Na aktivitu:" a přenos přenos trasování. Tento přenos trasování je propojení mezi dvěma trasování. V "Aktivity B" mohou existovat i přenos trasování na konci aktivity převést zpět do "Aktivity A". Toto je podobná volání funkce v programech: A volá B, pak vrátí B.  
  
 "Následovat přenos" je podobná "Krokování s vnořením" ladicí program. Následuje přenos z A B. Nemá žádný vliv na ostatní trasování.  
  
 Postupujte podle přenos dvěma způsoby: pomocí myši nebo pomocí klávesnice:  
  
-   Pomocí myši: Dvakrát klikněte na přenos trasování v podokně trasování.  
  
-   Pomocí klávesnice: Vyberte přenos trasování a použijte "Přenos postupujte podle" v **aktivity** nabídky, nebo klikněte na tlačítko "F11"  
  
> [!NOTE]
>  V mnoha případech při přenosech aktivity A do B aktivity, aktivity A čeká na aktivitě B přenosy zpět na aktivitu A. To znamená, že aktivity A nemá žádné trasování zaznamenána během doby, kdy je aktivita B aktivně trasování. Také je však možné, že aktivity A nečeká a pokračuje v protokolu trasování. Je také možné, že aktivity B nepřenese zpět na aktivitu A. Proto aktivity přenosy jsou stále liší od volání funkce v této smysl. Rozumíte aktivity přenosy lepší v zobrazení grafu.  
  
#### <a name="jump-to-next-or-previous-transfer"></a>Přejít na další nebo předchozí přenosu  
 Při analýze aktuální aktivity nebo vybraných aktivit když je vybraných více aktivit, můžete rychle najít činnosti, které se přenáší do. "Přechod na další transfer" můžete najít další trasování přenosu v aktivitě. Jakmile zjistíte, přenos trasování, můžete použít "Následovat přenos" krok do další aktivity.  
  
-   Přejít na další přenosu: použití **aktivity** nabídky, nebo klikněte na tlačítko "Ctrl + F10".  
  
-   Přejít na předchozí přenosu: použití **aktivity** nabídky, nebo klikněte na tlačítko "Ctrl + F9".  
  
#### <a name="navigate-in-graph-view"></a>Přejděte v zobrazení grafu  
 I když přejdete podokna aktivit a trasování je podobná ladění, pomocí **grafu** zobrazení poskytuje mnohem lepší podmínky v navigačním panelu. Další informace jsou uvedeny v části "Zobrazení grafu".  
  
### <a name="loading-large-trace-files"></a>Načítání velkých trasovací soubory  
 Trasovací soubory mohou být značně velké. Například pokud zapnout trasování na úrovni "Podrobné", bude výsledný soubor trasování pro spuštění pár minut můžete snadno být stovky megabytů nebo i větší, v závislosti na rychlosti a komunikace vzor sítě.  
  
 Když velké trasovací soubor otevřete v prohlížeči trasování služby, může negativně ovlivněn výkon systému. Rychlost načítání a doby odezvy po načtení může být pomalé. Skutečná rychlost se liší od času v závislosti na konfiguraci hardwaru. Ve většině počítačů načítání větší než 200M trasovací soubor má vliv ovlivňuje výkon. Pro trasování soubory větší než 1G může nástroj spotřebovávat veškerou dostupnou paměť, nebo přestane reagovat velmi dlouhou dobu.  
  
 Aby se zamezilo pomalé načítání a dobu odezvy v Analýza velkých trasovací soubory, prohlížeče trasování služeb obsahuje funkci "Částečné načítání", který načte pouze malou část toho trasování najednou. Například můžete mít více než 1GB na serveru spuštěna po několik dní trasovací soubor. Když máte došlo k chybám a chcete analyzovat trasování, není potřeba otevřít celý trasovacího souboru. Místo toho můžete načtení trasování v určitém časovém intervalu čas, kdy může došlo k chybě. Protože obor je menší, nástroj prohlížeče trasování služeb můžete načíst soubor rychleji a můžete identifikovat pomocí menší sady dat chyby.  
  
#### <a name="enabling-partial-loading"></a>Povolení částečné načítání  
 Není nutné ručně povolit částečné načítání. Pokud celková velikost souborů trasování, které pokus o načtení překročí 40 MB, prohlížeče trasování služeb automaticky zobrazí dialogové okno částečné načítání výběr součástí, který chcete načíst.  
  
> [!NOTE]
>  Protože trasování nemusí rovnoměrně v čase span, délka, které zadáte v částečné načítání nástrojů nemusí být přímo úměrná velikosti načítání zobrazené časové období. Načítání skutečná velikost může být menší než velikost odhadované v dialogovém okně částečné načítání.  
  
#### <a name="adjusting-partial-loading"></a>Úprava částečné načítání  
 Po částečně načtení trasování souboru můžete změnit sadu dat, který je právě načítán. Můžete tak učinit úpravou částečné načítání panelu nástrojů v horní části v prohlížeči.  
  
1.  Panelu nástrojů přesouvat pomocí myši nebo zadat počáteční a koncový čas.  
  
2.  Klikněte **upravit** tlačítko.  
  
## <a name="understanding-trace-icons"></a>Principy trasování ikony  
 Tady je seznam ikon, které používá nástroj prohlížeče trasování služeb v **aktivity** zobrazení, **grafu** zobrazení a **trasování** podokně představují různé položky.  
  
> [!NOTE]
>  Některé trasování, které nejsou rozdělené (například "zprávu je uzavřený") mají žádné ikonu.  
  
### <a name="activity-tracing-traces"></a>Aktivita trasování pro trasování  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Upozornění trasování](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Trasování upozornění: trasování, které jsou vydávány na úrovni upozornění|  
|![Chyba trasování](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Chyba trasování: trasování, které jsou vydávány na úrovni chyby.|  
|![Trasování spuštění aktivit:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Trasování spuštění aktivit: trasování, který označuje začátek aktivitu. Obsahuje název aktivity. Jako návrháře aplikací nebo vývojáře byste měli definovat jednu aktivitu spustit trasování podle id aktivity podle procesu nebo přístup z více vláken.<br /><br /> Pokud je id aktivity rozšíří napříč zdrojů trasování pro trasování korelace, můžete se podívat, více spuštění stejné id aktivity (jeden na každý zdroj trasování). Spuštění trasování jsou vydávány, pokud je pro zdroj trasování povoleno ActivityTracing.|  
|![Trasování aktivit zastavení](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Zastavit trasování aktivit: trasování, který označuje konec aktivity. . Obsahuje název aktivity. Jako návrháře aplikací nebo vývojáře byste měli definovat jednu aktivitu Zastavit trasování podle id aktivity na zdroj trasování. Po zastavení vysílaných tento zdroj trasování, s výjimkou Pokud členitost času trasování není dostatečně malé aktivity zobrazit žádné trasování z daného trasování zdroje. Pokud k tomu dojde, může být dvou trasování s stejnou dobu, včetně zastavení, prokládaný. při zobrazení. Pokud je id aktivity rozšíří napříč zdrojů trasování pro trasování korelace, uvidíte více zastaví pro stejné id aktivity (jeden na každý zdroj trasování). Zastavit trasování jsou vydávány, pokud je ActivityTracing zdroj trasování.|  
|![Aktivita Suspend trasování](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Aktivita Suspend trasování: trasování, který označuje čas aktivitu je pozastavena. Žádné trasování jsou vygenerované v pozastavenou aktivity, dokud obnoví aktivity. Aktivitu pozastavenou označuje, že žádné zpracování se děje v aktivity v rámci oboru zdroj trasování. Pozastavení nebo obnovení činnosti trasování jsou užitečné pro vytváření profilů. Pozastavit trasování jsou vydávány, pokud je ActivityTracing zdroj trasování.|  
|![Aktivita obnovit trasování](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|Aktivita obnovit trasování: trasování, který označuje čas aktivitu je obnoven po bylo pozastaveno. Trasování může znovu vygenerované v aktivity. Pozastavení nebo obnovení činnosti trasování jsou užitečné pro vytváření profilů. Obnovit trasování jsou vydávány, pokud je ActivityTracing zdroj trasování.|  
|![Transfer](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Přenos: Trasování, který je vygenerované při převodu logické řízení toku z jedné aktivity do jiného. Aktivitu, kterou přenos pochází z může pokračovat v práci paralelní aktivity, které přenos přejde na. Přenos trasování jsou vydávány, pokud je ActivityTracing zdroj trasování.|  
|![Přenos z](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Přenos z: Trasování, která definuje přenos z jiné aktivity do aktuální aktivita.|  
|![Transfer To](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Přenos do: Trasování, která definuje přenos logické řízení toku z aktuální aktivita pro jinou aktivitu.|  
  
### <a name="wcf-traces"></a>Trasování WCF  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Zprávy protokolu trasování](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Zprávy protokolu trasování: trasování, který je vygenerované při zaznamenání zprávu WCF funkcí protokolování zpráv, když `System.ServiceModel.MessageLogging` zdroj trasování je povoleno. Kliknutím na toto trasování zobrazí zprávu. Existují čtyři body konfigurovat protokolování pro zprávu: ServiceLevelSendRequest, TransportSend, TransportReceive a ServiceLevelReceiveRequest, které lze zadat také pomocí `messageSource` atribut v protokolu trasování zpráv.|  
|![Zprávy přijaté trasování](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Zprávy přijaté trasování: trasování, který je vygenerované při příjmu zprávy WCF, pokud `System.ServiceModel` zdroj trasování je povoleno na úrovni informace nebo Verbose. Trasování je nezbytné pro zobrazení na šipku korelace zprávu v aktivitě **grafu** zobrazení.|  
|![Zprávy odeslané trasování](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Zprávy odeslané trasování: trasování, které jsou vydávány, když je odeslána zpráva WCF, pokud `System.ServiceModel` zdroj trasování je povoleno na úrovni informace nebo Verbose. Trasování je nezbytné pro zobrazení na šipku korelace zprávu v aktivitě **grafu** zobrazení.|  
  
### <a name="activities"></a>Aktivity  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Aktivita](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Aktivita: Označuje, že je aktuální aktivita obecné aktivity.|  
|![Kořenová aktivita](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Kořenová aktivita: označuje kořenové aktivity procesu.|  
  
### <a name="wcf-activities"></a>Aktivity WCF  
  
|Ikona|Popis|  
|----------|-----------------|  
|![Aktivita prostředí](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Aktivita prostředí: aktivitu, která vytvoří, otevře nebo zavře WCF hostitele nebo klienta. Chybách, ke kterým došlo během těchto fází se zobrazí v této aktivitě.|  
|![Naslouchání aktivity](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Naslouchání aktivity: aktivitu, která protokoly trasování související s naslouchací proces. Uvnitř této aktivity jsme můžete zobrazit žádosti o připojení a informace o naslouchací proces.|  
|![Přijímat bajtů aktivity](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Přijímat aktivity bajtů: aktivitu, které jsou seskupeny všechny trasování týkající se přijímání bajtů na připojení mezi dva koncové body. Tato aktivita je nezbytné v korelace s přenosu aktivity, které rozšíří jejich id aktivity, jako jsou ovladače http.sys. Chyby připojení, jako je například přerušení se zobrazí v této aktivitě.|  
|![Zpracování zpráv aktivity](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Aktivitu zprávu zpracovat: aktivitu, která skupiny trasování související s vytvářením zpráv WCF. V této aktivitě se zobrazí chyby z důvodu chybné obálky nebo chybnou zprávu. Uvnitř této aktivity jsme můžete prohlédnout hlavičky zpráv, které chcete zobrazit, pokud k ní id aktivity se rozšíří volající. Pokud je to pravda, pokud jsme přenést do procesu akce aktivity (další ikona), jsme můžete také přiřadit pro danou aktivitu šířený aktivity id korelace mezi volající a volaného trasování.|  
|![Zprávy protokolu trasování](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Zpracovat aktivity akce: aktivitu, které jsou seskupeny všechny trasování související s žádost WCF mezi dva koncové body. Pokud `propagateActivity` je nastaven na `true` u obou koncových bodů v konfiguraci všech trasování z obou koncové body jsou sloučeny do jedné aktivity pro přímé korelace. Tyto aktivity se obsahuje chyby kvůli přenos nebo zabezpečení zpracování, rozšíření na hranici kód uživatele a zpět (pokud existuje odpověď).|  
|![Zpracování zpráv aktivity](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Spuštění uživatelského kódu aktivity: trasování aktivitu, která skupiny uživatelský kód pro zpracování požadavku.|  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Pokud nemáte oprávnění k zápisu do registru, zobrazí se následující chybová zpráva "Microsoft Service prohlížeče trasování nebyl zaregistrován v systému" při použití "`svctraceviewer /register`" příkaz pro registraci nástroj. V takovém případě by měl přihlásit pomocí účtu, který má oprávnění k zápisu do registru.  
  
 Kromě toho nástroj prohlížeče trasování služeb zapíše některá nastavení (například vlastní filtry a možnosti filtrování) k souboru SvcTraceViewer.exe.settings v jeho sestavení. Pokud nemáte oprávnění ke čtení pro soubor, stále můžete spustit nástroj, ale nelze načíst nastavení.  
  
 Pokud se zobrazí chybová zpráva "došlo k neznámé chybě při zpracování jednoho nebo více trasování" při otevírání souboru ETL, znamená, že formát soubor .etl je neplatný.  
  
 Pokud otevřete protokolu trasování vytvořený Arabic operačního systému, můžete si všimnout, době filtru nefunguje. Například roce 2005 odpovídá roce 1427 v Arabic kalendáři. Časové rozmezí filtr nástroj prohlížeče trasování služeb podporuje však nepodporuje starší než 1752 datum. To můžete neznamená, že zatím nejste moct vybrat správné datum ve filtru. Chcete-li vyřešit tento problém, můžete vytvořit vlastní filtr (**zobrazení nebo vlastní filtry**) pomocí výrazu jazyka XPath mají být zahrnuty za určité časové období.  
  
## <a name="see-also"></a>Viz také  
 [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Konfigurace trasování](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Trasování aktivit a šíření pro trasování začátku do konce korelace](http://msdn.microsoft.com/library/2c11a905-64f8-47b5-bae5-a74fc666137e)
