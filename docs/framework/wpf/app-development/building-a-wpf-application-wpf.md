---
title: "Sestavení aplikace WPF (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87fc77aaa95e2d2de4b0c6eb75484ab9b4006c31
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="building-a-wpf-application-wpf"></a>Sestavení aplikace WPF (WPF)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]aplikace se dají vytvářet jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] spustitelné soubory (.exe) knihovny (DLL) nebo kombinaci obou typů sestavení. Toto téma představuje jak sestavit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace a popisuje klíčové kroky v procesu sestavení.  
  
  
<a name="Building_a_WPF_Application_using_Command_Line"></a>   
## <a name="building-a-wpf-application"></a>Sestavení aplikace WPF  
 Aplikace WPF mohou být zkompilovány následujícími způsoby:  
  
-   Příkazového řádku. Aplikace musí obsahovat jenom kód (žádné XAML) a soubor definice aplikace. Další informace najdete v tématu [sestavení příkazového řádku s csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
-   Microsoft Build Engine (MSBuild). Kromě kódu a soubory XAML musí aplikace obsahovat soubor projektu nástroje MSBuild. Další informace najdete v tématu "MSBuild".  
  
-   Visual Studio. Visual Studio se integrované vývojové prostředí, které zkompiluje grafického subsystému WPF aplikace pomocí nástroje MSBuild a zahrnuje vizuálního návrháře pro vytvoření uživatelského rozhraní. Další informace najdete v tématu [vývoj aplikací v sadě Visual Studio](http://msdn.microsoft.com/library/97490c1b-a247-41fb-8f2c-bc4c201eff68) a [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).  
  
<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>   
## <a name="wpf-build-pipeline"></a>Kanál sestavení WPF  
 Když [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení projektu, kombinace jazyka a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]-jsou vyvolány určité cíle. Provádění těchto cílů proces se nazývá kanálu sestavení a jsou klíčové kroky vidíte na následujícím obrázku.  
  
 ![Proces sestavení WPF](../../../../docs/framework/wpf/app-development/media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")  
  
<a name="Pre_Build_Initializations"></a>   
### <a name="pre-build-initializations"></a>Před sestavením Inicializacích  
 Před vytvořením, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] Určuje umístění důležité nástroje a knihovny, včetně následujících:  
  
-   [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)].  
  
-   [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Adresáře.  
  
-   Umístění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] referenční sestavení.  
  
-   Vlastnost cesty pro hledání sestavení.  
  
 První umístění kde [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] vyhledá sestavení je adresář odkazů na sestavení (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). V tomto kroku procesu sestavení také inicializuje různé vlastnosti a skupiny položek a provádí veškerou práci, vyžaduje čištění.  
  
<a name="Resolving_references"></a>   
### <a name="resolving-references"></a>Řešení odkazů  
 Proces sestavení vyhledá a sváže sestavení požadovaná pro sestavení projektu aplikace. Tato logika je součástí `ResolveAssemblyReference` úloh. Ve všech sestaveních deklarován jako `Reference` v souboru projektu, které jsou uvedeny úlohy spolu s informace o cesty pro hledání a metadata sestavení, které jsou již v systému nainstalována. Úloha vyhledá sestavení a používá metadata nainstalované sestavení filtrovat tyto základní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení, které potřebují není zobrazit nahoru v manifestech výstup. Děje se tak aby se zabránilo redundantní informace v manifestech ClickOnce. Například vzhledem k tomu, že knihovně PresentationFramework.dll lze považovat za zástupce aplikace vytvořené a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a kromě toho od všech [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení existovat ve stejném umístění na každý počítač, který má [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] nainstalovaná, není nutné zahrnout všechny informace o všech [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] referenční sestavení v manifestech.  
  
<a name="Markup_Compilation___Pass_1"></a>   
### <a name="markup-compilationpass-1"></a>Značky kompilace – předat 1  
 V tomto kroku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory jsou analyzovat a zkompilovat tak, aby modul runtime trávit, analýza čas [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] a ověření hodnot vlastností. Zkompilovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je před tokenizovaného tak, aby v době běhu, načte by měla být mnohem rychlejší než načítání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.  
  
 V tomto kroku tyto činnosti provést každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, který je `Page` sestavení položky:  
  
1.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Souboru je analyzována kompilátorem značek.  
  
2.  Znázornění kompilované se vytvoří pro tento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zkopírovali do složky obj\Release.  
  
3.  Znázornění CodeDOM nové částečné třídy je vytvořili a zkopírovali do složky obj\Release.  
  
 Kromě toho se vygeneruje soubor specifické pro jazyk kódu pro každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Například pro stránky Page1.xaml v [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)] projektu Page1.g.vb se vygeneruje; Page1.xaml stránce v [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] projekt, Page1.g.cs se vygeneruje. ".G" v názvu souboru označuje soubor je vygenerováno, kód, který má deklaraci třídu pro element nejvyšší úrovně souboru kódu (například `Page` nebo `Window`). Třída je deklarovaný s `partial` modifikátor v [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] (`Extends` v [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)]) k označení, je jiná deklarace pro třídu jinam, obvykle v modelu code-behind souboru Page1.xaml.cs.  
  
 Rozšiřuje třídu z příslušné základní třídy (například <xref:System.Windows.Controls.Page> pro stránku) a implementuje <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> rozhraní. <xref:System.Windows.Markup.IComponentConnector> Rozhraní má metody pro inicializaci součásti a připojit názvy a události na elementy v jeho obsah. V důsledku toho soubor generovaného kódu má implementace metody takto:  
  
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
  
 Ve výchozím nastavení spouští kompilace kódu ve stejné <xref:System.AppDomain> jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] modul. To poskytuje výrazné zvýšení výkonu. Můžou být toto chování se `AlwaysCompileMarkupFilesInSeparateDomain` vlastnost. To nabízí výhodu v podobě uvolnění všechny referenční sestavení pomocí uvolnění samostatné <xref:System.AppDomain>.  
  
<a name="Pass_2_of_Markup_Compilation"></a>   
### <a name="markup-compilationpass-2"></a>Značky kompilace – předat 2  
 Ne všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou stránky kompilovány na během průchodu 1 kompilace kódu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]soubory, které jste definovali místně odkazy na typ (odkazů pro typy definované v kódu jinde v rámci jednoho projektu) se nevztahují kompilace v tuto chvíli. Je to proto, že tyto místně definované typy existovat pouze ve zdroji a nebyla dosud kompilována. Chcete-li to zjistit, analyzátor používá heuristiky, které zahrnují hledá položky, jako například `x:Name` v souboru kódu. Pokud tyto instance nenajde, že dokud soubory kódu sestavili jsme, po který, odloží se kompilace kódu souboru druhý kompilace kódu předat procesy tyto soubory.  
  
<a name="File_Classification"></a>   
### <a name="file-classification"></a>Klasifikace souborů  
 Proces sestavení PUT výstupní soubory do jiné skupiny prostředků založené na sestavení, které aplikace se bude uložena v umístění. V typické aplikaci nelokalizované, všechny datové soubory označen jako `Resource` jsou umístěny v hlavní sestavení (spustitelný soubor nebo knihovna). Když `UICulture` je nastavena v projektu, všechny kompilované [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory a tyto prostředky konkrétně označené jako konkrétní jazyk, které jsou umístěny v satelitní sestavení prostředků. Kromě toho všechny jazykově neutrální prostředky jsou umístěny v hlavní sestavení. V tomto kroku procesu sestavení, která byla zjištěna.  
  
 `ApplicationDefinition`, `Page`, A `Resource` akce sestavení v souboru projektu se dají rozšířit o `Localizable` metadata (přijatelné hodnoty jsou `true` a `false`), která určuje, zda se soubor nachází konkrétní jazyk nebo jazykově neutrální.  
  
<a name="Core_Compilation"></a>   
### <a name="core-compilation"></a>Základní kompilace  
 Základní kompilační krok zahrnuje kompilace kódu souborů. To je řízená logiku v souborech cíle pro specifický jazyk Microsoft.CSharp.targets a Microsoft.VisualBasic.targets. V případě heuristiky zjistíte, které stačí jednom průchodu kompilátoru značek a potom se vygeneruje hlavní sestavení. Ale pokud jeden nebo více [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory v projektu obsahují odkazy na místně definované typy a pak soubor .dll dočasné se vygeneruje, takže sestavení konečné aplikace mohou být vytvořeny po dokončení druhé fázi kompilace kódu.  
  
<a name="Manifest_generation"></a>   
### <a name="manifest-generation"></a>Generování manifestu  
 Na konci procesu sestavení po sestavení aplikace a soubory obsahu jsou připravené [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] manifestů aplikace jsou generovány.  
  
 Soubor manifestu nasazení popisuje model nasazení: aktuální verze, chování aktualizací a identity vydavatele společně s digitální podpis. Tento manifest se má být vytvořené správci, kteří obsluhují nasazení. Přípona souboru je .xbap (pro [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) a .application nainstalovaných aplikací. Bývalé závisí `HostInBrowser` vlastností projektu a v důsledku manifest identifikuje aplikaci jako hostované prohlížečem.  
  
 Manifest aplikace (..exe soubor) popisuje sestavení aplikace a závislé knihovny a uvádí oprávnění požadované aplikací. Tento soubor má být autorem vývojáře aplikace. Aby bylo možné spustit [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] aplikace, uživatel otevře soubor manifestu nasazení aplikace.  
  
 Tyto soubory manifestu se vytváří vždy pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Nainstalovaných aplikací, nejsou vytvořeny Pokud `GenerateManifests` vlastnost je zadaná v souboru projektu s hodnotou `true`.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Získejte dva další oprávnění, kromě těchto oprávnění přiřazená uživateli typické internetové zóny aplikace: <xref:System.Security.Permissions.WebBrowserPermission> a <xref:System.Security.Permissions.MediaPermission>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Systém sestavení deklaruje tato oprávnění v manifestu aplikace.  
  
<a name="Incremental_Build_Support"></a>   
## <a name="incremental-build-support"></a>Podpora přírůstkové sestavení  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Systém sestavení poskytuje podporu pro přírůstkové sestavení. Je docela inteligentního o zjišťování změny kód a kompilaci pouze tyto artefakty vliv změn. Tento mechanismus přírůstkové sestavení používá následující soubory:  
  
-   $(*AssemblyName*) _MarkupCompiler.Cache soubor, abyste zachovali aktuální stav kompilátoru.  
  
-   $(*AssemblyName*) _MarkupCompiler.lref soubor do mezipaměti [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory s odkazy na místně definované typy.  
  
 Toto je sada pravidel pro přírůstkové sestavení:  
  
-   Soubor je nejmenší jednotka, kde systém sestavení zjistí změnu. Pro soubor kód nelze tedy systém sestavení zjistit, pokud byl změněn typu nebo pokud jste přidali kód. To platí i pro soubory projektu.  
  
-   Tento mechanismus přírůstkové sestavení musí být cognizant, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky definuje třídu nebo používá jiné třídy.  
  
-   Pokud `Reference` položky přejít, a potom znovu zkompiluje všechny stránky.  
  
-   Pokud se změní soubor kódu, znovu zkompiluje všechny stránky s odkazy na typ místně definované.  
  
-   Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru změny:  
  
    -   Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je deklarován jako `Page` v projektu: Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá odkazy na místně definovaný typ, který znovu zkompiluje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plus všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místní odkazy; Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] má místní odkazy, znovu zkompiluje všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místní odkazy.  
  
    -   Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je deklarován jako `ApplicationDefinition` v projektu: znovu zkompiluje všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky (důvod: každý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahuje odkaz na <xref:System.Windows.Application> typ, který možná změnil).  
  
-   Pokud soubor projektu deklaruje jako definice aplikace místo souboru kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru:  
  
    -   Zkontrolujte, zda `ApplicationClassName` došlo ke změně hodnoty v souboru projektu (existuje nový typ aplikace?). Pokud ano, znovu zkompiluje celý aplikace.  
  
    -   Jinak, znovu zkompiluje všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky s místní odkazy.  
  
-   Pokud se změní soubor projektu: všechny předchozí pravidla použít a zjistit, co musí zopakovat. Změní na následující vlastnosti aktivační události dokončení nové kompilace: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace`, a `HostInBrowser`.  
  
 Následující scénáře pak ji znovu zkompilovat jsou možné:  
  
-   Znovu zkompiluje celý aplikace.  
  
-   Pouze ty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou soubory, které jste definovali místně odkazy na typ zopakovat.  
  
-   Nic znovu zkompiluje (Pokud se změnila nic v projektu).  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [Referenční dokumentace WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Prostředek, obsah a datové soubory aplikace WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
