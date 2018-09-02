---
title: Sbalení URI v technologii WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 7addb503d0a7d4c7a4388144759e7f40264d7703
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468782"
---
# <a name="pack-uris-in-wpf"></a>Sbalení URI v technologii WPF
Ve Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] slouží k identifikaci a načíst soubory mnoha způsoby, včetně následujících:  
  
-   Zadání [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zobrazit při prvním spuštění aplikace.  
  
-   Načtení obrázků.  
  
-   Přejděte na stránky.  
  
-   Načítají se soubory dat – spustitelný soubor.  
  
 Kromě toho [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] slouží k identifikaci a nahrajte soubory z různých umístěních, včetně následujících:  
  
-   Aktuální sestavení.  
  
-   Odkazované sestavení.  
  
-   Umístění relativně k sestavení.  
  
-   Aplikace webovou stránku původu.  
  
 K zajištění konzistentní mechanismus pro identifikaci a načítání těchto typů souborů z těchto míst [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá rozšiřitelnosti aplikace *schéma URI balíku*. Toto téma obsahuje základní informace o schématu, popisuje, jak vytvořit balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro širokou škálu scénářů, tento článek popisuje absolutní a relativní [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení před zobrazením jak používat balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obou značek a kódu.  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>Schéma URI balíku  
 Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] používá schéma [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) specifikace (OPC), který popisuje model pro organizaci a identifikaci obsahu. Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíčku* je logický kontejner pro jeden nebo více logických *částí*. Tento koncept znázorňuje následující obrázek.  
  
 ![Diagram balíčku a částí](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 K identifikaci částí specifikace OPC využívá rozšiřitelnosti RFC 2396 (identifikátory URI (Uniform Resource): Obecná syntaxe) k definování sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma.  
  
 Schéma, která je zadána [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je reprezentován jeho předponu http, ftp a souboru jsou známých příkladů. Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schématu jako jeho schéma používá "balíček" a obsahuje dvě součásti: autorita a cestu. Tady je formát pro sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 balíček: / /*autority*/*cesta*
  
 *Autority* Určuje typ balíčku, který je obsažen část, zatímco *cesta* Určuje umístění části v rámci balíčku.  
  
 Tento koncept je znázorněn v následujícím obrázku:  
  
 ![Vztah mezi balíčku, autority a cestu](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 Balíčky a části jsou podobná aplikace a soubory, kde aplikace (balíček) může obsahovat jeden nebo více souborů (částí), včetně:  
  
-   Soubory prostředků, které jsou kompilovány do místní sestavení.  
  
-   Soubory prostředků, které jsou kompilovány do odkazované sestavení.  
  
-   Soubory prostředků, které jsou kompilovány do odkazující sestavení.  
  
-   Soubory obsahu.  
  
-   Lokalita zdroje souborů.  
  
 Pro přístup k tyto typy souborů, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje dva orgány: aplikace: / / / / / a siteoforigin: / / / / /. Aplikace: / / / / / autority identifikuje datové soubory aplikace, která jsou známá v době kompilace, včetně souborů prostředků a obsahu. Siteoforigin: / / / / / autority identifikuje lokality původní soubory. Rozsah každé oprávnění je znázorněno na následujícím obrázku.  
  
 ![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  Komponenta autority sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je vložený [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který odkazuje na balíček a musí odpovídat specifikaci RFC 2396. Kromě toho musí být nahrazen znakem "," znak "/" a vyhrazené znaky, jako je například "%" a "?" musí být uvozeny řídicími znaky. Zobrazit OPC podrobnosti.  
  
 Následující části popisují, jak vytvořit balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pomocí těchto dvou orgány ve spojení s příslušné cesty pro identifikaci prostředků, obsah a lokality původní soubory.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>Identifikátory URI prostředků soubor balíčku  
 Soubory prostředků, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` položek a jsou zkompilovány do sestavení. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje vytváření sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , který je možné určit soubory prostředků, které jsou kompilovány do místní sestavení nebo zkompilovány do sestavení, které se odkazuje z místní sestavení.  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>Soubor prostředků místní sestavení  
 Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředek soubor, který se zkompiluje do místní sestavení používá následující autority a cesta:  
  
-   **Autorita**: aplikace: / / / / /.  
  
-   **Cesta**: název souboru prostředků, včetně jeho cesty vzhledem ke kořenové složce místní sestavení projektu.  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který se nachází v kořenové složce místní sestavení projektu.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěný v podsložce složky místní sestavení projektu.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>Soubor prostředků odkazovaných sestavení  
 Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředek soubor, který se zkompiluje do odkazované sestavení používá následující autority a cesta:  
  
-   **Autorita**: aplikace: / / / / /.  
  
-   **Cesta**: název souboru prostředku, který se zkompiluje do odkazovaných sestavení. Cestou musí být v následujícím formátu:  
  
     *AssemblyShortName*{*; Verze*] {*; PublicKey*]; component /*cesta*  
  
    -   **AssemblyShortName**: krátký název odkazovaného sestavení.  
  
    -   **; Verze** [volitelný]: verze odkazovaného sestavení, která obsahuje soubor prostředků. To se používá, když dva nebo víc odkazovaných sestavení se stejným názvem, short jsou načteny.  
  
    -   **; PublicKey** [volitelný]: veřejný klíč, který se použil k podepsání odkazovaných sestavení. To se používá, když dva nebo víc odkazovaných sestavení se stejným názvem, short jsou načteny.  
  
    -   **; součást**: Určuje, že se z místní sestavení odkazuje sestavení, který se odkazuje.  
  
    -   **/ Cesta**: název souboru prostředků, včetně jeho cesty vzhledem ke kořenové složce projektu odkazované sestavení.  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který se nachází v kořenové složce projektu odkazované sestavení.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěný v podsložce složky odkazované sestavení projektu.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který se nachází v kořenové složce složky specifické pro verzi, odkazovaná sestavení projektu.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Všimněte si, že sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntaxe pro zdrojové soubory odkazované sestavení lze použít pouze s aplikací: / / / / / autoritu. Například následující se nepodporuje v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>Identifikátory URI souboru balíčku obsahu  
 Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor s obsahem používá následující autority a cesta:  
  
-   **Autorita**: aplikace: / / / / /.  
  
-   **Cesta**: název souboru obsahu, včetně jeho cesty relativní k umístění systému souboru hlavního spustitelného sestavení aplikace.  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu soubor umístěný ve stejné složce jako spustitelného sestavení.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor obsahu, umístěné v podsložce, která je relativní vzhledem k sestavení spustitelného souboru aplikace.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] Nelze nalézt soubory obsahu do. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schéma podporuje pouze navigaci na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] soubory, které jsou k dispozici na webovou stránku původu.  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>Lokality identifikátorů URI zdroje balíčku  
 Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ke stránce původu soubor používá následující autority a cesta:  
  
-   **Autorita**: siteoforigin: / / / / /.  
  
-   **Cesta**: název webu zdrojový soubor, včetně jeho cesty relativní k umístění, ze kterého byl spuštěn spustitelný soubor sestavení.  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality zdrojový soubor, uložené v umístění, ze kterého je spuštěn spustitelný soubor sestavení.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 Následující příklad ukazuje, pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality původu souborů uložených ve podsložky, která je relativní vzhledem k umístění, ze kterého se spustí spustitelný soubor sestavení aplikace.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>Stránkovací soubory  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky jsou zkompilovány do sestavení stejným způsobem jako soubory prostředků. V důsledku toho [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky lze identifikovat pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků.  
  
 Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které jsou běžně nakonfigurována jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky mají jeden z následujících jako jeho kořenový element:  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>Absolutní vs. Identifikátory relativních Pack URI  
 Plně kvalifikovaný pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] obsahuje schéma, oprávnění a cesty, a bude považován za absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Jako zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky obvykle umožňují nastavit příslušné atributy s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], který obsahuje pouze cestu.  
  
 Představte si třeba následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] soubor prostředků v místní sestavení.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který odkazuje na tento prostředek soubor by.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Protože lokality původu soubory nejsou přiřazeny k sestavení, se může odkazovat jenom na absolutní Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  
  
 Ve výchozím nastavení, relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se považuje za relativní k umístění značek nebo kódu, který obsahuje odkaz na. Pokud se používá počáteční zpětné lomítko, ale relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkaz se považovat za kořeni aplikace. Zvažte například následující strukturu projektu.  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , která odkazuje na *kořenové*\SubFolder\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `Page2.xaml`  
  
 Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , která odkazuje na *kořenové*\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>Identifikátor URI rozlišení Pack  
 Formát balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] umožňuje pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro různé typy souborů, které vypadají stejně. Představte si třeba následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Tento balíček absolutní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] může odkazovat na soubor prostředků v místní sestavení nebo souboru obsahu. Totéž platí pro následující relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/ResourceOrContentFile.xaml`  
  
 Aby bylo možné určit typ souboru, který sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] řeší [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků v místní sestavení a soubory obsahu pomocí heuristiky následující:  
  
1.  Metadata sestavení testu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut, který odpovídá této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
2.  Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nenajde, cesta balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor s obsahem.  
  
3.  Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nebyl nalezen, testovat soubory sady prostředků, které jsou kompilovány do místní sestavení.  
  
4.  Pokud soubor prostředků, která odpovídá cestu sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je najít cestu balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor prostředků.  
  
5.  Pokud se prostředek nenajde, interně vytvořené <xref:System.Uri> je neplatný.  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení se nedá použít pro [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které odkazují na následující:  
  
-   Obsah souborů v odkazovaných sestaveních: Služba nepodporuje tyto typy souborů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Vložené soubory v odkazovaných sestaveních: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] poznají, která jsou jedinečná, vzhledem k tomu, aby obsahovaly název odkazovaného sestavení a `;component` příponu.  
  
-   Lokality původu souborů: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] poznají, které byly jedinečné, protože jsou pouze soubory, které lze identifikovat podle sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které obsahují siteoforigin: / / / / / autority.  
  
 Jeden zápis, který pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení umožňuje, je pro kód je poněkud nezávislé na umístění prostředků a obsahu souborů. Například, pokud máte soubor prostředků v místním sestavení, které je překonfigurovat tak, aby se soubor s obsahem, sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředku zůstala stejná, stejně jako kód, který používá sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>Programování s identifikátory Pack URI  
 Mnoho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídy implementovat vlastnosti, které lze nastavit s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně:  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 Tyto vlastnosti můžete nastavit od značek a kódu. Tato část ukazuje základní konstrukce pro oba a potom jsou uvedeny příklady běžným scénářům.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>Pomocí identifikátory Pack URI v kódu  
 Aktualizací Service pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je zadán v kódu tak, že nastavíte elementu atributu s balíčkem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Příklad:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Tabulka 1 znázorňuje různé absolutní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.  
  
 Tabulka 1: Absolutní Pack identifikátory URI v kódu  
  
|Soubor|Absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků – místní sestavení|`"pack://application:,,,/ResourceFile.xaml"`|  
|Soubor prostředků v podsložce – místní sestavení|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Soubor prostředků – odkazovaného sestavení|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Soubor prostředků v podsložce odkazovaného sestavení|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Soubor prostředků v verze odkazovaného sestavení|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|Soubor s obsahem|`"pack://application:,,,/ContentFile.xaml"`|  
|Obsah souboru do podsložky|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Lokality zdrojový soubor|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Lokality zdrojový soubor v podsložce|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Tabulka 2 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.  
  
 Tabulka 2: Pack relativní identifikátory URI v kódu  
  
|Soubor|Relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků v místní sestavení|`"/ResourceFile.xaml"`|  
|Soubor prostředků v podsložce místní sestavení|`"/Subfolder/ResourceFile.xaml"`|  
|Soubor prostředků v odkazovaném sestavení|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Soubor prostředků v podsložce odkazovaného sestavení|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Soubor s obsahem|`"/ContentFile.xaml"`|  
|Obsah souboru do podsložky|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>Použití identifikátory Pack URI v kódu  
 Zadejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] v kódu po vytvoření instance <xref:System.Uri> třídy a předáním této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr do konstruktoru. To je patrné z následujícího příkladu.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Ve výchozím nastavení <xref:System.Uri> třídy bere v úvahu pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] být absolutní. V důsledku toho je vyvolána výjimka, pokud instance <xref:System.Uri> třída se vytvoří s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Naštěstí <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> přetížení <xref:System.Uri> konstruktoru třídy přijímá parametr typu <xref:System.UriKind> aby bylo možné určit, zda sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je absolutní nebo relativní.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 Měli byste zadat jenom <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative> když jste si jisti, že zadaný balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je jeden z nich. Pokud neznáte typ sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který se používá, například když uživatel zadá sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] v době běhu použít <xref:System.UriKind.RelativeOrAbsolute> místo.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Tabulka 3 znázorňuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu s použitím <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabulka 3: Absolutní Pack identifikátory URI v kódu  
  
|Soubor|Absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků – místní sestavení|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor prostředků v podsložce – místní sestavení|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor prostředků – odkazovaného sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor prostředků v podsložce odkazovaného sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor prostředků v verze odkazovaného sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor s obsahem|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|Obsah souboru do podsložky|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Lokality zdrojový soubor|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Lokality zdrojový soubor v podsložce|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Tabulka 4 znázorňuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabulka 4: Pack relativní identifikátory URI v kódu  
  
|Soubor|Relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků – místní sestavení|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Soubor prostředků v podsložce – místní sestavení|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Soubor prostředků – odkazovaného sestavení|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Soubor prostředků v podsložce - odkazovaného sestavení|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Soubor s obsahem|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|Obsah souboru do podsložky|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>Běžné scénáře identifikátoru URI balíčku  
 V předchozích částech projednat tom, jak vytvořit balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro identifikaci prostředků, obsah a lokality původní soubory. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], tyto konstrukce se používají v mnoha různými způsoby, a následující části se věnují několika běžných použití.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Určení uživatelské rozhraní k zobrazení při spuštění aplikace  
 <xref:System.Windows.Application.StartupUri%2A> Určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zobrazíte, když [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spuštění aplikace. Pro samostatné aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být okno, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] můžete také určit stránku jako počáteční uživatelského rozhraní, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Pokud aplikace je samostatná aplikace, a stránka není zadán s <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otevře <xref:System.Windows.Navigation.NavigationWindow> hostovat na stránce. Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], stránka se zobrazí v prohlížeči hostitele.  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>Přejděte na stránku  
 Následující příklad ukazuje, jak přejít na stránku.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Další informace o různých způsobů, jak procházet v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], naleznete v tématu [Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>Určení ikonu okna.  
 Následující příklad ukazuje, jak pomocí identifikátoru URI můžete určit ikonu okna.  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Další informace naleznete v tématu <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>Načítají se obrázek, zvuk a Video soubory  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje aplikacím používat celou řadu typů médií, které můžete identifikovat a načítají s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Další informace o práci s mediálního obsahu, najdete v části [grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Načítání z umístění původních slovník prostředků  
 Slovníky sloučených prostředků (<xref:System.Windows.ResourceDictionary>) lze použít pro podporu motivů aplikace. Jeden způsob, jak vytvářet a spravovat motivy, je vytvořit víc motivů jako slovníky prostředků, které jsou umístěné v lokalitě aplikace původu. To umožňuje motivy, které chcete přidat a aktualizovat bez nutnosti opětovné kompilace a opětovné nasazení aplikace. Tyto slovníky prostředků je možné identifikovat a načíst pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], která je uvedena v následujícím příkladu.  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Přehled motivy obsažené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], naleznete v tématu [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Viz také  
 [Prostředek, obsah a datové soubory aplikace WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
