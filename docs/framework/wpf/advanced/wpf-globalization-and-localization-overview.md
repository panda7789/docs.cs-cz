---
title: Přehled globalizace a lokalizace WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6f2bc9021ca376b7b27f74efed6866a907b480ad
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="wpf-globalization-and-localization-overview"></a>Přehled globalizace a lokalizace WPF
Pokud svůj produkt dostupnost pouze jeden jazyk, omezíte se zákazníkovi potenciální základní k zlomek naše world 6.5 miliardy naplnění. Pokud chcete, aby vaše aplikace k dosažení globální cílovou skupinu, nákladově efektivní lokalizace produktu je jedním z nejlepší a nejhospodárnějším možným způsobů spojit více zákazníků.  
  
 Tento přehled zavádí globalizace a lokalizace v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Globalizace je návrh a vývoj aplikací, které provést na více místech. Například globalizace podporuje lokalizované uživatelská rozhraní a místní data pro uživatele v různých jazykové verze. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje funkce globalizovaná návrhu, včetně automatického rozložení, satelitních sestavení a lokalizované atributy a komentářů.
  
 Lokalizace je překlad prostředky aplikace do lokalizované verze pro konkrétní jazykové verze, které podporuje aplikace. Při lokalizaci v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], můžete použít rozhraní API v <xref:System.Windows.Markup.Localizer> oboru názvů. Tato rozhraní API power [ukázkový nástroj LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016) nástroj příkazového řádku. Informace o tom, jak vytvářet a používat LocBaml najdete v tématu [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Osvědčené postupy pro globalizaci a lokalizaci v grafickém subsystému WPF  
 Můžete provést nejvíce z globalizace a lokalizace funkce, která je integrovaná do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podle návrhu uživatelského rozhraní a lokalizace související typy, které tato část obsahuje.  
  
### <a name="best-practices-for-wpf-ui-design"></a>Osvědčené postupy pro návrh uživatelského rozhraní grafického subsystému WPF  
 Při návrhu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zvažte tyto doporučené postupy pro implementaci:  
  
-   Zápis vaší [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; Vyhněte se vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v kódu. Při vytváření vašeho [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zveřejnění prostřednictvím předdefinované lokalizace rozhraní API.  
  
-   Nepoužívejte absolutní umístění a pevné velikosti pro rozložení obsahu; Místo toho použijte relativní nebo automatické nastavení velikosti.
  
    -   Použití <xref:System.Windows.Window.SizeToContent%2A>; a udržovat šířky a výšky nastavena na `Auto`.  
  
    -   Nepoužívejte <xref:System.Windows.Controls.Canvas> k rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.  
  
    -   Použití <xref:System.Windows.Controls.Grid> a její velikost sdílení funkce.  
  
-   Protože textu často vyžaduje další prostor, zadejte místo navíc v okraje. Místo navíc umožňuje možné overhanging znaků.  
  
-   Povolit <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> na <xref:System.Windows.Controls.TextBlock> aby nedošlo k oříznutí.
  
-   Nastavte **XML: lang** atribut. Tento atribut popisuje jazykovou verzi konkrétní elementu a jeho podřízené elementy. Hodnota této vlastnosti se změní chování několik funkcí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Například změní chování dělení slov, kontrolu pravopisu, číslo nahrazení, tvarování komplexní skriptu a použití náhradního písma. V tématu [globalizace pro grafický subsystém WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md) Další informace o nastavení [XML: lang v jazyce XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md).  
  
-   Vytvoření vlastní složeného písma získat lepší kontrolu nad písma, která se používají pro různé jazyky. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá GlobalUserInterface.composite písma ve vašem adresáři Windows\Fonts.  
  
-   Při vytváření navigační aplikace, které mohou být lokalizována v jazykové verzi, uvede text ve formátu zprava doleva, explicitně nastavit <xref:System.Windows.FlowDirection> každé stránky, aby stránce nedědí <xref:System.Windows.FlowDirection> z <xref:System.Windows.Navigation.NavigationWindow>.  
  
-   Když vytvoříte samostatné navigační aplikacím, které se hostují mimo prohlížeče, nastavte <xref:System.Windows.Application.StartupUri%2A> pro aplikace počáteční <xref:System.Windows.Navigation.NavigationWindow> místo na stránku (například `<Application StartupUri="NavigationWindow.xaml">`). Tento návrh umožňuje změnit <xref:System.Windows.FlowDirection> okna a navigačním panelu. Další informace a příklady naleznete v tématu [globalizace domovské stránky ukázka](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
### <a name="best-practices-for-wpf-localization"></a>Osvědčené postupy pro lokalizaci WPF  
 Při lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace, zvažte implementaci tyto doporučené postupy pro:  
  
-   Lokalizace komentáře použijte k zajištění další kontext překladatelům při lokalizaci.  
  
-   Lokalizace atributy použít k řízení lokalizace místo selektivně vynechání <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti prvků. V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md) Další informace.  
  
-   Použití **msbuild /t:updateuid** a **/t:checkuid** chcete přidat a zaškrtněte <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti v vaší [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Použití <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti, které chcete sledovat změny mezi vývojovým týmem a lokalizaci. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti můžete lokalizovat nové změny vývoj. Pokud ručně přidáte <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastností [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], tato úloha je obvykle zdlouhavé a méně přesný.  
  
    -   Upravit nebo změnit <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti až zahájíte lokalizace.  
  
    -   Nepoužívejte duplicitní <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti (Nezapomeňte tento tip při použití příkazu kopírování a vložení).  
  
    -   Nastavte `UltimateResourceFallback` umístění v AssemblyInfo.* zadat příslušný jazyk pro použití náhradní (například `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).  
  
         Pokud se rozhodnete zahrnout hlavní sestavení jazyka zdroje Díky vynechání `<UICulture>` značky v souboru projektu, nastavte `UltimateResourceFallback` umístění jako hlavní sestavení místo satelit (například `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>Lokalizace aplikace WPF  
 Při lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, máte několik možností. Například můžete vázat lokalizovatelný prostředky v aplikaci na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru, uložit Lokalizovatelný text v tabulkách resx, nebo mají vaše lokalizátora použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory. Tato část popisuje lokalizace pracovní postup, který používá BAML formu XAML, který poskytuje několik výhod:  
  
-   Je možné lokalizovat po sestavení.  
  
-   Můžete aktualizovat na novější verzi BAML formu XAMLwith lokalizace ze starší verze formuláře BAML XAML tak, aby v době, kdy budete vyvíjet je možné lokalizovat.  
  
-   Můžete ověřit původní zdrojové elementy a sémantiku v době kompilace protože BAML formu XAML je kompilované formu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
### <a name="localization-build-process"></a>Lokalizace procesu sestavení  
 Když budete vyvíjet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, procesu sestavení pro lokalizaci vypadá takto:  
  
-   Vývojář se vytvoří a globalizuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. V projektu soubor sady developer `<UICulture>en-US</UICulture>` tak, aby při kompiluje aplikace, se vygeneruje hlavní sestavení jazykově neutrální. Toto sestavení obsahuje satelit. resources.dll soubor, který obsahuje všechny lokalizovatelný prostředky. Volitelně můžete ponechat zdrojové jazyk v hlavní sestavení protože naše lokalizace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] podporu extrakci z hlavní sestavení.  
  
-   Při kompilaci souboru do sestavení, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je převeden do formuláře BAML XAML. Jazykově neutrální `MyDialog.exe` a jazykově závislé (angličtina) `MyDialog.resources.dll` soubory jsou k dispozici na hovořícího anglicky zákazníka.  
  
### <a name="localization-workflow"></a>Lokalizace pracovního postupu  
 Zahájí proces lokalizace po nelokalizované `MyDialog.resources.dll` soubor. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Prvky a vlastnosti v původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se extrahují z formuláře BAML XAML do páry klíč hodnota s použitím [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] pod <xref:System.Windows.Markup.Localizer>. Lokalizace aplikace pomocí překladatelům při lokalizaci páry klíč hodnota. Můžete vygenerovat nový. resource.dll z nové hodnoty po dokončení lokalizace.  
  
 U klíčů páry klíč hodnota se `x:Uid` hodnoty, které jsou umístěny vývojáře v původním [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tyto `x:Uid` povolit hodnoty [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] ke sledování a slučování změn, které vývojář až lokalizátora dojít během lokalizace. Například pokud se změní Vývojář [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] až lokalizátora začne, lokalizace, tak, aby pracovní minimální překlad dojde ke ztrátě můžete sloučit změny vývoj s lokalizace už dokončené práce.  
  
 Následující obrázek ukazuje typické lokalizace pracovní postup, který je založený na formuláři BAML XAML. Tento diagram předpokládá, že vývojář zapíše aplikace v angličtině. Vývojář se vytvoří a globalizuje aplikaci WPF. V projektu soubor sady developer `<UICulture>en-US</UICulture>` tak, aby na sestavení, získá jazyk neutrální hlavní sestavení vygeneroval s satelit. resources.dll obsahující všechny lokalizovatelný prostředky. Vzhledem k tomu WPF lokalizace rozhraní API podporují extrakci z hlavní sestavení Alternativně může zachovat jazyka zdroje v hlavní sestavení jeden. Po dokončení procesu sestavení získat XAML zkompilovat do BAML. Jazykově neutrální MyDialog.exe.resources.dll získat odeslané anglické hovořícího zákazníkům.  
  
 ![Pracovní postup lokalizace](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![Nelokalizované pracovní postup](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>Příklady lokalizace WPF  
 Tato část obsahuje příklady lokalizované aplikací, které vám pomohou pochopit, jak sestavit a lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
#### <a name="run-dialog-box-example"></a>Spustit dialogové okno pole příklad  
 Na následujících obrázcích zobrazit výstup **spustit** dialogové okno pole ukázka.  
  
 **Angličtina:**  
  
 ![Dialogové okno Spustit](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **Němčina:**  
  
 ![Dialogové okno spustit Němčina](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **Navrhování globální dialogového okna spustit**  
  
 Tento příklad vytvoří **spustit** dialogové okno s použitím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Toto dialogové okno je ekvivalentní **spustit** dialogu, který má k dispozici [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] nabídky Start.  
  
 Některé označuje pro provedení globální dialogová okna jsou:  
  
 **Automatické rozložení**  
  
 *V Window1.xaml:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 Předchozí okno Vlastnosti automaticky zmenší okno na základě velikosti obsahu. Tato vlastnost zabraňuje okno z vyjímání vypnout obsah, který zvětšuje velikost po lokalizace; Když obsah snižuje velikost po lokalizace nepotřebné místa, odebere se také.  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti jsou potřebné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fungovala správně.  
  
 Používají se v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] sledování změn mezi vývoj a lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti umožňují sloučení na novější verzi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] s starší lokalizace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Přidání <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnost spuštěním **msbuild /t:updateuid RunDialog.csproj** v příkazovém řádku. Toto je doporučená metoda přidávání <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti vzhledem k tomu, že je ručně přidáte je obvykle zdlouhavá a méně přesný. Můžete zkontrolovat, který <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti jsou správně nastaveny tak, že spustíte **msbuild /t:checkuid RunDialog.csproj**.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Strukturovaná pomocí <xref:System.Windows.Controls.Grid> prvek, který je užitečný ovládací prvek pro využívat výhod automatického rozložení v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Všimněte si, že dialogové okno je rozdělit na tři řádky a sloupce pět. Není jednou z definice řádků a sloupců má pevnou velikost; Proto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které jsou umístěny v každé buňce můžete přizpůsobit zvyšovat a snižuje velikost během lokalizace.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 První dva sloupce kde **otevřete:** popisek a <xref:System.Windows.Controls.ComboBox> jsou umístěny použít 10 procent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] celková šířka.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 Všimněte si, že v příkladu používá funkci sdílené sizing <xref:System.Windows.Controls.Grid>. Poslední tři sloupce využít výhod to tak, že sami stejné <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Jako jeden by uživatel očekával od názvu vlastnosti, to umožňuje sloupce, které chcete sdílet stejnou velikost. Takže pokud "Procházet..." Získá lokalizovaný delší řetězec "Durchsuchen..." všechna tlačítka Zvětšit šířku místo nutnosti malé tlačítko "OK" a nepřiměřeně vysokých "Durchsuchen..." tlačítko.  
  
 **Xml:lang**  
  
 `Xml:lang="en-US"`  
  
 Upozornění [XML: lang v jazyce XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) umístěn na kořenový prvek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Tato vlastnost popisuje jazykovou verzi daného elementu a jeho podřízených položek. Tato hodnota se používá několik funkce v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a by mělo být změněno správně při lokalizaci. Tato hodnota se změní, jaké slovník jazyk je použít k dělení slov a slova kontrola pravopisu. Ovlivní také zobrazení číslic a jak záložní systém písmo vybere písmo pro použít. Nakonec vlastnost ovlivňuje, čísla způsob, jak se zobrazují a způsob texty napsané v komplexní skriptů jsou ve tvaru. Výchozí hodnota je "en US".  
  
 **Vytváření satelitních sestavení prostředků**  
  
 *V .csproj:*  
  
 `<UICulture>en-US</UICulture>`  
  
 Všimněte si, přidání `UICulture` hodnotu. Pokud je nastavena platná <xref:System.Globalization.CultureInfo> hodnotu, třeba cs cz, sestavení projektu způsobí vygenerování satelitní sestavení s lokalizovatelný všechny prostředky v ní.  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` Nemusí být lokalizovaný, protože by se měla objevit, stejný pro všechny jazykové verze. `Localizable` je nastavena na `false` , aby zůstala v neutrální hlavní sestavení jazyka místo satelitní sestavení. Výchozí hodnota všech prostředků, noncompilable je `Localizable` nastavena na `true`.  
  
 **Lokalizace spustit dialogové okno**  
  
 **analyzovat**  
  
 Po vytvoření aplikace, je prvním krokem v jeho lokalizace analýzy lokalizovatelný prostředky mimo satelitní sestavení Pro účely tohoto tématu, použít LocBaml ukázkový nástroj, který najdete na [ukázkový nástroj LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016). Všimněte si, že je LocBaml pouze ukázkový nástroj, čeho chcete vám pomůže začít s vytvářením lokalizace nástroj, který nejlépe odpovídá do procesu lokalizace. Pomocí LocBaml, spusťte následující příkaz k analýze: **LocBaml/analyzovat RunDialog.resources.dll/out:** generovat soubor "RunDialog.resources.dll.CSV".  
  
 **Lokalizace**  
  
 Použijte svém oblíbeném editoru CSV, který podporuje kódování Unicode k úpravám tohoto souboru. Filtrovat všechny záznamy s lokalizace kategorie "Žádný". Měli byste vidět následující položky:  
  
|Klíč prostředku|Lokalizace kategorie|Hodnota|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Tlačítko|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Tlačítko|Zrušit|  
|Button_3:System.Windows.Controls.Button.$Content|Tlačítko|Procházet...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|Zadejte název programu, složky, dokumentu nebo internetových prostředků a systém Windows ho otevřít.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|Otevřete:|  
|Window_1:System.Windows.Window.Title|Název|Spustit|  
  
 Lokalizace aplikací němčina by vyžadovaly překlady následující:  
  
|Klíč prostředku|Lokalizace kategorie|Hodnota|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Tlačítko|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Tlačítko|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|Tlačítko|Durchsuchen…|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|Den Geben Sie Namen eines Programms, Ordners, Dokuments oder einer Internetresource.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|Öffnen:|  
|Window_1:System.Windows.Window.Title|Název|Spustit|  
  
 **Generovat**  
  
 Poslední krok lokalizace zahrnuje vytvoření nově lokalizované satelitní sestavení. Můžete to provést pomocí následujícího příkazu LocBaml:  
  
 **LocBaml.exe /generate RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV /out: . /cul:de-DE**  
  
 Na Němčina [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], pokud je tato resources.dll je umístěn ve složce de-DE vedle hlavní sestavení, tento prostředek automaticky načte místo v složce en US. Pokud nemáte německé verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] abyste to mohli otestovat, nastavit jazykovou verzi na jakémkoli jazykové verze [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] používáte (tj. en US) a nahradit původní resources.dll.  
  
 **Načítání prostředků satelit**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|Kód|Původní anglické BAML|Lokalizované BAML|  
|Jazykově neutrální prostředky|Další prostředky v angličtině|Další prostředky lokalizované němčina|  
  
 Rozhraní .NET framework automaticky zvolí takovou které satelitní sestavení prostředky načíst podle aplikace `Thread.CurrentThread.CurrentUICulture`. Tato výchozí jazykovou verzi vaší [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operačního systému. Pokud používáte Němčina [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], de-DE\MyDialog.resources.dll načte, pokud používáte Angličtina [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], en-US\MyDialog.resources.dll načte. Zadáním NeutralResourcesLanguage v projektu na AssemblyInfo.* můžete nastavit ultimate záložní prostředků pro vaši aplikaci. Pokud například zadáte:  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 en-US\MyDialog.resources.dll se pak použije s německé verzi systému Windows, pokud de-DE\MyDialog.resources.dll nebo de\MyDialog.resources.dll není k dispozici.  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Domovská stránka Microsoft Saúdská Arábie  
 Na následujících obrázcích zobrazit angličtinu a arabské domovské stránky. Kompletní příklad, který vytváří tyto grafiky najdete v části [globalizace domovské stránky ukázka](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
 **Angličtina:**  
  
 ![Stránka v angličtině](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **Arabština:**  
  
 ![Arabic stránky](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>Navrhování globální Domovská stránka Microsoft  
 Tento model se webu znázorňuje globalizace funkcí pro jazyky RightToLeft Microsoft Saúdská Arábie. Jazyků, například hebrejština a arabština mít pořadí čtení zprava doleva tak rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musí být nastíněny často poměrně odlišně, než by bylo v jazycích zleva doprava, jako je angličtina. Lokalizace z jazyk zleva doprava na jazyk zprava doleva a naopak může být velmi náročné. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má byly navržené tak, aby takové lokalizace mnohem jednodušší.  
  
 **FlowDirection**  
  
 *Homepage.xaml:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 Upozornění <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost <xref:System.Windows.Controls.Page>. Změna této vlastnosti <xref:System.Windows.FlowDirection.RightToLeft> se změní <xref:System.Windows.FrameworkElement.FlowDirection%2A> z <xref:System.Windows.Controls.Page> a její podřízené elementy, aby rozložení tohoto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je obráceně stane zprava doleva, jako byste očekávali Arabic uživatele. Chování dědičnosti jeden můžete přepsat zadáním explicitního <xref:System.Windows.FrameworkElement.FlowDirection%2A> u libovolného elementu. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Vlastnost je k dispozici na všech <xref:System.Windows.FrameworkElement> nebo dokumentu související elementu a implicitní hodnotu <xref:System.Windows.FlowDirection.LeftToRight>.  
  
 Zkontrolujte, zda jsou i přechodu štětce pozadí obráceně správně při kořenu <xref:System.Windows.FrameworkElement.FlowDirection%2A> mění:  
  
 **FlowDirection="LeftToRight"**  
  
 ![Tok zleva doprava](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection="RightToLeft"**  
  
 ![Tok zprava doleva](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **Vyhněte se použití pevné dimenze pro panely a ovládací prvky**  
  
 Podívejte se prostřednictvím Homepage.xaml, Všimněte si, že kromě zajištění dostatečného pevnou šířku a výšku zadané pro celý [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nahoře <xref:System.Windows.Controls.DockPanel>, neexistují žádné pevné dimenze. Nepoužívejte pevné dimenze aby výstřižek lokalizované text, který může být delší než zdrojový text. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] panely a bude automaticky změny velikosti podle obsahu, které obsahují ovládací prvky. Většina ovládacích prvků také má minimální a maximální dimenzí, které se dají nastavit pro další ovládací prvek (tj. hodnota MinWidth = "20"). S <xref:System.Windows.Controls.Grid>, relativní šířky a výšky lze také nastavit pomocí ' *' (tj Width = "0,25\*") nebo použijte jeho velikost buňky sdílení funkce.  
  
 **Lokalizace komentáře**  
  
 Existují mnoho případy, kdy obsah může být nejednoznačný a jednoduché přeložit. Vývojář nebo Návrhář má schopnost poskytnout další kontext a komentáře k překladatelům při lokalizaci prostřednictvím lokalizace komentáře. Například následující Localization.Comments vysvětluje použití znaku '&#124;'.  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 Tento komentář se sváže s obsahem na TextBlock_1 a v případě nástroj LocBaml (najdete v části [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)), ho můžete zobrazit ve sloupci 6. TextBlock_1 řádku souboru CSV:  
  
|Klíč prostředku|Kategorie|Čtení|Upravitelnými|Komentář|Hodnota|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|HODNOTA TRUE|HODNOTA TRUE|Tento znak se používá jako dekorativní pravidlo.|&#124;|  
  
 Komentáře mohou být umístěny na obsah nebo vlastnost libovolný element, pomocí následující syntaxe:  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **Lokalizace atributy**  
  
 Často vývojáře nebo správce lokalizace vyžaduje kontrolu nad co můžete překladatelům při lokalizaci číst a upravovat. Například možné, že chcete lokalizátora přeložit název vaší společnosti nebo právní slov. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje atributy, které vám umožní nastavit čitelnost, modifiability a kategorie obsah elementu nebo vlastnost, která vaše lokalizace nástroje slouží k uzamčení, skrytí nebo řazení elementů. Další informace naleznete v tématu <xref:System.Windows.Localization.Attributes%2A>. Pro účely tohoto příkladu výstupy nástroj LocBaml pouze hodnoty těchto atributů. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] všechny ovládací prvky mají výchozí hodnoty pro tyto atributy, ale je může nepřepíšete. Například v následujícím příkladu přepíše výchozí atributy lokalizace pro `TextBlock_1` a nastaví obsah pro čtení ale unmodifiable pro překladatelům při lokalizaci.  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 Kromě čitelnost a atributy modifiability [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje výčet kategorií běžné uživatelského rozhraní (<xref:System.Windows.LocalizationCategory>), lze poskytnout další kontext překladatelům při lokalizaci. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Výchozí kategorie pro ovládací prvky platformy může být přepsána nastaveními v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] také:  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 Lokalizace výchozí atributy, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje je také možné přepsat prostřednictvím kódu, abyste mohli správně nastavit správné výchozí hodnoty pro vlastní ovládací prvky. Příklad:  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 Jednotlivé instance atributů nastavena [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bude mít přednost před s hodnotami nastavenými v kódu na vlastní ovládací prvky. Další informace o atributy a komentářů naleznete v tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
 **Záložní písma a složená písma**  
  
 Pokud zadáte písma, která nepodporuje daný codepoint rozsah, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bude automaticky záložní na takový, který nemá pomocí globální Interface.compositefont uživatele, který je umístěný v adresáři Windows\Fonts. Složené písma fungovat stejně jako jakákoli jiná písma a mohou být využívána explicitně nastavení elementu FontFamily (tj. FontFamily = "Globální uživatelské rozhraní"). Můžete zadat vlastní záložní předvoleb písma vytváření složených písma a určením co písmo pro konkrétní codepoint rozsahy a jazyky.  
  
 Další informace o složená písma v tématu <xref:System.Windows.Media.FontFamily>.  
  
 **Lokalizace domovské stránce Microsoft**  
  
 Můžete postupovat podle kroků stejná jako v příkladu spustit dialogové okno k lokalizaci této aplikace. Je k dispozici pro vás v souboru CSV lokalizované pro arabštinu [globalizace domovské stránky ukázka](http://go.microsoft.com/fwlink/?LinkID=159990).
