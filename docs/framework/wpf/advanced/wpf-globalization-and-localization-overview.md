---
title: Přehled globalizace a lokalizace WPF
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 54c5caaf3ade07f342e94ad0359f00c1418eace4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368598"
---
# <a name="wpf-globalization-and-localization-overview"></a>Přehled globalizace a lokalizace WPF
Pokud váš produkt dostupnost pouze jeden jazyk, omezíte vašeho potenciálního zákazníka základní zlomek naplnění 6.5 miliard náš svět. Pokud chcete, aby vaše aplikace pro oslovení publika, nákladově efektivní lokalizaci skrytých váš produkt je jedním ze způsobů nejlepší a nejhospodárnějším oslovovat víc zákazníků.  
  
 Tento přehled zavádí globalizace a lokalizace v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Globalizace je návrh a vývoj aplikací, které provádějí v několika umístěních. Například globalizace podporuje lokalizovaná uživatelská rozhraní a regionální data pro uživatele v různé jazykové verze. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje funkce pro globalizovaná návrh, včetně automatické rozložení, satelitních sestavení a lokalizované atributy a komentáře.
  
 Lokalizace je převod prostředků aplikace do lokalizované verze pro specifické jazykové verze, které aplikace podporuje. Když lokalizujete ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], používají rozhraní API v <xref:System.Windows.Markup.Localizer> oboru názvů. Tato rozhraní API power [ukázkový locbaml – nástroj](https://go.microsoft.com/fwlink/?LinkID=160016) nástroj příkazového řádku. Informace o tom, jak vytvářet a používat locbaml – najdete v tématu [lokalizace aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Osvědčené postupy pro globalizaci a lokalizaci v subsystému WPF  
 Můžete provést z globalizace a lokalizace funkce, která je integrována do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podle návrhu uživatelského rozhraní a související lokalizace tipy, které v této části najdete.  
  
### <a name="best-practices-for-wpf-ui-design"></a>Osvědčené postupy pro návrh uživatelského rozhraní WPF  
 Při návrhu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zvažte implementaci těchto osvědčených postupů:  
  
-   Zápis vaše [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; Vyhněte se vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v kódu. Při vytváření vašeho [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ji zpřístupnit prostřednictvím vestavěné lokalizace rozhraní API.  
  
-   Vyhněte se použití absolutní umístění a pevné velikosti pro rozložení obsahu; Místo toho použijte relativní nebo automatické nastavení velikosti.
  
    -   Použití <xref:System.Windows.Window.SizeToContent%2A>; a zachování šířky a výšky nastavena na `Auto`.  
  
    -   Vyhněte se použití <xref:System.Windows.Controls.Canvas> rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.  
  
    -   Použití <xref:System.Windows.Controls.Grid> a jeho sdílení velikost funkce.  
  
-   Protože lokalizovaný text často vyžaduje více místa, zadejte místo navíc je v rozpětí. Umožňuje místo navíc je možné overhanging znaky.  
  
-   Povolit <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> na <xref:System.Windows.Controls.TextBlock> aby nedošlo k oříznutí.
  
-   Nastavte **XML: lang** atribut. Tento atribut popisuje jazykovou verzi konkrétní elementu a jeho podřízené prvky. Hodnota této vlastnosti změní chování několik funkcí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Například změní chování dělení slov, kontrolu pravopisu, číslo nahrazení, složitým tvarování a zpětné volání. Zobrazit [globalizace pro WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md) pro další informace o nastavení [XML: lang v XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md).  
  
-   Vytvořte přizpůsobené složený font získat lepší kontrolu nad písma, které se používají pro různé jazyky. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá písmo GlobalUserInterface.composite ve vašem adresáři Windows\Fonts.  
  
-   Při vytváření navigačních aplikací, které může být lokalizována jazykové verze, který představuje text ve formátu zprava doleva, explicitně nastavit <xref:System.Windows.FlowDirection> z každé stránky, na stránce nedědí <xref:System.Windows.FlowDirection> z <xref:System.Windows.Navigation.NavigationWindow>.  
  
-   Když vytvoříte samostatný navigační aplikace, které jsou hostované mimo prohlížeč, nastavte <xref:System.Windows.Application.StartupUri%2A> počáteční aplikace <xref:System.Windows.Navigation.NavigationWindow> místo na stránku (například `<Application StartupUri="NavigationWindow.xaml">`). Tento návrh umožňuje změnit <xref:System.Windows.FlowDirection> okně a na navigačním panelu. Další informace a příklad najdete v tématu [globalizace Domovská stránka ukázkové](https://go.microsoft.com/fwlink/?LinkID=159990).  
  
### <a name="best-practices-for-wpf-localization"></a>Osvědčené postupy pro lokalizaci WPF  
 Když lokalizujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace, zvažte implementaci těchto osvědčených postupů:  
  
-   Lokalizace komentáře použijte k zajištění další kontext Lokalizátoři.  
  
-   Použití atributů lokalizace řídit lokalizace místo selektivně vynechání <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti prvků. Zobrazit [atributy a komentáře lokalizace](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md) Další informace.  
  
-   Použití **msbuild /t:updateuid** a **/t:checkuid** přidat a zkontrolujte <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti v vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Použití <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti, které sledují změny mezi vývojem a lokalizaci. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> Vlastnosti vám usnadní lokalizaci nové změnami vývoje. Pokud chcete ručně přidat <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti, které chcete [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], úloha je obvykle únavné a méně přesné.  
  
    -   Upravit nebo změnit <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti po zahájení lokalizace.  
  
    -   Nepoužívejte duplicitní <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti (Nezapomeňte tento tip při použití příkazu kopírování a vkládání).  
  
    -   Nastavte `UltimateResourceFallback` umístění v AssemblyInfo.* k určení odpovídající jazyk pro použití náhradní lokality (například `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).  
  
         Pokud se rozhodnete zahrnout Zdrojový jazyk v hlavním sestavení vynecháním `<UICulture>` značky v souboru projektu, nastavte `UltimateResourceFallback` umístění jako hlavní sestavení namísto satelitní (například `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>Lokalizace aplikace WPF  
 Když lokalizujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, máte několik možností. Například můžete vytvořit vazbu lokalizovatelné prostředky v aplikaci [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru, uložit Lokalizovatelný text v tabulkách resx, nebo mít vaše lokalizátora použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory. Tato část popisuje lokalizace pracovního postupu, který používá formuláře BAML z XAML, který poskytuje několik výhod:  
  
-   Je možné lokalizovat po sestavení.  
  
-   Můžete aktualizovat na novější verzi formuláře BAML XAMLwith lokalizace ze starší verze formuláře BAML z XAML tak, že je možné lokalizovat ve stejnou dobu, které vyvíjíte.  
  
-   Můžete ověřit původní zdrojové elementy a sémantika v době kompilace vzhledem k tomu, že je formulář BAML z XAML kompilovaný formy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
### <a name="localization-build-process"></a>Lokalizace procesu sestavení  
 Při vývoji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, proces sestavení pro lokalizaci vypadá takto:  
  
-   Vývojář vytvoří a globalizuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. V projektu soubor sady pro vývojáře `<UICulture>en-US</UICulture>` tak, že když bude uložena zkompilovaná aplikace, je generována do hlavního sestavení jazykově neutrální. Toto sestavení obsahuje satelit. resources.dll soubor, který obsahuje všechny lokalizovatelné prostředky. Volitelně můžete zachovat Zdrojový jazyk v hlavním sestavení protože naše lokalizace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] podporují extrakce z hlavní sestavení.  
  
-   Když je soubor zkompilovaný do sestavení, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je převedena na formuláři BAML z XAML. Jazykově neutrální `MyDialog.exe` a jazykově závislé (v angličtině) `MyDialog.resources.dll` soubory jsou k dispozici pro anglicky mluvící zákazníka.  
  
### <a name="localization-workflow"></a>Lokalizace pracovního postupu  
 Proces lokalizace začne za nelokalizované `MyDialog.resources.dll` sestavení souboru. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Prvků a vlastností v váš původním [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se extrahují z formuláře BAML z XAML na páry klíč hodnota s použitím [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] pod <xref:System.Windows.Markup.Localizer>. Lokalizátoři lokalizovat aplikaci pomocí páry klíč hodnota. Vygenerovat nový. resource.dll z nové hodnoty po dokončení lokalizace.  
  
 Klíče dvojice klíč hodnota jsou `x:Uid` hodnoty, které jsou umístěny vývojář v původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tyto `x:Uid` povolit hodnoty [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] ke sledování a sloučení změn, ke kterým dochází mezi vývojáři a lokalizátora při lokalizaci. Například, pokud vývojář změní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] po zahájení lokalizátora lokalizace tak, aby práce minimální překlad dojde ke ztrátě můžete sloučit změny vývoj s již dokončené lokalizační práce.  
  
 Následující obrázek ukazuje typické lokalizace pracovního postupu, který je založen na formuláři BAML z XAML. Tento diagram předpokládá, že vývojář aplikace zapíše v angličtině. Vývojář vytvoří a globalizuje aplikaci WPF. V projektu soubor sady pro vývojáře `<UICulture>en-US</UICulture>` tak, aby při sestavování, získá jazyk neutrální hlavní sestavení generována s satelit. resources.dll obsahující všechny lokalizovatelné prostředky. Alternativně jeden může zachovat Zdrojový jazyk v hlavním sestavení, protože lokalizace WPF rozhraní API podporují extrakce z hlavní sestavení. Po dokončení procesu sestavení XAML získat zkompilován BAML. Jazykově neutrální MyDialog.exe.resources.dll získat dodat anglické mluvy zákazníkovi.  
  
 ![Pracovní postup lokalizace](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![Nelokalizované pracovní postup](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>Příklady lokalizace WPF  
 Tato část obsahuje příklady lokalizované aplikace, které vám pomohou pochopit, jak sestavit a lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.  
  
#### <a name="run-dialog-box-example"></a>Spuštění příkladu pole dialogového okna  
 Následující obrázky znázorňují výstup **spustit** ukázka pole dialogového okna.  
  
 **Angličtina:**  
  
 ![Dialogové okno Spustit](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **Němčina:**  
  
 ![Dialogové okno spustit Němčina](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **Navrhování globální dialogového okna spustit**  
  
 Tento příklad vytvoří **spustit** dialogové okno s použitím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Je ekvivalentní tomuto dialogovému oknu **spustit** dialogové okno, které je k dispozici [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] nabídky Start.  
  
 Mezi nejdůležitější funkce pro provádění globální dialogová okna jsou:  
  
 **Automatické rozložení**  
  
 *V Window1.xaml:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 Předchozí okno Vlastnosti automaticky přizpůsobí svou velikost podle velikosti obsahu okna. Tato vlastnost zabraňuje okně odříznutí obsah, který zvyšuje velikost po lokalizace; zároveň se tím odebere nepotřebné místa při obsah zmenšena, po lokalizace.  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti jsou potřebné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fungovat správně.  
  
 Jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ke sledování změn mezi vývojem a lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti umožňují sloučení novější verze [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] s starší lokalizace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Přidáte <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnost spuštěním **msbuild /t:updateuid RunDialog.csproj** v příkazovém řádku. Toto je doporučený způsob přidávání <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti vzhledem k tomu, že je ručně přidáte je obvykle zdlouhavá a méně přesné. Můžete zkontrolovat, který <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> spuštěním jsou správně nastaveny vlastnosti **msbuild /t:checkuid RunDialog.csproj**.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Strukturovaná pomocí <xref:System.Windows.Controls.Grid> ovládací prvek, který je užitečných ovládací prvek pro využití výhod automatické rozložení v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Všimněte si, že dialogové okno se dělí do tři řádky a pět sloupců. Není jednou z definice řádků a sloupců má pevnou velikost; Proto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které jsou umístěny v každé buňce můžete přizpůsobit zvyšuje a snižuje velikost při lokalizaci.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 První dva sloupce kde **otevřít:** popisek a <xref:System.Windows.Controls.ComboBox> jsou umístěny 10 procent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] celková šířka.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 Všimněte si, že v příkladu používá funkci sdílí velikosti <xref:System.Windows.Controls.Grid>. Poslední tři sloupce využít to tak, že sami ve stejném <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Jako jeden byste očekávali od názvu vlastnosti, díky tomu sloupce, které chcete sdílet stejnou velikost. Proto při "Procházet..." získá lokalizovaný řetězec delší "Durchsuchen...", všechna tlačítka Zvětšit šířku nemuseli malé tlačítko "OK" a nepřiměřeně velké tlačítko "Durchsuchen...".  
  
 **Xml:lang**  
  
 `Xml:lang="en-US"`  
  
 Všimněte si, že [XML: lang v XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) objektu umístěn na kořenový element [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Tato vlastnost popisuje jazyková verze daného elementu a jeho podřízené položky. Tato hodnota se používá několik funkcí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a by měla být změněna odpovídajícím způsobem při lokalizaci. Tato hodnota se změní, jaké slovník je použít k dělení slov a slova kontrolu pravopisu. Ovlivní také zobrazení číslic a jak záložní systém písmo vybere písmo použít. A konečně vlastnost ovlivňuje, čísla způsob, jak se zobrazují a způsob, jak textu napsaného ve složitých skriptech jsou ve tvaru. Výchozí hodnota je "en US".  
  
 **Vytváření satelitní sestavení prostředků**  
  
 *V csproj:*  
  
 `<UICulture>en-US</UICulture>`  
  
 Všimněte si, že přidání `UICulture` hodnotu. Pokud je nastavené na platný <xref:System.Globalization.CultureInfo> hodnotu, třeba cs cz, sestavení projektu vygeneruje satelitní sestavení s všechny lokalizovatelné prostředky v ní.  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` Nemusí být lokalizována, protože by se měla objevit, stejný pro všechny jazykové verze. `Localizable` je nastavena na `false` tak, aby ho zůstal v neutrální hlavní sestavení jazyka místo do satelitního sestavení. Výchozí hodnota všech prostředků noncompilable je `Localizable` nastavena na `true`.  
  
 **Lokalizace spuštění dialogového okna**  
  
 **Parse**  
  
 Po vytvoření aplikace, je prvním krokem při jeho lokalizace analýza lokalizovatelné prostředky nedostatek satelitní sestavení. Pro účely tohoto tématu, použijte ukázkový locbaml – nástroj, který se nachází v [locbaml – nástroj ukázka](https://go.microsoft.com/fwlink/?LinkID=160016). Všimněte si, že je locbaml – pouze ukázkový nástroj pomůže vám začít s vytvářením lokalizační nástroj, který se vejde do procesu lokalizace. Pomocí locbaml –, spusťte následující příkaz k analýze: **locbaml – / analyzovat RunDialog.resources.dll/out:** vygenerovat soubor "RunDialog.resources.dll.CSV".  
  
 **Lokalizace**  
  
 Pomocí oblíbeného editoru sdíleného svazku clusteru, který podporuje kódování Unicode pro úpravy tohoto souboru. Vyfiltrovat všechny položky s lokalizace kategorii "None". Zobrazí se následující položky:  
  
|Klíč prostředku|Lokalizace kategorie|Hodnota|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Tlačítko|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Tlačítko|Zrušit|  
|Button_3:System.Windows.Controls.Button.$Content|Tlačítko|Projděte...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|Zadejte název programu, složce, dokumentu nebo prostředků Internetu a Windows ji otevřete.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|Otevřít:|  
|Window_1:System.Windows.Window.Title|Název|Spustit|  
  
 Lokalizace aplikace na němčinu by vyžadovaly následující převody:  
  
|Klíč prostředku|Lokalizace kategorie|Hodnota|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Tlačítko|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Tlačítko|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|Tlačítko|Durchsuchen...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|Den Geben Sie Namen eines Programms Ordners, Dokuments oder einer Internetresource.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|Öffnen:|  
|Window_1:System.Windows.Window.Title|Název|Spustit|  
  
 **Generovat**  
  
 Posledním krokem lokalizace zahrnuje vytvoření nově lokalizované satelitní sestavení. Můžete to provést pomocí následujícího příkazu locbaml –:  
  
 **LocBaml.exe /generate RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV /out: . /cul:de-DE**  
  
 V Německu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], pokud je tato resources.dll je umístěn ve složce de-DE vedle hlavní sestavení, tento prostředek se automaticky načte místo ve složce en US. Pokud nemáte německé verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] to pokud chcete otestovat, nastavit jazykovou verzi na libovolné jazykovou verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] používáte (tj en US) a nahradit původní resources.dll.  
  
 **Načítání satelitních prostředků**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|Kód|Původní anglické BAML|Lokalizované BAML|  
|Jazykově neutrální prostředky|Další prostředky v angličtině.|Další prostředky lokalizovanými pro němčinu|  
  
 Rozhraní .NET framework automaticky zvolí satelitní sestavení prostředků načíst podle aplikace `Thread.CurrentThread.CurrentUICulture`. Výchozí hodnota pro jazykovou verzi vašeho [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operačního systému. Ano, pokud používáte Němčina [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], načte de-DE\MyDialog.resources.dll, pokud používáte Angličtina [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], načte en-US\MyDialog.resources.dll. Ultimate záložní prostředky pro vaši aplikaci můžete nastavit tak, že zadáte NeutralResourcesLanguage v AssemblyInfo.* váš projekt. Pokud například zadáte:  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 potom en-US\MyDialog.resources.dll se použije Windows němčina Pokud de-DE\MyDialog.resources.dll nebo de\MyDialog.resources.dll není k dispozici.  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Domovská stránka Microsoft Saúdská Arábie  
 Na následujících obrázcích ukazují angličtinu a arabština domovské stránky. Kompletní příklad, který vytváří tyto grafiky naleznete v tématu [globalizace Domovská stránka ukázkové](https://go.microsoft.com/fwlink/?LinkID=159990).  
  
 **Angličtina:**  
  
 ![Stránka v angličtině](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **Arabština:**  
  
 ![Arabské stránky](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>Navrhování globální hlavní stránku Microsoftu.  
 To napodobovat webu ukazuje funkce globalizace stanovené RightToLeft jazyky Microsoft Saúdská Arábie. Například hebrejské a Arabské jazyky mají pořadí čtení zprava doleva tak rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musí často rozloží úplně jinak než v jazycích zleva doprava, jako je angličtina. Lokalizace z jazyka zleva doprava, zprava doleva jazyk nebo naopak může být poměrně složité. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] byla navržena tak, aby takové lokalizace značně zjednodušují.  
  
 **FlowDirection**  
  
 *Homepage.XAML:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 Všimněte si, že <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost <xref:System.Windows.Controls.Page>. Změna této vlastnosti na <xref:System.Windows.FlowDirection.RightToLeft> se změní <xref:System.Windows.FrameworkElement.FlowDirection%2A> z <xref:System.Windows.Controls.Page> a jeho podřízené prvky tak, aby rozložení tohoto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obráceně podle Arabské uživatel očekává stane zprava doleva. Chování dědičnosti jednoho můžete přepsat zadáním explicitní <xref:System.Windows.FrameworkElement.FlowDirection%2A> u libovolného elementu. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Vlastnost je k dispozici na všech <xref:System.Windows.FrameworkElement> nebo související element dokumentu a má implicitní hodnotu <xref:System.Windows.FlowDirection.LeftToRight>.  
  
 Podívejte se, že jsou i přechodu štětce pozadí obráceně správně při kořenové <xref:System.Windows.FrameworkElement.FlowDirection%2A> se změnilo:  
  
 **FlowDirection = "LeftToRight"**  
  
 ![Tok zleva doprava](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection = "RightToLeft"**  
  
 ![Tok zprava doleva](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **Vyhněte se použití pevné dimenze pro ovládací prvky a panelů**  
  
 Podívejte se prostřednictvím Homepage.xaml, Všimněte si, že kromě pevnou šířku a výšku zadaný pro celý [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nahoře <xref:System.Windows.Controls.DockPanel>, neexistují žádné pevné dimenze. Vyhněte se využívat pevné dimenze, abyste zabránili oříznutí lokalizovaný text, který může být delší než zdrojový text. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] panely a automaticky použije resize na základě obsahu, které obsahují ovládací prvky. Většina ovládací prvky také mít minimální a maximální dimenze, které můžete nastavit pro další ovládací prvek (tedy hodnota MinWidth = "20"). S <xref:System.Windows.Controls.Grid>, relativní šířky a výšky můžete také nastavit pomocí "*" (například Width = "0,25\*") nebo použijte jeho velikost buňky funkce pro sdílení obsahu.  
  
 **Komentáře lokalizace**  
  
 Jsou v mnoha případech, kdy obsahu může být nejednoznačný a jednoduché přeložit. Vývojář nebo Návrhář má schopnost poskytovat další kontext a komentáře k Lokalizátoři prostřednictvím komentáře lokalizace. Například následující Localization.Comments vysvětluje použití znaku '&#124;".  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 Tento komentář se sváže s obsahem vaší TextBlock_1 a v případě locbaml – nástroj (viz [lokalizace aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)), lze je zobrazit v 6 sloupec řádku TextBlock_1 ve výstupním souboru CSV:  
  
|Klíč prostředku|Kategorie|Čtení|Upravitelné|Komentář|Hodnota|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|HODNOTA TRUE|HODNOTA TRUE|Tento znak se používá jako dekorativní pravidlo.|&#124;|  
  
 Komentáře mohou být umístěny na obsah nebo vlastnost libovolného elementu, použijte tuto syntaxi:  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **Lokalizace atributy**  
  
 Často vývojář nebo správce lokalizace potřebujete kontrolu toho, co můžete Lokalizátoři přečíst a upravit. Například možná chcete lokalizátora přeložit název vaší společnosti nebo právní formulace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje atributy, které vám umožní nastavit čitelnost, modifiability a kategorie obsah elementu nebo vlastnost, která lokalizační nástroj slouží k uzamčení, skrýt nebo řazení elementů. Další informace naleznete v tématu <xref:System.Windows.Localization.Attributes%2A>. Pro účely tohoto příkladu locbaml – nástroj vypíše jenom hodnotami těchto atributů. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] všechny ovládací prvky mají výchozí hodnoty pro tyto atributy, ale může je přepsat. Například následující příklad přepisuje výchozí atributy lokalizace pro `TextBlock_1` a sady obsahu, aby byly čitelné ale neupravitelných pro Lokalizátoři.  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 Kromě čitelnost a atributy modifiability [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje výčet kategorií společné uživatelské rozhraní (<xref:System.Windows.LocalizationCategory>), který je možné poskytnout Lokalizátoři širší kontext. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Výchozí kategorie pro ovládací prvky platformy může být přepsána nastaveními v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] také:  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 Lokalizace výchozí atributy, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje lze také přepsat pomocí kódu, abyste mohli správně nastavit správný výchozí hodnoty pro vlastní ovládací prvky. Příklad:  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 Jednotlivé atributy instance nastavit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přednost hodnoty nastavené v kódu na vlastní ovládací prvky. Další informace o atributy a komentáře, naleznete v tématu [atributy a komentáře lokalizace](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
 **Použití náhradní lokality písma a složená písma**  
  
 Pokud zadáte písma, která nepodporuje daný bod kódu rozsah, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bude automaticky použití náhradní lokality, který provádí pomocí globální Interface.compositefont uživatele, který je umístěn v adresáři Windows\Fonts. Složená písma pracovat stejně jako jakákoli jiná písma a je možné explicitně nastavením elementu FontFamily (to znamená FontFamily = "Globální uživatelské rozhraní"). Vytváření vlastních složený font a určením co písma pro konkrétní bod kódu oblasti a jazyky můžete zadat vlastní záložní předvoleb písma.  
  
 Další informace o složená písma naleznete v tématu <xref:System.Windows.Media.FontFamily>.  
  
 **Lokalizace hlavní stránku Microsoftu.**  
  
 Můžete postupovat podle stejných kroků jako v příkladu dialogového okna Spustit lokalizace této aplikace. Je k dispozici pro vás v lokalizovaných CSV soubor pro arabštinu [globalizace Domovská stránka ukázkové](https://go.microsoft.com/fwlink/?LinkID=159990).
