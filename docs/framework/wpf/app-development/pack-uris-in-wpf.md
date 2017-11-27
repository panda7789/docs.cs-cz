---
title: "Sbalení URI v technologii WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05e13b8fc899b5cc6addb6d41db826f39b7528f0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="pack-uris-in-wpf"></a>Sbalení URI v technologii WPF
V [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] slouží k identifikaci a načíst soubory mnoha způsoby, včetně následujících:  
  
-   Určení [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zobrazíte při aplikaci prvním spuštění.  
  
-   Načítání obrázků.  
  
-   Navigace na stránky.  
  
-   Načítání-spustitelný soubor datových souborů.  
  
 Kromě toho [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] slouží k identifikaci a nahrajte soubory z různých umístění, včetně následujících:  
  
-   Aktuální sestavení.  
  
-   Odkazované sestavení.  
  
-   Umístění relativně k sestavení.  
  
-   Aplikace Web původu.  
  
 K zajištění konzistentní mechanismus pro identifikaci a načítání těchto typů souborů z těchto umístění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá rozšiřitelnosti služby *schéma identifikátoru URI pack*. Toto téma obsahuje přehled schéma, popisuje postup vytvoření pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro různé scénáře, popisuje absolutní a relativní [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení před znázorňující způsob použití sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obou značek a kód.  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>Schéma identifikátoru URI Pack  
 Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma používá [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) specifikace (OPC), která popisuje model pro uspořádání a určení obsahu. Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíček* je logický kontejner pro jednu nebo více logických *částí*. Tento koncept znázorňuje následující obrázek.  
  
 ![Diagram balíčku a částí](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 K identifikaci částí, specifikace OPC využívá rozšiřitelnosti RFC 2396 (identifikátory URI (Uniform Resource): Obecná syntaxe) můžete definovat sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma.  
  
 Schéma, která je zadána [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je definována předponu jeho; souborů protokolu http, ftp a jsou známé příklady. Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma používá "pack" jako jeho schéma a obsahuje dvě součásti: autority a cestu. Tady je formát pro sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 Sada: / /*autority*/*cesta*
  
 *Autority* Určuje typ balíčku, který je součástí obsažený v, zatímco *cesta* Určuje umístění součástí v rámci balíčku.  
  
 Tento koncept je zobrazená ve na následujícím obrázku:  
  
 ![Vztah mezi balíčku, autority a cestu](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 Jsou obdobou aplikací a souborů, kde aplikace (balíček) může obsahovat jeden nebo více souborů (části), včetně balíčků a částí:  
  
-   Soubory prostředků, které jsou zkompilovány do místní sestavení.  
  
-   Soubory prostředků, které jsou zkompilovány do odkazované sestavení.  
  
-   Soubory prostředků, které jsou zkompilovány do odkazující sestavení.  
  
-   Soubory obsahu.  
  
-   Lokalita počátek souborů.  
  
 Pro přístup k tyto typy souborů, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje dva autorit: aplikace: / / / a siteoforigin: / / /. Aplikace: / / / autority identifikuje datové soubory aplikace, které jsou známé při kompilaci, včetně prostředků a obsah souborů. Siteoforigin: / / / autority identifikuje lokalitu počátek souborů. Rozsah každý oprávnění je znázorněno na následujícím obrázku.  
  
 ![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  Komponenta autority sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] který body do balíčku a musí odpovídat RFC 2396. Kromě toho musí být nahrazen znakem "," znak "/" a vyhrazené znaky, jako je například "%" a "?", je nutné uvést. V tématu OPC podrobnosti.  
  
 Následující části popisují, jak vytvořit pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pomocí těchto dvou autority ve spojení s příslušné cesty k identifikaci prostředků, obsah a lokality počátek souborů.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>Identifikátory URI Pack souboru prostředků  
 Soubory prostředků, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` položky a kompilované do sestavení. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]podporuje vytváření sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] který lze použít k identifikaci soubory prostředků, které jsou buď zkompilovat do místní sestavení nebo zkompilovány do sestavení, které se odkazuje z místní sestavení.  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>Místní sestavení zdrojového souboru  
 Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] prostředku soubor, který se zkompiluje do místní sestavení používá následující autority a cesta:  
  
-   **Autorita**: aplikace: / / /.  
  
-   **Cesta**: název souboru prostředků, včetně jeho cesty relativní vůči kořenovému adresáři místní sestavení projektu složky.  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru prostředků, který se nachází v kořenové složce místní sestavení projektu.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdrojového souboru, který je umístěný v podsložce složky místní sestavení projektu.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>Soubor prostředků odkazované sestavení  
 Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] prostředku soubor, který se zkompiluje do odkazované sestavení používá následující autority a cesta:  
  
-   **Autorita**: aplikace: / / /.  
  
-   **Cesta**: název souboru prostředků, který se zkompiluje do odkazované sestavení. Cesta musí splňovat následující formát:  
  
     *AssemblyShortName*{*; Verze*] {*; PublicKey*]; součásti nebo*cesta*  
  
    -   **AssemblyShortName**: krátký název pro odkazované sestavení.  
  
    -   **; Verze** [Nepovinné]: verze odkazované sestavení, která obsahuje soubor prostředků. To se používá, pokud dva nebo více odkazovaná sestavení se stejným názvem krátké jsou načteny.  
  
    -   **; PublicKey** [Nepovinné]: veřejný klíč, který se použil k podepsání odkazované sestavení. To se používá, pokud dva nebo více odkazovaná sestavení se stejným názvem krátké jsou načteny.  
  
    -   **; součást**: Určuje, že odkazovaného sestavení odkazuje z místní sestavení.  
  
    -   **Či cestu**: název souboru prostředků, včetně jeho cesty relativní vůči kořenovému adresáři složky odkazované sestavení projektu.  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru prostředků, který se nachází v kořenové složce projektu odkazované sestavení.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdrojového souboru, který je umístěný v podsložce složky odkazované sestavení projektu.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru prostředků, který se nachází v kořenové složce odkazované, specifické pro verzi sestavení projektu složky.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Všimněte si, že sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntaxe pro soubory prostředků odkazované sestavení může být použita pouze s aplikací: / / / autoritu. Například následující není podporována v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>Identifikátory URI Pack souboru obsahu  
 Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor obsahu používá následující autority a cesta:  
  
-   **Autorita**: aplikace: / / /.  
  
-   **Cesta**: název souboru obsahu, včetně jeho cesty relativní k umístění systému souboru hlavní spustitelný soubor sestavení aplikace.  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu soubor umístěný ve stejné složce jako spustitelný soubor sestavení.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu soubor umístěný ve složce do podsložky, která je relativní vzhledem ke spustitelné sestavení aplikace.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]soubory obsahu nelze přesměrováni do. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schéma podporuje pouze navigaci na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] soubory, které jsou umístěny v lokalitě původu.  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>Lokality počátek Pack identifikátory URI  
 Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro lokalitu původu souboru používá následující autority a cesta:  
  
-   **Autorita**: siteoforigin: / / /.  
  
-   **Cesta**: název webu zdrojový soubor, včetně jeho cesty relativní k umístění, ze kterého se spuštění spustitelného souboru sestavení.  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality zdrojový soubor, uložené v umístění, ze kterého se spouští spustitelný soubor sestavení.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality zdrojový soubor, uložené v podsložku, která je relativní k umístění, ze kterého se spouští spustitelný soubor sestavení aplikace.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>Stránkovací soubory  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]soubory, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky kompilované do sestavení stejným způsobem jako soubory prostředků. V důsledku toho [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky lze identifikovat pomocí pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků.  
  
 Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které jsou běžně nakonfigurována jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky mají jednu z těchto jako kořenový element:  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>Absolutní vs. Identifikátory URI relativní Pack  
 Plně kvalifikovaný pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] obsahuje schéma, oprávnění a cestu, a bude považován za absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Jako zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy obvykle umožňují nastavit příslušné atributy s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], což zahrnuje pouze cestu.  
  
 Zvažte například následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] soubor prostředků v místním sestavení.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Sada pro relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] který odkazuje tento prostředek soubor bude následující.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Protože lokality počátek soubory nejsou přidružené sestavení, se může odkazovat pouze s absolutní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  
  
 Ve výchozím nastavení sadu relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] považuje za relativní k umístění kód nebo kód, který obsahuje odkaz na. Pokud se používá počáteční zpětné lomítko, ale relativního pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkaz se považovat za relativní vůči kořenovému adresáři aplikace. Zvažte například následující strukturu projektu.  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazující *kořenové*\SubFolder\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `Page2.xaml`  
  
 Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazující *kořenové*\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>Pack URI řešení  
 Formát pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] díky je možné, pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro různé typy souborů, které vypadají stejně. Zvažte například následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Tato sada absolutní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] může odkazovat na soubor prostředků v místním sestavení nebo soubor obsahu. Totéž platí pro následující relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/ResourceOrContentFile.xaml`  
  
 Aby bylo možné zjistit typ souboru, který sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přeloží [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků v místní sestavení a soubory obsahu pomocí heuristiky následující:  
  
1.  Probe metadata sestavení <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut, který odpovídá sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
2.  Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nenajde, cesta sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor obsahu.  
  
3.  Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nebyl nalezen, probe soubory sadu prostředků, které jsou zkompilovány do místní sestavení.  
  
4.  Pokud soubor prostředků, který odpovídá cesta sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] nenajde, cesta sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor prostředků.  
  
5.  Pokud prostředek není nalezen, interně vytvořené <xref:System.Uri> je neplatný.  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]řešení se nevztahuje na [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , naleznete na následující:  
  
-   Obsah souborů v odkazovaných sestaveních: nepodporuje tyto typy souborů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Vložené soubory v odkazovaných sestaveních: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , je identifikovat jsou jedinečné, protože obsahují název odkazovaného sestavení a `;component` příponu.  
  
-   Lokality původ souborů: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , je identifikovat jsou jedinečné, protože jsou pouze soubory, které lze identifikovat podle pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] obsahující siteoforigin: / / / autority.  
  
 Jeden zápis, který pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení umožňuje je pro kód být poněkud nezávislé na umístění prostředků a obsah souborů. Například, pokud máte soubor prostředků v místním sestavení, která je překonfigurovat tak, aby se soubor s obsahem, sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředek zůstane stejný, stejně jako kód, který používá sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>Programování s aktualizací Service Pack identifikátory URI  
 Mnoho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídy implementovat vlastnosti, které lze nastavit s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně:  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 Tyto vlastnosti můžete nastavit od značek a kódu. Tato část ukazuje základní konstrukce pro oba a poté zobrazí příklady běžné scénáře.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>Použití Pack identifikátory URI v kódu  
 Sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je určený ve značce nastavením elementu atributu balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Příklad:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Tabulka 1 ukazuje různé absolutní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.  
  
 Tabulka 1: Absolutní Pack identifikátory URI v kódu  
  
|Soubor|Absolutní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků - místní sestavení|`"pack://application:,,,/ResourceFile.xaml"`|  
|Souboru prostředků v podsložce - místní sestavení|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Soubor prostředků - odkazované sestavení|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Souboru prostředků v podsložce odkazované sestavení|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Soubor prostředků v verzí odkazované sestavení|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|Soubor obsahu|`"pack://application:,,,/ContentFile.xaml"`|  
|Obsah souboru do podsložky|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Lokality zdrojový soubor|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Lokality zdrojového souboru do podsložky|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Tabulka 2 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.  
  
 Tabulka 2: Pack relativní identifikátory URI v kódu  
  
|Soubor|Relativní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků v místním sestavení|`"/ResourceFile.xaml"`|  
|Souboru prostředků v podsložku místní sestavení|`"/Subfolder/ResourceFile.xaml"`|  
|Soubor prostředků v odkazované sestavení|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Souboru prostředků v podsložce odkazované sestavení|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Soubor obsahu|`"/ContentFile.xaml"`|  
|Obsah souboru do podsložky|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>Použití Pack identifikátory URI v kódu  
 Zadejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] v kódu po vytvoření instance <xref:System.Uri> třídy a předání sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr pro konstruktor. To je patrné z následujícího příkladu.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Ve výchozím nastavení <xref:System.Uri> třída zvažuje pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] na absolutní. V důsledku toho je vyvolána výjimka, pokud instance <xref:System.Uri> třída je vytvořena s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Naštěstí <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> přetížení z <xref:System.Uri> konstruktoru třídy přijme parametr typu <xref:System.UriKind> umožňují určit, zda sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je absolutní nebo relativní.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 Byste měli zadat jenom <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative> když jste si jisti, že zadaný pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je jeden z nich. Pokud neznáte typ sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] používané, například když uživatel zadá sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] za běhu použít <xref:System.UriKind.RelativeOrAbsolute> místo.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Tabulka 3 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabulka 3: Absolutní Pack identifikátory URI v kódu  
  
|Soubor|Absolutní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků - místní sestavení|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Souboru prostředků v podsložce - místní sestavení|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor prostředků - odkazované sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Souboru prostředků v podsložce odkazované sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor prostředků v verzí odkazované sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Soubor obsahu|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|Obsah souboru do podsložky|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Lokality zdrojový soubor|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Lokality zdrojového souboru do podsložky|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Tabulka 4 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabulka 4: Pack relativní identifikátory URI v kódu  
  
|Soubor|Relativní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Soubor prostředků - místní sestavení|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Souboru prostředků v podsložce - místní sestavení|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Soubor prostředků - odkazované sestavení|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Souboru prostředků v podsložce - odkazované sestavení|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Soubor obsahu|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|Obsah souboru do podsložky|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>Běžné scénáře URI Pack  
 V předchozích částech projednat konstruování pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] k identifikaci prostředků, obsah a lokality počátek souborů. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], tyto konstrukce se používají v mnoha různými způsoby, a následující části se věnují několik běžných použití.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Zadání uživatelského rozhraní k zobrazení při spuštění aplikace  
 <xref:System.Windows.Application.StartupUri%2A>Určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zobrazíte, když [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace spuštěna. Pro samostatné aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být v časovém období, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] můžete na stránce také určit jako počáteční uživatelského rozhraní, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Pokud aplikace je samostatná aplikace, a na stránce je definován s <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otevře <xref:System.Windows.Navigation.NavigationWindow> k hostování stránky. Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], stránka se zobrazí v prohlížeči hostitele.  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>Přejdete na stránku  
 Následující příklad ukazuje, jak přejděte na stránku.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Další informace o různých způsobech přejděte v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], najdete v části [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>Určení ikony okna  
 Následující příklad ukazuje, jak k používání identifikátoru URI k určení ikony časového období.  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Další informace naleznete v tématu <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>Načítání bitové kopie, zvuk a Video soubory  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]umožňuje aplikacím používat celou řadu typů médií, které můžete identifikovat a načíst s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak je znázorněno v následujících příkladech.  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Další informace o práci s obsahem média, najdete v části [grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Načítání slovník prostředků, a z webu původu  
 Slovnících prostředků (<xref:System.Windows.ResourceDictionary>) lze použít pro podporu aplikace motivů. Jeden způsob, jak vytvořit a spravovat motivy je vytvoření víc motivů jako slovnících prostředků, které jsou umístěny v lokalitě aplikace původu. To umožňuje motivy přidat a aktualizovat bez nutnosti rekompilace a znovu nasazovat aplikace. Tyto slovnících prostředků je možné identifikovat a načíst pomocí pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], která je uvedena v následujícím příkladu.  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Přehled motivy obsažené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], najdete v části [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Viz také  
 [Prostředek aplikace WPF, obsahu a datových souborů](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
