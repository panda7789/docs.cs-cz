---
title: Přehled globalizace a lokalizace
description: Přečtěte si o lokalizaci a globalizaci pro Windows Presentation Foundation, včetně automatického rozložení, satelitních sestavení a lokalizovaných atributů.
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 9a54ce2c265b989f99383ff9cdec961c80dd655c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168286"
---
# <a name="wpf-globalization-and-localization-overview"></a>Přehled globalizace a lokalizace WPF

Když omezíte dostupnost produktu jenom na jeden jazyk, omezíte potenciální zákaznickou základnu na zlomek světové populace z našeho světa 7 500 000 000. Pokud chcete, aby se vaše aplikace dostaly do globální cílové skupiny, je cenově výhodné lokalizace vašeho produktu jedním z nejlepších a nejúčinnějších způsobů, jak oslovit více zákazníků.

Tento přehled zavádí globalizaci a lokalizaci v nástroji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] . Globalizace je návrh a vývoj aplikací, které jsou prováděny ve více umístěních. Globalizace například podporuje lokalizovaná uživatelská rozhraní a regionální data pro uživatele v různých jazykových verzích. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje globální funkce návrhu, včetně automatického rozložení, satelitních sestavení a lokalizovaných atributů a komentářů.

Lokalizace je převod prostředků aplikace do lokalizovaných verzí pro konkrétní jazykové verze, které aplikace podporuje. Při lokalizaci v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použijete rozhraní API v <xref:System.Windows.Markup.Localizer> oboru názvů. Tato rozhraní API zapněte ukázkový nástroj příkazového řádku [nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml) . Informace o tom, jak sestavovat a používat LocBaml, najdete v tématu [lokalizace aplikace](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Osvědčené postupy pro globalizaci a lokalizaci v subsystému WPF

Můžete provést většinu funkcí globalizace a lokalizace, která je integrována v rámci, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podle návrhu uživatelského rozhraní a tipů týkajících se lokalizace, které tato část poskytuje.

### <a name="best-practices-for-wpf-ui-design"></a>Osvědčené postupy pro návrh uživatelského rozhraní WPF

Při navrhování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] založeném na bázi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zvažte implementaci těchto osvědčených postupů:

- Zapište své prostředí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Vyhněte se vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v kódu. Když vytvoříte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , budete ho zveřejňovat prostřednictvím integrovaných rozhraní API lokalizace.

- Nepoužívejte absolutní umístění a pevné velikosti pro rozložení obsahu; místo toho použijte relativní nebo automatické změny velikosti.

  - Používejte <xref:System.Windows.Window.SizeToContent%2A> a udržujte šířky a výšky nastavené na `Auto` .

  - Nepoužívejte <xref:System.Windows.Controls.Canvas> k rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] s.

  - Použití <xref:System.Windows.Controls.Grid> a funkce pro sdílení velikosti.

- Poskytněte nadbytečné místo v okrajích, protože lokalizovaný text často vyžaduje více místa. Dodatečné místo umožňuje možné přeseknutí znaků.

- Povolte <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> <xref:System.Windows.Controls.TextBlock> , aby se zabránilo oříznutí.

- Nastavte `xml:lang` atribut. Tento atribut popisuje jazykovou verzi konkrétního prvku a jeho podřízených elementů. Hodnota této vlastnosti mění chování několika funkcí v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Například změní chování při dělení slov, kontrolu pravopisu, nahrazování čísel, složité tvarování skriptů a Fallback písma. Další informace o nastavení [zpracování XML: lang v jazyce XAML](../../../desktop-wpf/xaml-services/xml-language-handling.md)naleznete v tématu [globalizace pro WPF](globalization-for-wpf.md) .

- Vytvořte vlastní složené písmo, abyste získali lepší kontrolu nad písmy, která se používají v různých jazycích. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá GlobalUserInterface. složené písmo v adresáři Windows\Fonts.

- Při vytváření navigačních aplikací, které mohou být lokalizovány do jazykové verze, která prezentuje text ve formátu zprava doleva, explicitně nastavte <xref:System.Windows.FlowDirection> každou stránku, aby bylo zajištěno, že stránka nedědí <xref:System.Windows.FlowDirection> z <xref:System.Windows.Navigation.NavigationWindow> .

- Když vytváříte samostatné navigační aplikace, které jsou hostovány mimo prohlížeč, nastavte <xref:System.Windows.Application.StartupUri%2A> pro počáteční aplikaci na <xref:System.Windows.Navigation.NavigationWindow> místo na stránku (například `<Application StartupUri="NavigationWindow.xaml">` ). Tento návrh umožňuje změnit <xref:System.Windows.FlowDirection> okno a navigační panel. Další informace a příklad naleznete v části [Ukázka domovské stránky globalizace](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).

### <a name="best-practices-for-wpf-localization"></a>Osvědčené postupy pro lokalizaci WPF

Při lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací založených na platformě zvažte implementaci těchto osvědčených postupů:

- Použijte lokalizační komentáře k poskytnutí dalšího kontextu pro lokalizovatelné.

- Použijte lokalizační atributy k řízení lokalizace namísto selektivního vynechání <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastností u elementů. Další informace najdete v tématu [lokalizace atributů a komentářů](localization-attributes-and-comments.md) .

- Pomocí `msbuild -t:updateuid` a `-t:checkuid` můžete přidat a ověřit <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Pomocí <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastností můžete sledovat změny mezi vývojem a lokalizací. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>vlastnosti vám pomůžou lokalizovat nové vývojové změny. Pokud ručně přidáte <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , úkol je obvykle zdlouhavý a méně přesný.

  - Neupravujte ani neměňte <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti po zahájení lokalizace.

  - Nepoužívejte duplicitní <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vlastnosti (nezapomeňte tento tip použít při použití příkazu kopírování a vložení).

  - Nastavte `UltimateResourceFallback` umístění v souboru AssemblyInfo. \* Určete vhodný jazyk pro záložní (například `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]` ).

    Pokud se rozhodnete zahrnout zdrojový jazyk do hlavního sestavení vyvoláním `<UICulture>` značky v souboru projektu, nastavte `UltimateResourceFallback` umístění jako hlavní sestavení namísto satelitního (například `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]` ).

## <a name="localize-a-wpf-application"></a>Lokalizace aplikace WPF

Při lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace máte několik možností. Můžete například navazovat lokalizovatelné prostředky v aplikaci na soubor XML, uložit Lokalizovatelný text v tabulkách resx nebo nechat soubory lokalizátora používat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Tato část popisuje pracovní postup lokalizace, který používá formát BAML jazyka XAML, který poskytuje několik výhod:

- Po sestavení můžete lokalizovat.

- Můžete aktualizovat na novější verzi formátu BAML s lokalizacemi ze starší verze formátu BAML XAML, aby bylo možné lokalizovat ve stejnou dobu, kterou vyvíjíte.

- Můžete ověřit původní zdrojové prvky a sémantiku v době kompilace, protože formát BAML XAML je kompilovaná forma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

### <a name="localization-build-process"></a>Proces sestavení lokalizace

Při vývoji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je proces sestavení pro lokalizaci následující:

- Vývojář vytvoří a globalizace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. V souboru projektu, který vývojář nastaví `<UICulture>en-US</UICulture>` tak, aby se při kompilování aplikace vygenerovalo hlavní sestavení s neutrálním jazykem. Toto sestavení má satelitní .resources.dll soubor, který obsahuje všechny lokalizovatelné prostředky. V případě potřeby můžete zachovat zdrojový jazyk v hlavním sestavení, protože naše rozhraní API lokalizace podporují extrakci z hlavního sestavení.

- Když je soubor zkompilován do sestavení, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je převedena na formu BAML XAML. `MyDialog.exe`Anglické a kulturní soubory (anglicky), které jsou v angličtině, `MyDialog.resources.dll` jsou vydány pro uživatele, kteří mají zkušenosti s anglickým hlasem.

### <a name="localization-workflow"></a>Pracovní postup lokalizace

Proces lokalizace začíná po sestavení nemístně `MyDialog.resources.dll` vytvořeného souboru. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Prvky a vlastnosti v originálu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou extrahovány z formátu BAML jazyka XAML do párů klíč-hodnota pomocí rozhraní API v <xref:System.Windows.Markup.Localizer> . Lokalizovat používají páry klíč-hodnota k lokalizaci aplikace. Po dokončení lokalizace můžete vygenerovat nové .resource.dll z nových hodnot.

Klíče párů klíč-hodnota jsou `x:Uid` hodnoty, které vývojář umístí do původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Tyto `x:Uid` hodnoty umožňují rozhraní API sledovat a slučovat změny, ke kterým dochází mezi vývojářem a lokalizátora během lokalizace. Pokud se například vývojář změní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] po lokalizátora, můžete sloučit změny vývoje s již dokončenou prací lokalizace, aby se ztratila minimální práce v překladu.

Následující obrázek znázorňuje typický pracovní postup lokalizace, který je založen na formátu BAML jazyka XAML. Tento diagram předpokládá, že vývojář zapíše aplikaci v angličtině. Vývojář vytvoří a globalizace aplikaci WPF. V souboru projektu, který vývojář nastaví `<UICulture>en-US</UICulture>` tak, aby na sestavení, je jazykově neutrální hlavní sestavení vygenerováno pomocí satelitního .resources.dll obsahujícího všechny lokalizovatelné prostředky. Alternativně může jeden zdrojový jazyk v hlavním sestavení zachovat, protože rozhraní API lokalizace WPF podporují extrakci z hlavního sestavení. Po procesu sestavení se XAML zkompiluje do BAML. Kulturně neutrální MyDialog.exe.resources.dll dostanou zákazníkům v angličtině.

![Diagram znázorňující pracovní postup lokalizace.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Diagram znázorňující nemístní pracovní postup](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>Příklady lokalizace WPF

Tato část obsahuje příklady lokalizovaných aplikací, které vám pomůžou pochopit, jak sestavovat a lokalizovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.

### <a name="run-dialog-box-example"></a>Příklad dialogového okna pro spuštění

Následující obrázek ukazuje výstup ukázkového dialogového okna **spuštění** .

**Angličtina:**

![Snímek obrazovky se zobrazeným dialogovým oknem pro spuštění v angličtině](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Němčina:**

![Snímek obrazovky s dialogovým oknem pro spuštění v němčině](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Návrh globálního dialogového okna pro spuštění**

Tento příklad vytvoří dialogové okno **Spustit** pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Toto dialogové okno je ekvivalentní s dialogovým oknem **Spustit** , který je k dispozici v nabídce Start systému Microsoft Windows.

Mezi nejdůležitější funkce pro globální dialogová okna patří:

**Automatické rozložení**

*V souboru Window1. XAML:*

`<Window SizeToContent="WidthAndHeight">`

Předchozí vlastnost okna automaticky změní velikost okna podle velikosti obsahu. Tato vlastnost brání oknu v vyjmutí obsahu, který se po lokalizaci zvětšuje na velikost; Odebere také nepotřebné místo, když se obsah po lokalizaci zmenší.

`<Grid x:Uid="Grid_1">`

<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] správnou funkčnost rozhraní API pro lokalizaci jsou potřebné vlastnosti.

Jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraními API lokalizace ke sledování změn mezi vývojem a lokalizací [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>vlastnosti umožňují sloučit novější verzi nástroje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se starší lokalizací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Vlastnost lze přidat <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> spuštěním `msbuild -t:updateuid RunDialog.csproj` příkazu v příkazovém prostředí. Toto je doporučená metoda přidávání vlastností, <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> protože jejich ruční přidání je obvykle časově náročné a méně přesné. Můžete kontrolovat, zda <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> jsou vlastnosti správně nastaveny spuštěním `msbuild -t:checkuid RunDialog.csproj` .

[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Je strukturován pomocí <xref:System.Windows.Controls.Grid> ovládacího prvku, který je užitečným ovládacím prvkem pro využití automatického rozložení v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Všimněte si, že je dialogové okno rozděleno na tři řádky a pět sloupců. Není jedna z definic řádků a sloupců má pevnou velikost; Proto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] mohou být prvky, které jsou umístěny v každé buňce, přizpůsobeny zvýšení a snížení velikosti během lokalizace.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

První dva sloupce, kde je umístěn **otevřený:** Label a <xref:System.Windows.Controls.ComboBox> jsou použity, používají 10 procent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] celkové šířky.

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Všimněte si, že v příkladu se používá funkce sdílené velikosti <xref:System.Windows.Controls.Grid> . Poslední tři sloupce využívají tyto možnosti samotným umístěním do stejného <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> . Vzhledem k tomu, že by to bylo očekáváno od názvu vlastnosti, umožní to, aby sloupce sdílely stejnou velikost. Takže když "Procházet..." bude lokalizována do delšího řetězce "Durchsuchen...", všechna tlačítka se zvětšují šířkou namísto malého tlačítka "OK" a neúměrně velkých "Durchsuchen...". tlačítko.

**XML: lang**

`xml:lang="en-US"`

Všimněte si [XML: zpracování jazyka v jazyce XAML](../../../desktop-wpf/xaml-services/xml-language-handling.md) , které je umístěno v kořenovém elementu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Tato vlastnost popisuje jazykovou verzi daného prvku a jeho podřízených objektů. Tuto hodnotu používá několik funkcí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a při lokalizaci by měla být vhodně měněna. Tato hodnota změní jazyk slovníku, který se používá k dělení slov a pravopisné kontrolní výrazy. Má vliv také na zobrazení číslic a na způsob, jakým způsobem záložní systém písem vybere písmo, které se má použít. Nakonec vlastnost ovlivňuje způsob zobrazení čísel a způsob, jakým jsou napsány texty v složitých skriptech. Výchozí hodnota je "en-US".

**Sestavení satelitního sestavení prostředků**

*V. csproj:*

Upravte `.csproj` soubor a přidejte následující značku do nepodmíněného `<PropertyGroup>` :

`<UICulture>en-US</UICulture>`

Všimněte si přidání `UICulture` hodnoty. Pokud je tato hodnota nastavena na platnou <xref:System.Globalization.CultureInfo> hodnotu, například en-US, sestavení projektu vygeneruje satelitní sestavení se všemi lokalizovatelnými prostředky.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

`RunIcon.JPG`Není nutné, aby byla lokalizována, protože by měla být zobrazena stejně pro všechny jazykové verze. `Localizable`je nastaven na `false` tak, aby zůstal v jazyce neutrálním hlavním sestavením namísto satelitního sestavení. Výchozí hodnota všech prostředků noncompilable je `Localizable` nastavená na `true` .

**Lokalizace dialogového okna pro spuštění**

**Parse** (Parsování)

Po sestavení aplikace se v prvním kroku lokalizace analyzuje lokalizovatelné prostředky ze satelitního sestavení. Pro účely tohoto tématu použijte vzorový LocBaml Tool, který najdete v [ukázce nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml). Všimněte si, že LocBaml je pouze ukázkový nástroj, který vám může pomoci začít při vytváření lokalizačního nástroje, který se vejde do procesu lokalizace. Pomocí LocBaml spusťte následující příkaz k analýze: **LocBaml/parse RunDialog.resources.dll/out:** pro vygenerování souboru "RunDialog.resources.dll.CSV".

**Lokalizovat**

Pro úpravu tohoto souboru použijte oblíbený editor CSV, který podporuje kódování Unicode. Odfiltruje všechny položky s kategorií lokalizace "none". Měly by se zobrazit následující položky:

|Klíč prostředku|Kategorie lokalizace|Hodnota|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Tlačítko|OK|
|Button_2: System. Windows. Controls. Button. $Content|Tlačítko|Zrušit|
|Button_3: System. Windows. Controls. Button. $Content|Tlačítko|Procházet...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Text|Zadejte název programu, složky, dokumentu nebo zdroje v internetu a systém Windows jej otevře.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Text|Otevřít:|
|Window_1: System. Windows. Window. title|Nadpis|Spustit|

Lokalizace aplikace do němčiny by vyžadovala následující překlady:

|Klíč prostředku|Kategorie lokalizace|Hodnota|
|-|-|-|
|Button_1: System. Windows. Controls. Button. $Content|Tlačítko|OK|
|Button_2: System. Windows. Controls. Button. $Content|Tlačítko|Abbrechen|
|Button_3: System. Windows. Controls. Button. $Content|Tlačítko|Durchsuchen...|
|ComboBox_1: System. Windows. Controls. ComboBox. $Content|ComboBox||
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Text|Geben Sie den Namen eines, Ordners, dokumenty oder einer Internetresource a.|
|TextBlock_2: System. Windows. Controls. TextBlock. $Content|Text|Öffnen:|
|Window_1: System. Windows. Window. title|Nadpis|Spustit|

**Generovat**

Poslední krok lokalizace zahrnuje vytvoření nově lokalizovaného satelitního sestavení. To lze provést pomocí následujícího příkazu LocBaml:

**LocBaml.exe/Generate RunDialog.resources.dll/trans:RunDialog.resources.dll.CSV/out:. /CUL: de-DE DE**

V případě německého okna platí, že pokud je tento resources.dll umístěn ve složce de-DE vedle hlavního sestavení, bude tento prostředek automaticky načten místo do složky en-US. Pokud nemáte v německé verzi Windows k otestování, nastavte jazykovou verzi na libovolnou jazykovou verzi Windows, kterou používáte (například `en-US` ), a nahraďte původní DLL prostředky.

**Načítání satelitních prostředků**

|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Kód|Původní anglická verze BAML|Lokalizovaný BAML|
|Kulturně neutrální prostředky|Další prostředky v angličtině|Další prostředky lokalizované do němčiny|

Rozhraní .NET automaticky zvolí, které sestavení satelitních prostředků se má načíst na základě aplikace <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> . Tato hodnota je nastavená na jazykovou verzi operačního systému Windows. Pokud používáte německé Windows, soubor *de-DE\MyDialog.resources.dll* se načte. Pokud používáte anglickou verzi Windows, soubor *en-US\MyDialog.resources.dll* se načte. Můžete nastavit konečný záložní prostředek pro aplikaci zadáním `NeutralResourcesLanguage` atributu v souboru *AssemblyInfo* projektu. Pokud například zadáte:

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

pak se soubor *en-US\MyDialog.resources.dll* používá s německými okny, pokud nejsou k dispozici žádné z následujících souborů: *de-DE\MyDialog.resources.dll* nebo *de\MyDialog.resources.dll*.

### <a name="microsoft-saudi-arabia-homepage"></a>Domovská stránka Microsoft Saúdská Arábie

Následující obrázek ukazuje domovskou stránku pro angličtinu a arabštinu. Kompletní vzorek, který vytváří tyto grafiky, najdete v [ukázce domovské stránky globalizace](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).

**Angličtina:**

![Snímek obrazovky zobrazující domovskou stránku v angličtině](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arabština:**

![Snímek obrazovky znázorňující arabskou domovskou stránku](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Návrh globální domovské stránky Microsoftu

Tento model webu Microsoft Saúdská Arábie ilustruje funkce globalizace, které jsou k dispozici pro jazyky RightToLeft. Jazyky, jako jsou hebrejština a arabština, mají směr čtení zprava doleva, takže rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musí být často rozloženo mnohem jinak, než by bylo v jazycích abecedy, jako je angličtina. Lokalizace od zleva doprava po jazyku zprava doleva a naopak může být poměrně náročná. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bylo navrženo tak, aby tyto lokalizace bylo mnohem snazší.

**FlowDirection**

*Domovská stránka. XAML:*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

Všimněte si <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnosti <xref:System.Windows.Controls.Page> . Změnou této vlastnosti na <xref:System.Windows.FlowDirection.RightToLeft> dojde ke změně <xref:System.Windows.FrameworkElement.FlowDirection%2A> ovládacího prvku <xref:System.Windows.Controls.Page> a jeho podřízených prvků tak, aby bylo rozložení tohoto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] překlopení převráceno na hodnotu zprava doleva v případě, že by se očekávalo arabského uživatele. Jeden může přepsat chování dědičnosti zadáním explicitní <xref:System.Windows.FrameworkElement.FlowDirection%2A> na jakémkoli elementu. <xref:System.Windows.FrameworkElement.FlowDirection%2A>Vlastnost je k dispozici na jakémkoli <xref:System.Windows.FrameworkElement> elementu nebo v dokumentu, který je v relaci, a má implicitní hodnotu <xref:System.Windows.FlowDirection.LeftToRight> .

Všimněte si, že i když se změní kořenový adresář, jsou štětce barevného přechodu pozadí správně převráceny <xref:System.Windows.FrameworkElement.FlowDirection%2A> :

**FlowDirection = "LeftToRight"**

![Snímek obrazovky zobrazující tok přechodu zleva doprava](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection = "RightToLeft"**

![Snímek obrazovky zobrazující tok přechodu zprava doleva](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Vyhnout se použití pevných dimenzí pro panely a ovládací prvky**

Prohlédněte si stránku domove. XAML a Všimněte si, že z pevného šířky a výšky zadané pro celý [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na začátku <xref:System.Windows.Controls.DockPanel> nejsou žádné jiné pevné dimenze. Vyhněte se použití pevných dimenzí k zabránění oříznutí lokalizovaného textu, který může být delší než zdrojový text. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]panely a ovládací prvky se automaticky změní na základě obsahu, který obsahují. Většina ovládacích prvků má také minimální a maximální rozměry, které lze nastavit pro více ovládacích prvků (například MinWidth = "20"). Pomocí <xref:System.Windows.Controls.Grid> můžete také nastavit relativní šířky a výšky pomocí ' \* ' (například `Width="0.25*"` ) nebo použít funkci sdílení velikosti buňky.

**Komentáře lokalizace**

Existuje mnoho případů, kdy může být obsah dvojznačný a obtížné ho přeložit. Vývojář nebo Návrhář má možnost poskytnout dalším kontextům a komentářům k lokalizacím prostřednictvím lokalizačních komentářů. Například lokalizace. komentáře níže upřesňují použití znaku ' &#124; '.

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

Tento komentář se bude přidružit k obsahu TextBlock_1 a v případě nástroje LocBaml (viz [lokalizace aplikace](how-to-localize-an-application.md)), může se zobrazit v šesté sloupci TextBlock_1 řádku ve výstupním souboru. CSV:

|Klíč prostředku|Kategorie|Čitelný|Upravitelná|Komentář|Hodnota|
|-|-|-|-|-|-|
|TextBlock_1: System. Windows. Controls. TextBlock. $Content|Text|TRUE|PRAVDA|Tento znak se používá jako ozdobné pravidlo.|&#124;|

Komentáře lze umístit na obsah nebo vlastnost libovolného elementu pomocí následující syntaxe:

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**Atributy lokalizace**

Vývojář nebo Správce lokalizace často potřebuje kontrolu nad tím, co můžou lokalizovat mohou číst a upravovat. Například nebudete chtít, aby lokalizátora přeložil název vaší společnosti nebo právní slovo. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje atributy, které umožňují nastavit čitelnost, upravitelnost a kategorii obsahu nebo vlastnosti prvku, který může nástroj pro lokalizaci použít k uzamknutí, skrytí nebo řazení prvků. Další informace naleznete v tématu <xref:System.Windows.Localization.Attributes%2A>. Pro účely této ukázky nástroj LocBaml pouze vytvoří výstup hodnot těchto atributů. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ovládací prvky všechny mají výchozí hodnoty pro tyto atributy, ale můžete je přepsat. Například následující příklad přepisuje výchozí atributy lokalizace pro `TextBlock_1` a nastaví obsah tak, aby byl čitelný, ale nedokáže být pro lokalizovatelné.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

Kromě atributů čitelnosti a modifikátoru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje výčet běžných kategorií uživatelského rozhraní ( <xref:System.Windows.LocalizationCategory> ), které lze použít k tomu, aby lokalizovat více kontextu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Výchozí kategorie pro ovládací prvky platformy lze přepsat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] také:

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

Výchozí atributy lokalizace, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytují, lze také přepsat prostřednictvím kódu, takže můžete správně nastavit správné výchozí hodnoty pro vlastní ovládací prvky. Například:

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

Atributy pro atribut instance nastavené v nástroji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mají přednost před hodnotami nastavenými v kódu pro vlastní ovládací prvky. Další informace o atributech a komentářích naleznete v tématu [lokalizace atributů a komentářů](localization-attributes-and-comments.md).

**Náhradní písma a složená písma**

Pokud zadáte písmo, které nepodporuje daný rozsah kódu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automaticky se převede na jeden, který používá globální uživatelské rozhraní. compositefont, které se nachází v adresáři Windows\Fonts. Složená písma fungují stejně jako jakákoli jiná písma a lze je použít explicitně nastavením prvku `FontFamily` (například `FontFamily="Global User Interface"` ). Můžete určit vlastní možnost nouzového písma, a to vytvořením vlastního složeného písma a určením písma, které se má použít pro konkrétní kódu rozsahy a jazyky.

Další informace o složených písmech najdete v tématu <xref:System.Windows.Media.FontFamily> .

**Lokalizace domovské stránky Microsoftu**

K lokalizaci této aplikace můžete použít stejný postup jako v dialogovém okně Spustit. Lokalizovaný soubor. CSV pro arabštinu je k dispozici v [ukázce domovské stránky globalizace](https://github.com/microsoft/WPF-Samples/tree/master/Globalization%20and%20Localization/GlobalizationHomepage).
