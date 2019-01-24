---
title: Sestavení aplikace WPF (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 3bae07f8b72225ccb502a32fbc03fb4651c80d63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654279"
---
# <a name="building-a-wpf-application-wpf"></a>Sestavení aplikace WPF (WPF)
Aplikace Windows Presentation Foundation (WPF) může být sestaven jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] spustitelné soubory (.exe), knihovny (DLL), nebo kombinací obou typů sestavení. Toto téma popisuje, jak vytvořit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací a popisuje klíčové kroky v procesu sestavení.  
  
  
<a name="Building_a_WPF_Application_using_Command_Line"></a>   
## <a name="building-a-wpf-application"></a>Sestavení aplikace WPF  
 Aplikace WPF, mohou být zkompilovány následujícími způsoby:  
  
-   Příkazový řádek. Aplikace musí obsahovat pouze kód (bez XAML) a soubor definice aplikace. Další informace najdete v tématu [sestavení příkazového řádku s csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
-   Microsoft Build Engine (MSBuild). Kromě kód a soubory XAML musí aplikace obsahovat souboru projektu MSBuild. Další informace najdete v tématu "MSBuild".  
  
-   Visual Studio. Visual Studio je integrované vývojové prostředí, které aplikace WPF pomocí nástroje MSBuild zkompiluje a obsahuje vizuálního návrháře pro vytvoření uživatelského rozhraní. Další informace najdete v tématu [vývoj aplikací v sadě Visual Studio](https://msdn.microsoft.com/library/97490c1b-a247-41fb-8f2c-bc4c201eff68) a [návrh XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>   
## <a name="wpf-build-pipeline"></a>WPF Build Pipeline  
 Když [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projekt se vytvořil, kombinace specifické pro jazyk a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]– jsou vyvolány určité cíle. Proces provedení tyto cíle se nazývá kanálu sestavení, a jsou klíčové kroky návodu na následujícím obrázku.  
  
 ![Proces sestavení WPF](../../../../docs/framework/wpf/app-development/media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")  
  
<a name="Pre_Build_Initializations"></a>   
### <a name="pre-build-initializations"></a>Inicializace před sestavením  
 Před sestavením, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] Určuje umístění důležité nástroje a knihovny, včetně následujících:  
  
-   Rozhraní .NET Framework.  
  
-   [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Adresáře.  
  
-   Umístění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] odkazovat na sestavení.  
  
-   Vlastnost cesty pro vyhledávání sestavení.  
  
 První místo kde [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] vyhledá sestavení je adresář sestavení odkazu (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). Během tohoto kroku proces sestavení také inicializuje různé vlastnosti a skupiny položek a provede všechny potřebné vyčištění práci.  
  
<a name="Resolving_references"></a>   
### <a name="resolving-references"></a>Překládají se odkazy  
 Proces sestavení vyhledá a připojí sestavení požadovaná k vytvoření projektu aplikace. Tato logika je součástí `ResolveAssemblyReference` úloh. Všechna sestavení deklarován jako `Reference` v souboru projektu jsou k dispozici k úloze spolu s informací o vyhledávací cesty a metadat na sestavení v systému už nainstalovaná. Úloha vyhledá sestavení a používá instalované sestavení metadat k filtrování tyto základní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení, které potřebují nezobrazit nahoru v manifestech výstup. To se provádí, aby nadbytečné informace v manifesty ClickOnce. Například protože knihovně PresentationFramework.dll lze považovat za zástupce aplikace založená na a pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a navíc od všech [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení existují ve stejném umístění na každém počítači, který má rozhraní .NET Framework nainstalovaný, není nutné zahrnout všechny informace o všech odkaz na sestavení rozhraní .NET Framework v manifestech.  
  
<a name="Markup_Compilation___Pass_1"></a>   
### <a name="markup-compilationpass-1"></a>Kompilace označování – průchod 1  
 V tomto kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory jsou analyzovány a zkompilovány tak, aby modul runtime trávit čas parsování [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] a ověřením hodnoty vlastností. Zkompilovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je předem tokenizovaného tak, aby v době běhu, načtením by měl být mnohem rychlejší než načítání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.  
  
 Během tohoto kroku, provést následující aktivity místo každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, který je `Page` vytvářet položky:  
  
1.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Souboru je analyzovány pomocí kompilátoru značek.  
  
2.  Pro, který se vytvoří zkompilovanou reprezentaci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zkopírovány do složky obj\Release.  
  
3.  CodeDOM reprezentace nové částečné třídy je vytvořili a zkopírovali do složky obj\Release.  
  
 Kromě toho je vygenerován soubor specifické pro jazyk kódu pro každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Pro stránku Page1.xaml v projektu jazyka Visual Basic, například se generuje Page1.g.vb; pro stránku Page1.xaml v projektu v jazyce C# je generována Page1.g.cs. Označuje ".g" v názvu souboru, soubor je vygenerován kód, který obsahuje deklaraci částečné třídy pro element nejvyšší úrovně označovacího souboru (například `Page` nebo `Window`). Třída je deklarována s `partial` modifikátor v jazyce C# (`Extends` v jazyce Visual Basic) k označení, existuje jiný deklaraci pro třídu jinde, obvykle v modelu code-behind souboru Page1.xaml.cs.  
  
 Částečné třídy sahá od příslušné základní třídy (například <xref:System.Windows.Controls.Page> stránky) a implementuje <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> rozhraní. <xref:System.Windows.Markup.IComponentConnector> Rozhraní má metody k inicializaci součásti a propojit názvy a události na prvcích v jeho obsahu. V důsledku toho souboru generovaného kódu obsahuje implementace metody, jako je následující:  
  
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
  
 Ve výchozím nastavení, kompilace označení běží ve stejném <xref:System.AppDomain> jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] modul. Tímto způsobem významného zvýšení výkonu. Toto chování lze přepínat pomocí `AlwaysCompileMarkupFilesInSeparateDomain` vlastnost. To má výhodu uvolnění všech referenční sestavení pomocí uvolnění jako samostatná <xref:System.AppDomain>.  
  
<a name="Pass_2_of_Markup_Compilation"></a>   
### <a name="markup-compilationpass-2"></a>Kompilace označování – předání 2  
 Ne všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou stránky kompilovány při průchodu 1 kompilace označení. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které jste definovali místně odkazů na typy (odkazy na typy definované v kódu jinde ve stejném projektu) jsou vyloučení z kompilace v tuto chvíli. Je to proto, že tyto místně definované typy existují pouze ve zdroji a nebyly dosud zkompilována. Aby bylo možné určit to, analyzátor používá heuristickými metodami, které zahrnují hledá položky, jako `x:Name` v souboru označení. Po nalezení takové situaci, že se kompilace souboru označení odložit, dokud již byly zkompilovány soubory kódu, a druhý kompilace označení předat procesy tyto soubory.  
  
<a name="File_Classification"></a>   
### <a name="file-classification"></a>Klasifikace souborů  
 Výstupní soubory sestavení procesů vkládání do různých skupin prostředků založené na sestavení, které aplikace se umístí do. V typické aplikaci nelokalizované, všechny datové soubory označené jako `Resource` jsou umístěné v hlavním sestavení (spustitelné nebo knihovna). Když `UICulture` je nastavena v projektu, všechny zkompilované [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory a prostředky, které výslovně označena jako specifické pro jazyk jsou umístěny v sestavení satelitních prostředků. Kromě toho všechny jazykově neutrální prostředky jsou umístěné v hlavním sestavení. V tomto kroku do procesu sestavení, který je k určení.  
  
 `ApplicationDefinition`, `Page`, A `Resource` akce sestavení v souboru projektu se dají rozšířit o `Localizable` metadata (přípustné hodnoty jsou `true` a `false`), která určuje, zda je soubor konkrétní jazyk nebo jazykově neutrální.  
  
<a name="Core_Compilation"></a>   
### <a name="core-compilation"></a>Základní kompilace  
 Základní kompilační krok zahrnuje kompilace kódu souborů. To je orchestrované systémem logiku v souborech jazykově specifické cíle Microsoft.CSharp.targets a Microsoft.VisualBasic.targets. V případě heuristiky zjistíte, který stačí jednom průchodu kompilátoru značky a pak hlavní sestavení je generováno. Nicméně pokud jeden nebo více [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory v projektu mají odkazy na místně definované typy, pak je vygenerován soubor dočasné .dll, aby sestavení konečné aplikace mohou být vytvořeny po dokončení překontrolovat kompilace označení.  
  
<a name="Manifest_generation"></a>   
### <a name="manifest-generation"></a>Generování manifestu  
 Na konci procesu sestavení po sestavení aplikace a soubory obsahu jsou připravené [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] manifestů aplikace.  
  
 Soubor manifestu nasazení popisuje model nasazení: aktuální verze, chování aktualizací a identita vydavatele spolu s digitální podpis. Tento manifest slouží vytvořené správci, kteří zacházejí nasazení. Přípona souboru je .xbap (pro [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) a .application nainstalovaných aplikací. Nejprve závisí `HostInBrowser` vlastnosti projektu a v důsledku manifest identifikuje aplikaci jako hostované v prohlížeči.  
  
 Manifest aplikace (. soubor exe.manifest) popisuje sestavení aplikace a závislé knihovny a seznam oprávnění vyžadované aplikací. Tento soubor má být autorem aplikace pro vývojáře. Pokud chcete spustit [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] aplikace, uživatel otevře soubor manifestu nasazení vaší aplikace.  
  
 Tyto soubory manifestu se vytváří vždy pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Nainstalovaných aplikací, nejsou vytvořeny není-li `GenerateManifests` je zadána vlastnost v souboru projektu s hodnotou `true`.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Získejte dvě další oprávnění, kromě těchto oprávnění přiřazená uživateli typické internetové zóně aplikace: <xref:System.Security.Permissions.WebBrowserPermission> a <xref:System.Security.Permissions.MediaPermission>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Sestavovací systém deklaruje tato oprávnění v manifestu aplikace.  
  
<a name="Incremental_Build_Support"></a>   
## <a name="incremental-build-support"></a>Podpora přírůstkové sestavení  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Sestavovací systém poskytuje podporu pro přírůstkové sestavení. Je poměrně inteligentní o zjišťování změny značek nebo kódu a zkompiluje jenom tyto artefakty, které jsou ovlivněny změnou. Mechanismus přírůstkového sestavení používá následující soubory:  
  
-   $(*AssemblyName*) _MarkupCompiler.Cache soubor, abyste zachovali aktuální stav kompilátoru.  
  
-   $(*AssemblyName*) _MarkupCompiler.lref soubor do mezipaměti [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory s odkazy na místně definované typy.  
  
 Následuje sadu pravidel, kterými se řídí přírůstkové sestavení:  
  
-   Soubor je nejmenší jednotka, ve kterém sestavovací systém zjistí změnu. Takže pro soubor kódu nemůže určit systém sestavení, pokud se změnil typ nebo kód byl přidán. Totéž platí pro soubory projektu.  
  
-   Mechanismus přírůstkového sestavení musí být cognizant, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránku definuje třídu nebo používá jiné třídy.  
  
-   Pokud `Reference` položky přejít, a potom znovu kompilovat všechny stránky.  
  
-   Pokud se změní soubor kódu, znovu kompilovat všechny stránky s lokálně definovaný typ reference.  
  
-   Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] změny souborů:  
  
    -   Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je deklarován jako `Page` v projektu: Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] neobsahuje odkazy lokálně definovaný typ, můžete znovu zkompilovat, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plus všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s odkazy na místní; Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] má místní odkazy, znovu kompilovat všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s odkazy na místní.  
  
    -   Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je deklarován jako `ApplicationDefinition` v projektu: znovu kompilovat všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky (důvod: každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahuje odkaz na <xref:System.Windows.Application> typ, který se mohl změnit).  
  
-   Pokud soubor projektu deklaruje jako definice aplikace místo souboru kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru:  
  
    -   Zkontrolujte, zda `ApplicationClassName` změnila hodnota v souboru projektu (existuje nový typ aplikace?). Pokud ano, znovu zkompilujte celé aplikace.  
  
    -   V opačném případě znovu kompilovat všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s odkazy na místní.  
  
-   Pokud se změní soubor projektu: všechny předchozí pravidla a zjistit, co je potřeba překompilovat. Změní na následující vlastnosti trigger dokončení opětovné kompilace: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`, a `HostInBrowser`.  
  
 Následující scénáře překompilujte jsou možné:  
  
-   Celá aplikace je znovu zkompilovat.  
  
-   Pouze ty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které se mají místně definované odkazy na typ překompilují.  
  
-   Nic přepsán (Pokud se nic v projektu nezměnilo).  
  
## <a name="see-also"></a>Viz také:
- [Nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
- [Referenční dokumentace WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)
- [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
- [Prostředek, obsah a datové soubory aplikace WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
