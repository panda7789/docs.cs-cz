---
title: Sestavení aplikace WPF (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: a5254de07029e53dd6b72bd2c096c38525a661b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958709"
---
# <a name="building-a-wpf-application-wpf"></a>Sestavení aplikace WPF (WPF)

Aplikace Windows Presentation Foundation (WPF) mohou být sestaveny jako .NET Framework spustitelné soubory (. exe), knihovny (. dll) nebo kombinace obou typů sestavení. Toto téma ukazuje, jak sestavit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace a popisuje klíčové kroky v procesu sestavení.

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>Sestavení aplikace WPF

Aplikace WPF může být zkompilována následujícími způsoby:

- Příkazový řádek. Aplikace musí obsahovat pouze kód (žádný XAML) a definiční soubor aplikace. Další informace najdete v tématu sestavování z příkazového [řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo při sestavování [z příkazového řádku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

- Microsoft Build Engine (MSBuild). Kromě kódu a souborů XAML musí aplikace obsahovat soubor projektu MSBuild. Další informace naleznete v tématu "MSBuild".

- Visual Studio. Visual Studio je integrované vývojové prostředí, které kompiluje aplikace WPF pomocí nástroje MSBuild a obsahuje vizuálního návrháře pro vytváření uživatelského rozhraní. Další informace najdete v tématu [zápis a Správa kódu pomocí sady Visual Studio](/visualstudio/ide/index-writing-code) a [Návrh XAML v aplikaci Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>Kanál sestavení WPF

Při sestavení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]projektu je vyvolána kombinace cílů specifických pro jazyk a. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Proces provádění těchto cílů se nazývá kanál sestavení a klíčové kroky jsou znázorněny na následujícím obrázku.

![Proces sestavení WPF](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>Inicializace před sestavením

Před sestavením nástroj MSBuild určí umístění důležitých nástrojů a knihoven, včetně následujících:

- .NET Framework.

- [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Adresáře.

- Umístění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] referenčních sestavení.

- Vlastnost pro cesty pro vyhledávání sestavení.

První umístění, kde MSBuild vyhledává sestavení, je referenční adresář sestavení (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). Během tohoto kroku proces sestavení také inicializuje různé vlastnosti a skupiny položek a provede všechny potřebné čisticí operace.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>Řešení odkazů

Proces sestavení vyhledá a vytvoří vazby sestavení potřebných k sestavení projektu aplikace. Tato logika je obsažena v `ResolveAssemblyReference` úloze. Všechna sestavení deklarovaná `Reference` jako v souboru projektu jsou k dispozici pro úlohu spolu s informacemi o cestách pro vyhledávání a metadatech na sestaveních, která jsou již v systému nainstalována. Úkol vyhledá sestavení a používá metadata nainstalovaného sestavení k vyfiltrování těch základních [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení, která se nemusí zobrazit ve výstupních manifestech. To se provádí, aby se zabránilo redundantním informacím v manifestech ClickOnce. Například vzhledem k tomu, že PresentationFramework. dll lze považovat za zástupce aplikace založené na a pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a kromě toho, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] že všechna sestavení existují ve stejném umístění na každém počítači, který má .NET Framework nainstalováno, není nutné zahrnout všechny informace o všech .NET Framework referenčních sestavení v manifestech.

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>Kompilace značek – Pass 1

V tomto kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou soubory analyzovány a kompilovány, aby modul runtime nestrávil čas při analýze [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] a ověřování hodnot vlastností. Kompilovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je předem vydaný, takže jeho načtení by v době běhu mělo být mnohem rychlejší než [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] načítání souboru.

Během tohoto kroku probíhají následující aktivity pro každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor, který `Page` je položkou sestavení:

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Soubor je analyzován kompilátorem značek.

2. Pro tuto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] složku se vytvoří kompilovaná reprezentace a zkopíruje se do složky obj\Release.

3. Je vytvořena reprezentace CodeDOM nové částečné třídy a zkopírována do složky obj\Release.

Kromě toho je pro každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor vygenerován soubor kódu specifický pro daný jazyk. Například pro stránku Page1. XAML v projektu Visual Basic je vygenerována Page1. g. vb; pro stránku Page1. XAML v C# projektu je vygenerována Page1.g.cs. Soubor ". g" v názvu souboru označuje, že se jedná o generovaný kód, který má deklaraci částečné třídy pro element nejvyšší úrovně souboru označení (například `Page` nebo `Window`). Třída je deklarována s `partial` modifikátorem v C# (`Extends` v Visual Basic), aby označovala jinou deklaraci pro třídu jinde, obvykle v souboru kódu na pozadí Page1.XAML.cs.

Částečná třída sahá od příslušné základní třídy (například <xref:System.Windows.Controls.Page> pro stránku) a <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> implementuje rozhraní. <xref:System.Windows.Markup.IComponentConnector> Rozhraní obsahuje metody pro inicializaci komponenty a připojení názvů a událostí k prvkům v jejím obsahu. V důsledku toho generovaný soubor kódu má implementaci metody jako následující:

```csharp
public void InitializeComponent() {
    if (_contentLoaded) {
        return;
    }
    _contentLoaded = true;
    System.Uri resourceLocater =
        new System.Uri(
            "window1.xaml",
            System.UriKind.RelativeOrAbsolute);
    System.Windows.Application.LoadComponent(this, resourceLocater);
}
```

```vb
Public Sub InitializeComponent() _

    If _contentLoaded Then
        Return
    End If

    _contentLoaded = True
    Dim resourceLocater As System.Uri = _
        New System.Uri("mainwindow.xaml", System.UriKind.Relative)

    System.Windows.Application.LoadComponent(Me, resourceLocater)

End Sub
```

Ve výchozím nastavení se kompilace kódu spouští ve stejném <xref:System.AppDomain> formátu jako modul MSBuild. Tím je zajištěno výrazné zvýšení výkonu. Toto chování lze zapnout pomocí `AlwaysCompileMarkupFilesInSeparateDomain` vlastnosti. To má výhodu odinstalování všech referenčních sestavení odinstalováním <xref:System.AppDomain>samostatného.

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>Kompilace značek – Pass 2

Ne všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky jsou kompilovány během průchodu 1 kompilace kódu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]soubory, které mají místně definované odkazy na typ (odkazy na typy definované v kódu jinde ve stejném projektu), jsou v tuto chvíli vyjmuty z kompilace. Důvodem je, že tyto lokálně definované typy existují pouze ve zdroji a ještě nejsou kompilovány. Chcete-li určit, analyzátor používá heuristiky, které zahrnují hledání položek `x:Name` , jako je například v souboru označení. Pokud je taková instance nalezena, je kompilace souboru označení odložena, dokud nebudou zkompilovány soubory kódu, potom druhá kompilace kódu zpracuje tyto soubory.

<a name="File_Classification"></a>

### <a name="file-classification"></a>Klasifikace souborů

Proces sestavení vloží výstupní soubory do různých skupin prostředků na základě toho, do kterého sestavení aplikace budou umístěna. V typické nemístní aplikaci jsou všechny datové soubory označené jako `Resource` umístěny do hlavního sestavení (spustitelný soubor nebo knihovna). Při `UICulture` nastavení v projektu jsou všechny zkompilované [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory a tyto prostředky konkrétně označené jako specifické pro jazyk umístěny do sestavení satelitních prostředků. Kromě toho všechny jazykové a neutrální prostředky jsou umístěny v hlavním sestavení. V tomto kroku procesu sestavení je toto určení provedeno.

`Page` `true` Akce sestavení `false`, a `Resource` v souboru`Localizable` projektu lze rozšířit s metadaty (přijatelné hodnoty jsou a), která určuje, zda je soubor specifický pro jazyk nebo `ApplicationDefinition` jazykově neutrální.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>Základní kompilace

Základní krok kompilace zahrnuje kompilaci souborů kódu. Toto je orchestrace pomocí logiky v souborech cílů specifických pro jazyk Microsoft. CSharp. targets a Microsoft. VisualBasic. targets. Pokud heuristické metody určily, že jeden průchod překladače kódu je dostatečný, pak je vygenerováno hlavní sestavení. Nicméně pokud má jeden nebo více [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů v projektu odkazy na lokálně definované typy, pak je vygenerován dočasný soubor. dll, aby konečné sestavení aplikace bylo možné vytvořit po dokončení druhé průchodu kompilace kódu.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>Generování manifestu

Po dokončení procesu sestavení po přípravě všech sestavení aplikace a souborů obsahu jsou vytvořeny manifesty ClickOnce pro aplikaci.

Soubor manifestu nasazení popisuje model nasazení: aktuální verze, chování aktualizace a identitu vydavatele spolu s digitálním podpisem. Tento manifest je určený k vytváření správců, kteří zpracovávají nasazení. Přípona souboru je. XBAP (pro [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) a. Application pro nainstalované aplikace. Předchozí je vyřízena `HostInBrowser` vlastností projektu a v důsledku toho manifest identifikuje aplikaci jako hostovanou v prohlížeči.

Manifest aplikace (soubor. exe. manifest) popisuje sestavení aplikace a závislé knihovny a seznam oprávnění vyžadovaných aplikací. Tento soubor má být vytvořen vývojářem aplikace. Aby bylo možné spustit aplikaci ClickOnce, uživatel otevře soubor manifestu nasazení aplikace.

Tyto soubory manifestu jsou vždy vytvořeny pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. U nainstalovaných aplikací nejsou vytvořeny, pokud `GenerateManifests` není vlastnost určena v souboru projektu s hodnotou. `true`

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Získejte dvě další oprávnění nad rámec těchto oprávnění přiřazených k běžným aplikacím Internet Zone <xref:System.Security.Permissions.WebBrowserPermission> : <xref:System.Security.Permissions.MediaPermission>a. Systém [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení deklaruje tato oprávnění v manifestu aplikace.

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>Podpora přírůstkového sestavení

Systém [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení poskytuje podporu pro přírůstková sestavení. Je poměrně inteligentní informace o detekci změn provedených v kódu nebo kódu a kompiluje pouze ty artefakty, které jsou ovlivněné změnou. Mechanismus přírůstkového sestavení používá následující soubory:

- Soubor _MarkupCompiler. cache aplikace $ (*AssemblyName*) pro zachování aktuálního stavu kompilátoru.

- Soubor $ (*AssemblyName*) _MarkupCompiler. lref pro ukládání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů s odkazy na lokálně definované typy.

Následuje sada pravidel pro přírůstkové sestavení:

- Soubor je nejmenší jednotka, na které systém sestavení detekuje změnu. Pro soubor kódu tedy systém sestavení nemůže zjistit, zda byl typ změněn nebo zda byl přidán kód. Stejné uchovávají pro soubory projektu.

- Mechanismus přírůstkového sestavení musí být společnost Cognizant, že [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka buď definuje třídu, nebo používá jiné třídy.

- Pokud `Reference` se položky změní, znovu zkompilujte všechny stránky.

- Pokud se změní soubor kódu, Rekompilujte všechny stránky s místně definovanými odkazy na typ.

- Pokud se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] změní soubor:

  - Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je deklarován jako `Page` v projektu: Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] neobsahuje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokálně definované odkazy na typ, zkompilujte znovu a všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místními odkazy; Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] má místní odkazy, Rekompilujte všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místními odkazy.

  - Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je deklarován jako `ApplicationDefinition` v projektu: rekompilovat všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky <xref:System.Windows.Application> (důvod: každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] má odkaz na typ, který se mohl změnit).

- Pokud soubor projektu deklaruje soubor s kódem jako definici aplikace namísto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru:

  - Zkontroluje, jestli `ApplicationClassName` se hodnota v souboru projektu nezměnila (je to nový typ aplikace?). V takovém případě znovu zkompilujte celou aplikaci.

  - V opačném případě znovu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zkompilujte všechny stránky s místními odkazy.

- Pokud se změní soubor projektu: použijte všechna předchozí pravidla a podívejte se, co je potřeba znovu zkompilovat. Změny následujících vlastností `AssemblyName`aktivují kompletní znovu zkompilování:, `IntermediateOutputPath`, `RootNamespace`a `HostInBrowser`.

Je možné provést následující scénáře překompilování:

- Celá aplikace je znovu zkompilována.

- Znovu se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zkompiluje pouze ty soubory, které mají místně definované odkazy na typ.

- Nic se nezkompiluje (Pokud se nic v projektu nezměnilo).

## <a name="see-also"></a>Viz také:

- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
- [Referenční dokumentace WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)
- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
- [Prostředek, obsah a datové soubory aplikace WPF](wpf-application-resource-content-and-data-files.md)
