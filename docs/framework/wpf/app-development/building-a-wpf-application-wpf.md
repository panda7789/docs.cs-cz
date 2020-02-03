---
title: Kompilace aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 00c76dfcdcedc7ceaefaaae785368f8b343457a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744764"
---
# <a name="compile-a-wpf-application"></a>Kompilace aplikace WPF

Aplikace Windows Presentation Foundation (WPF) mohou být sestaveny jako .NET Framework spustitelné soubory (. exe), knihovny (. dll) nebo kombinace obou typů sestavení. Toto téma ukazuje, jak sestavit aplikace WPF a popisuje klíčové kroky v procesu sestavení.

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>Sestavení aplikace WPF

Aplikace WPF může být zkompilována následujícími způsoby:

- Příkazový řádek. Aplikace musí obsahovat pouze kód (žádný XAML) a definiční soubor aplikace. Další informace najdete v tématu [sestavování z příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo při [sestavování z příkazového řádku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

- Microsoft Build Engine (MSBuild). Kromě kódu a souborů XAML musí aplikace obsahovat soubor projektu MSBuild. Další informace naleznete v tématu "MSBuild".

- Visual Studio. Visual Studio je integrované vývojové prostředí, které kompiluje aplikace WPF pomocí nástroje MSBuild a obsahuje vizuálního návrháře pro vytváření uživatelského rozhraní. Další informace najdete v tématu [zápis a Správa kódu pomocí sady Visual Studio](/visualstudio/ide/index-writing-code) a [Návrh XAML v aplikaci Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>Kanál sestavení WPF

Při sestavení projektu WPF je vyvolána kombinace cílů specifických pro jazyk a WPF. Proces provádění těchto cílů se nazývá kanál sestavení a klíčové kroky jsou znázorněny na následujícím obrázku.

![Proces sestavení WPF](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>Inicializace před sestavením

Před sestavením nástroj MSBuild určí umístění důležitých nástrojů a knihoven, včetně následujících:

- .NET Framework.

- Adresáře Windows SDK.

- Umístění referenčních sestavení WPF.

- Vlastnost pro cesty pro vyhledávání sestavení.

První umístění, kde MSBuild vyhledává sestavení, je referenční adresář sestavení (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). Během tohoto kroku proces sestavení také inicializuje různé vlastnosti a skupiny položek a provede všechny potřebné čisticí operace.

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>Řešení odkazů

Proces sestavení vyhledá a vytvoří vazby sestavení potřebných k sestavení projektu aplikace. Tato logika je obsažena v úloze `ResolveAssemblyReference`. Všechna sestavení deklarovaná jako `Reference` v souboru projektu jsou k dispozici pro úlohu spolu s informacemi o cestách pro vyhledávání a metadatech na sestaveních, která jsou již v systému nainstalována. Úkol vyhledá sestavení a používá metadata nainstalovaného sestavení k vyfiltrování těchto základních sestavení WPF, která se nemusí zobrazit ve výstupních manifestech. To se provádí, aby se zabránilo redundantním informacím v manifestech ClickOnce. Například vzhledem k tomu, že PresentationFramework. dll lze považovat za zástupce aplikace založené na a pro WPF a vzhledem k tomu, že všechna sestavení WPF existují na stejném umístění na každém počítači, který má .NET Framework nainstalován, není nutné zahrnout vše informace o všech .NET Framework odkazujících na sestavení v manifestech.

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>Kompilace značek – Pass 1

V tomto kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory analyzovány a kompilovány tak, aby modul runtime nestrávil čas analýzy XML a ověřování hodnot vlastností. Kompilovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je předem vydaný, takže při spuštění by měl být v době běhu mnohem rychlejší než načtení souboru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Během tohoto kroku probíhají následující aktivity pro každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor, který je `Page` položkou sestavení:

1. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je analyzován kompilátorem značek.

2. Pro tento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je vytvořena kompilovaná reprezentace a zkopírována do složky obj\Release.

3. Je vytvořena reprezentace CodeDOM nové částečné třídy a zkopírována do složky obj\Release.

Kromě toho je pro každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor vygenerován soubor kódu specifický pro daný jazyk. Například pro stránku Page1. XAML v projektu Visual Basic je vygenerována Page1. g. vb; pro stránku Page1. XAML v C# projektu je vygenerována Page1.g.cs. ". G" v názvu souboru označuje soubor je generovaný kód, který má deklaraci částečné třídy pro element nejvyšší úrovně souboru označení (například `Page` nebo `Window`). Třída je deklarována s modifikátorem `partial` v C# (`Extends` ve Visual Basic) k označení, že existuje jiná deklarace pro třídu jinde, obvykle v souboru kódu na pozadí Page1.XAML.cs.

Částečná třída sahá od příslušné základní třídy (například <xref:System.Windows.Controls.Page> pro stránku) a implementuje rozhraní <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType>. Rozhraní <xref:System.Windows.Markup.IComponentConnector> obsahuje metody pro inicializaci komponenty a připojení názvů a událostí k prvkům v jejím obsahu. V důsledku toho generovaný soubor kódu má implementaci metody jako následující:

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

Ve výchozím nastavení se kompilace kódu spouští ve stejném <xref:System.AppDomain> jako modul MSBuild. Tím je zajištěno výrazné zvýšení výkonu. Toto chování lze přepnout pomocí vlastnosti `AlwaysCompileMarkupFilesInSeparateDomain`. To má výhodu odinstalování všech referenčních sestavení odinstalováním samostatného <xref:System.AppDomain>.

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>Kompilace značek – Pass 2

Ne všechny stránky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou kompilovány během průchodu 1 kompilace kódu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které mají místně definované odkazy na typ (odkazy na typy definované v kódu jinde ve stejném projektu), jsou v tuto chvíli vyjmuty z kompilace. Důvodem je, že tyto lokálně definované typy existují pouze ve zdroji a ještě nejsou kompilovány. Chcete-li určit, analyzátor používá heuristiky, které zahrnují hledání položek, jako je například `x:Name` v souboru označení. Pokud je taková instance nalezena, je kompilace souboru označení odložena, dokud nebudou zkompilovány soubory kódu, potom druhá kompilace kódu zpracuje tyto soubory.

<a name="File_Classification"></a>

### <a name="file-classification"></a>Klasifikace souborů

Proces sestavení vloží výstupní soubory do různých skupin prostředků na základě toho, do kterého sestavení aplikace budou umístěna. V typické nemístní aplikaci jsou všechny datové soubory označené jako `Resource` umístěny do hlavního sestavení (spustitelný soubor nebo knihovna). Pokud je v projektu nastavena `UICulture`, všechny zkompilované soubory [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a tyto prostředky konkrétně označené jako jazyk jsou umístěny v sestavení satelitních prostředků. Kromě toho všechny jazykové a neutrální prostředky jsou umístěny v hlavním sestavení. V tomto kroku procesu sestavení je toto určení provedeno.

Akce `ApplicationDefinition`, `Page`a `Resource` sestavení v souboru projektu lze rozšířit pomocí `Localizable` metadat (přípustné hodnoty jsou `true` a `false`), která určuje, zda je soubor specifický pro jazyk nebo jazykově neutrální.

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>Základní kompilace

Základní krok kompilace zahrnuje kompilaci souborů kódu. Toto je orchestrace pomocí logiky v souborech cílů specifických pro jazyk Microsoft. CSharp. targets a Microsoft. VisualBasic. targets. Pokud heuristické metody určily, že jeden průchod překladače kódu je dostatečný, pak je vygenerováno hlavní sestavení. Pokud však jeden nebo více [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů v projektu obsahuje odkazy na lokálně definované typy, pak je vygenerován dočasný soubor DLL, aby konečné sestavení aplikace bylo možné vytvořit po dokončení druhé průchodu kompilace kódu.

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>Generování manifestu

Po dokončení procesu sestavení po přípravě všech sestavení aplikace a souborů obsahu jsou vytvořeny manifesty ClickOnce pro aplikaci.

Soubor manifestu nasazení popisuje model nasazení: aktuální verze, chování aktualizace a identitu vydavatele spolu s digitálním podpisem. Tento manifest je určený k vytváření správců, kteří zpracovávají nasazení. Přípona souboru je. XBAP (pro aplikace prohlížeče XAML (XBAP)) a aplikace pro nainstalované aplikace. Předchozí je vypsána vlastností projektu `HostInBrowser` a v důsledku toho manifest identifikuje aplikaci jako hostovanou v prohlížeči.

Manifest aplikace (soubor. exe. manifest) popisuje sestavení aplikace a závislé knihovny a seznam oprávnění vyžadovaných aplikací. Tento soubor má být vytvořen vývojářem aplikace. Aby bylo možné spustit aplikaci ClickOnce, uživatel otevře soubor manifestu nasazení aplikace.

Tyto soubory manifestu jsou vždy vytvořeny pro XBAP. U nainstalovaných aplikací nejsou vytvořeny, pokud není vlastnost `GenerateManifests` zadána v souboru projektu s hodnotou `true`.

Aplikace XBAP získají dvě další oprávnění nad rámec těchto oprávnění přiřazených k běžným aplikacím Internet Zone: <xref:System.Security.Permissions.WebBrowserPermission> a <xref:System.Security.Permissions.MediaPermission>. Systém sestavení WPF deklaruje tato oprávnění v manifestu aplikace.

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>Podpora přírůstkového sestavení

Systém sestavení WPF poskytuje podporu pro přírůstková sestavení. Je poměrně inteligentní informace o detekci změn provedených v kódu nebo kódu a kompiluje pouze ty artefakty, které jsou ovlivněné změnou. Mechanismus přírůstkového sestavení používá následující soubory:

- Soubor $ (*AssemblyName*) _MarkupCompiler. cache pro zachování aktuálního stavu kompilátoru.

- Soubor $ (*AssemblyName*) _MarkupCompiler. lref pro ukládání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů do mezipaměti s odkazy na lokálně definované typy.

Následuje sada pravidel pro přírůstkové sestavení:

- Soubor je nejmenší jednotka, na které systém sestavení detekuje změnu. Pro soubor kódu tedy systém sestavení nemůže zjistit, zda byl typ změněn nebo zda byl přidán kód. Stejné uchovávají pro soubory projektu.

- Mechanismus přírůstkového sestavení musí být společnost Cognizant, že stránka [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] buď definuje třídu, nebo používá jiné třídy.

- Pokud se `Reference` položky změní, znovu zkompilujte všechny stránky.

- Pokud se změní soubor kódu, Rekompilujte všechny stránky s místně definovanými odkazy na typ.

- Pokud se změní soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:

  - Pokud je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deklarována jako `Page` v projektu: Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] neobsahuje lokálně definované odkazy na typ, znovu zkompilujte tuto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místními odkazy; Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahuje místní odkazy, zkompilujte všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místními odkazy.

  - Pokud je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deklarována jako `ApplicationDefinition` v projektu: překompilujte všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky (důvod: každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] má odkaz na <xref:System.Windows.Application> typ, který se mohl změnit).

- Pokud soubor projektu deklaruje soubor s kódem jako definici aplikace namísto souboru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:

  - Ověřte, zda se hodnota `ApplicationClassName` v souboru projektu změnila (existuje nový typ aplikace?). V takovém případě znovu zkompilujte celou aplikaci.

  - V opačném případě znovu zkompilujte všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místními odkazy.

- Pokud se změní soubor projektu: použijte všechna předchozí pravidla a podívejte se, co je potřeba znovu zkompilovat. Změny následujících vlastností aktivují kompletní překompilování: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`a `HostInBrowser`.

Je možné provést následující scénáře překompilování:

- Celá aplikace je znovu zkompilována.

- Znovu se zkompiluje pouze ty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které mají místně definované odkazy na typ.

- Nic se nezkompiluje (Pokud se nic v projektu nezměnilo).

## <a name="see-also"></a>Viz také

- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
- [Referenční dokumentace WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)
- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
- [Prostředek, obsah a datové soubory aplikace WPF](wpf-application-resource-content-and-data-files.md)
