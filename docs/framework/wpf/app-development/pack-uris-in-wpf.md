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
ms.openlocfilehash: f9ea4acfc7ba86d3424bb11af0de685651f99c61
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796752"
---
# <a name="pack-uris-in-wpf"></a>Sbalení URI v technologii WPF

V Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] slouží k identifikaci a načítání souborů v mnoha ohledech, včetně následujících:

- Určení, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] které se má zobrazit při prvním spuštění aplikace

- Načítají se obrázky.

- Navigace na stránky.

- Načítání nespustitelných datových souborů.

Kromě toho [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] je možné použít k identifikaci a načítání souborů z nejrůznějších umístění, včetně následujících:

- Aktuální sestavení.

- Odkazované sestavení.

- Umístění relativní k sestavení

- Původní lokalita aplikace.

Pro zajištění konzistentního mechanismu pro identifikaci a načítání těchto typů souborů z těchto umístění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá rozšíření *schématu identifikátoru URI*. Toto téma obsahuje přehled schématu, popisuje [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , jak vytvořit balíček pro celou řadu scénářů, popisuje absolutní a relativní [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozlišení před zobrazením způsobu použití balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obou značek. a kód.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Schéma identifikátoru URI balíčku

Schéma balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se používá ve specifikaci OPC ( [Open balící konvence](https://go.microsoft.com/fwlink/?LinkID=71255) ), která popisuje model pro organizování a identifikaci obsahu. Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíček* je logický kontejner pro jednu nebo více logických *částí*. Tento koncept znázorňuje následující obrázek.

![Diagram balíčků a částí](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

K identifikaci částí OPC Specification využívá rozšiřitelnost RFC 2396 (Uniform resource identifiers (URI): Obecná syntaxe) pro definování schématu balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] .

Schéma, které je určeno parametrem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , je definováno jeho předponou. mezi známé příklady jsou http, FTP a File. Schéma balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] používá jako své schéma "sadu" a obsahuje dvě komponenty: autorita a cesta. Následuje formát balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

*cesta* k*autoritě*/Pack://

*Autorita* určuje typ balíčku, který součást obsahuje, zatímco *cesta* určuje umístění součásti v rámci balíčku.

Tento koncept je znázorněný na následujícím obrázku:

![Vztah mezi balíčkem, autoritou a cestou](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Balíčky a části jsou analogické pro aplikace a soubory, kde aplikace (balíček) může obsahovat jeden nebo více souborů (částí), včetně:

- Soubory prostředků, které jsou zkompilovány do místního sestavení.

- Soubory prostředků, které jsou zkompilovány do odkazovaného sestavení.

- Soubory prostředků, které jsou zkompilovány do odkazujícího sestavení.

- Soubory obsahu.

- Lokalita se zdrojovými soubory.

Pro přístup k těmto typům souborů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje dva autority: Application:///a siteoforigin:///. Autorita application:///identifikuje datové soubory aplikace, které jsou známy v době kompilace, včetně souborů prostředků a obsahu. Autorita siteoforigin:///identifikuje web se zdrojovými soubory. Rozsah jednotlivých autorit je znázorněn na následujícím obrázku.

![Diagram identifikátoru URI balíčku](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Součást [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] autority balíčku je vložená [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , která odkazuje na balíček a musí odpovídat specifikaci RFC 2396. Kromě toho musí být znak "/" nahrazen znakem "," a vyhrazené znaky, například "%" a "?" musí být uvozeny řídicím znakem. Podrobnosti najdete v OPC.

V následujících částech se dozvíte, jak [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] sestavit sadu pomocí těchto dvou úřadů ve spojení s příslušnými cestami k určení prostředků, obsahu a umístění souborů původu.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>Identifikátory URI sad prostředků souboru

Soubory prostředků jsou konfigurovány [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] jako `Resource` položky a zkompilovány do sestavení. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]podporuje konstrukci balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , který lze použít k identifikaci souborů prostředků, které jsou zkompilovány do místního sestavení nebo zkompilovány do sestavení, které je odkazováno z místního sestavení.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Soubor prostředků místního sestavení

Balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor prostředků kompilovaný do místního sestavení používá následující autoritu a cestu:

- **Autorita**: Application:///.

- **Cesta**: Název souboru prostředků, včetně jeho cesty, vzhledem k kořenovému adresáři složky projektu místní sestavení.

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro soubor prostředků, který je umístěn v kořenovém adresáři složky projektu místního sestavení.

`pack://application:,,,/ResourceFile.xaml`

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro soubor prostředků, který je umístěn v podsložce složky projektu místního sestavení.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Odkazovaný soubor prostředků sestavení

Balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor prostředků kompilovaný do odkazovaného sestavení používá následující autoritu a cestu:

- **Autorita**: Application:///.

- **Cesta**: Název souboru prostředků, který je zkompilován do odkazovaného sestavení. Cesta musí odpovídat následujícímu formátu:

  *AssemblyShortName* { *; Verze*] { *; PublicKey*]; součást/*cesta*

  - **AssemblyShortName**: krátký název odkazovaného sestavení.

  - **; Verze** [volitelné]: verze odkazovaného sestavení, které obsahuje soubor prostředků. To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.

  - **; PublicKey** [volitelné]: veřejný klíč, který se použil k podepsání odkazovaného sestavení. To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.

  - **; Component**: Určuje, zda je na odkazované sestavení odkazováno z místního sestavení.

  - **/Path**: název souboru prostředků, včetně jeho cesty, vzhledem k kořenu složky projektu odkazovaného sestavení.

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro soubor prostředků, který je umístěn v kořenovém adresáři složky projektu odkazovaného sestavení.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro soubor prostředků, který je umístěn v podsložce složky projektu odkazovaného sestavení.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro soubor prostředků, který je umístěn v kořenové složce odkazovaného projektu složky sestavení pro konkrétní verzi.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Všimněte si, že [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntaxe balíčku pro odkazované soubory prostředků sestavení se dá použít jenom s autoritou Application:///. Následující příklad není podporován v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroji.

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>Identifikátory URI sady souborů obsahu

Balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor obsahu používá následující autoritu a cestu:

- **Autorita**: Application:///.

- **Cesta**: Název souboru obsahu, včetně jeho cesty vzhledem k umístění systému souborů v hlavním spustitelném sestavení aplikace.

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro soubor obsahu umístěný ve stejné složce jako spustitelné sestavení.

`pack://application:,,,/ContentFile.xaml`

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro soubor obsahu umístěný v podsložce, která je relativní vzhledem ke spustitelnému sestavení aplikace.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> Soubory obsahu HTML nelze přejít na. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schéma podporuje pouze navigaci na soubory HTML, které jsou umístěny v lokalitě původu.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>Server sad identifikátorů URI pro původní sadu

Balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro lokalitu zdrojového souboru používá následující autoritu a cestu:

- **Autorita**: siteoforigin:///.

- **Cesta**: Název lokality zdrojového souboru, včetně cesty vzhledem k umístění, ze kterého bylo spuštěno spustitelné sestavení.

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro lokalitu zdrojového souboru, uložený v umístění, ze kterého se spouští spustitelné sestavení.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

Následující příklad ukazuje balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro lokalitu zdrojového souboru, uložený v podsložce, která je relativní k umístění, ze kterého se spouští sestavení spustitelného objektu aplikace.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Stránkovací soubory

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]soubory, které jsou konfigurovány jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky, jsou zkompilovány do sestavení stejným způsobem jako soubory prostředků. V důsledku toho mohou být [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] položkyidentifikoványpomocíbalíčkuprosouboryprostředků.`Page` [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]

Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů, které jsou běžně konfigurovány jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky, mají jeden z následujících prvků jako svůj kořenový prvek:

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>Absolutní vs. Identifikátory URI relativního balíčku

Plně kvalifikovaná sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zahrnuje schéma, autoritu a cestu a je považována za absolutní sadu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] V rámci zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky obvykle umožňují nastavit odpovídající atributy s relativním balíčkem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], který obsahuje pouze cestu.

Zvažte například následující absolutní balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor prostředků v místním sestavení.

`pack://application:,,,/ResourceFile.xaml`

Relativní balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který odkazuje na tento soubor prostředků, by byl následující.

`/ResourceFile.xaml`

> [!NOTE]
> Vzhledem k tomu, že lokalita původních souborů není přidružena k sestavením, mohou být pouze odkazována pouze s absolutním balíčkem [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].

Ve výchozím nastavení je relativní balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] považován za relativní k umístění značky nebo kódu, který obsahuje odkaz. Je-li použito počáteční zpětné lomítko, je však odkaz na [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relativní sadu považován za relativní ke kořenu aplikace. Zvažte například následující strukturu projektu.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Pokud Page1. XAML obsahuje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkaz, který odkazuje na *kořenový*\SubFolder\Page2.XAML, může odkaz použít následující relativní sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`Page2.xaml`

Pokud Page1. XAML obsahuje [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkaz, který odkazuje na *kořenový*\Page2.XAML, může odkaz použít následující relativní sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Rozlišení URI balíčku

Formát balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] umožňuje, aby balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro různé typy souborů vypadal stejně. Zvažte například následující absolutní sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`pack://application:,,,/ResourceOrContentFile.xaml`

Tento absolutní balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] může odkazovat buď na soubor prostředků v místním sestavení, nebo v souboru obsahu. Totéž platí pro následující relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`/ResourceOrContentFile.xaml`

Aby bylo možné určit typ souboru, na který balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] řeší [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] soubory prostředků v místních sestaveních a souborech obsahu pomocí následujících heuristik:

1. Sondujte metadata sestavení pro <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut, který odpovídá balíčku. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

2. Pokud je [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] atribut nalezen, cesta k balíčku odkazuje na soubor obsahu. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>

3. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Pokud atribut nebyl nalezen, proveďte test souborů prostředků sady, které jsou zkompilovány do místního sestavení.

4. Pokud je nalezen soubor prostředků, který odpovídá cestě k balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , cesta k balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor prostředků.

5. Pokud se prostředek nenajde, interně vytvořené <xref:System.Uri> pole je neplatné.

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]řešení [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které se nevztahuje na tyto informace:

- Soubory obsahu v odkazovaných sestaveních: tyto typy souborů nejsou podporovány [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástrojem.

- Vložené soubory v odkazovaných sestaveních: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] které identifikují jsou jedinečné, protože zahrnují název odkazovaného sestavení `;component` a příponu.

- Lokalita se zdrojovými [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] soubory: které identifikují jsou jedinečné, protože se jedná o jediné soubory, které je [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] možné identifikovat pomocí balíčku, který obsahuje autoritu siteoforigin:///.

Jedno zjednodušení, které [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] umožňuje rozlišení balíčku, je, že kód může být trochu nezávislý na umístění souborů prostředků a obsahu. Například pokud máte soubor prostředků v lokálním sestavení, které je překonfigurováno na soubor obsahu, zůstane balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředek stejný, jako kód, který používá sadu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Programování s identifikátory URI balíčku

Mnoho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tříd implementuje vlastnosti, které lze nastavit pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně:

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Tyto vlastnosti lze nastavit z kódu i kódu. Tato část ukazuje základní konstrukce pro obojí a pak ukazuje příklady běžných scénářů.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Použití identifikátorů URI Pack v kódu

Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je určena v označení pomocí nastavení elementu atributu s balíčkem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Příklad:

`<element attribute="pack://application:,,,/File.xaml" />`

Tabulka 1 znázorňuje různé absolutní balíky [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které lze zadat v označení.

Tabulka 1: Absolutní identifikátory URI Pack v kódu

|Soubor|Absolutní sada[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Místní sestavení souboru prostředků|`"pack://application:,,,/ResourceFile.xaml"`|
|Soubor prostředků v sestavení místních podsložek|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|Soubor prostředků – odkazované sestavení|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|Soubor prostředků v podsložce odkazovaného sestavení|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Soubor prostředků ve verzi odkazovaného sestavení|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|Soubor obsahu|`"pack://application:,,,/ContentFile.xaml"`|
|Soubor obsahu v podsložce|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|Lokalita zdrojového souboru|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|Lokalita zdrojového souboru v podsložce|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

Tabulka 2 znázorňuje různé relativní sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které lze zadat v označení.

Tabulka 2: Identifikátory URI relativních balíčků v kódu

|Soubor|Relativní balíček[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Soubor prostředků v místním sestavení|`"/ResourceFile.xaml"`|
|Soubor prostředků v podsložce místního sestavení|`"/Subfolder/ResourceFile.xaml"`|
|Soubor prostředků v odkazovaném sestavení|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Soubor prostředků v podsložce odkazovaného sestavení|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Soubor obsahu|`"/ContentFile.xaml"`|
|Soubor obsahu v podsložce|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Použití identifikátorů URI Pack v kódu

Zadáte balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] v kódu vytvořením instance <xref:System.Uri> třídy a předáním balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametru do konstruktoru. To je patrné z následujícího příkladu.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Ve výchozím nastavení <xref:System.Uri> třída považuje balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] za absolutní. V důsledku toho je vyvolána výjimka, když je vytvořena instance <xref:System.Uri> třídy s relativním balíčkem. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

```csharp
Uri uri = new Uri("/File.xaml");
```

Naštěstí přetížení konstruktoru třídy přijímá parametr typu <xref:System.UriKind> , který umožňuje určit, zda je balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] buď absolutní, nebo relativní. <xref:System.Uri> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Měli byste zadat jenom <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative> , pokud jste si jisti, že zadaný [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Pack je jeden nebo druhý. Pokud nevíte, který typ balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se používá, například když uživatel zadá do balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] za běhu, použijte <xref:System.UriKind.RelativeOrAbsolute> místo toho.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Tabulka 3 znázorňuje různé relativní sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které lze zadat v kódu pomocí. <xref:System.Uri?displayProperty=nameWithType>

Tabulka 3: Absolutní identifikátory URI Pack v kódu

|Soubor|Absolutní sada[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Místní sestavení souboru prostředků|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|Soubor prostředků v sestavení místních podsložek|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Soubor prostředků – odkazované sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|Soubor prostředků v podsložce odkazovaného sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Soubor prostředků ve verzi odkazovaného sestavení|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|Soubor obsahu|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|Soubor obsahu v podsložce|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|Lokalita zdrojového souboru|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|Lokalita zdrojového souboru v podsložce|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

Tabulka 4 znázorňuje různé relativní sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , které lze zadat v kódu pomocí. <xref:System.Uri?displayProperty=nameWithType>

Tabulka 4: Identifikátory URI relativních balíčků v kódu

|Soubor|Relativní balíček[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Místní sestavení souboru prostředků|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Soubor prostředků v sestavení místních podsložek|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Soubor prostředků – odkazované sestavení|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Soubor prostředků v sestavení odkazovaném podsložkou|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Soubor obsahu|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Soubor obsahu v podsložce|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Scénáře identifikátoru URI pro Common Pack

V předchozích částech jsme probrali postup sestavení [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] balíčku k identifikaci prostředků, obsahu a umístění původních souborů. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroji se tyto konstrukce používají v různých způsobech a následující oddíly obsahují několik běžných použití.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Určení uživatelského rozhraní, které se zobrazí při spuštění aplikace

<xref:System.Windows.Application.StartupUri%2A>Určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který se má zobrazit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] při spuštění aplikace. Pro samostatné aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být okno, jak je znázorněno v následujícím příkladu.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] také můžete určit stránku jako počáteční uživatelské rozhraní, jak je znázorněno v následujícím příkladu.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Pokud se jedná o samostatnou aplikaci a je určena Stránka s nástrojem <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace otevře <xref:System.Windows.Navigation.NavigationWindow> a bude hostovat stránku. [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]V případě se stránka zobrazuje v prohlížeči hostitele.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Navigace na stránku

Následující příklad ukazuje, jak přejít na stránku.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Další informace o různých způsobech navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroji najdete v tématu [Přehled navigace](navigation-overview.md).

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Určení ikony okna

Následující příklad ukazuje, jak použít identifikátor URI k určení ikony okna.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Další informace naleznete v tématu <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Načítání obrázků, zvukových souborů a videosouborů

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]umožňuje aplikacím využívat širokou škálu typů médií, které je možné identifikovat a načíst pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak je znázorněno v následujících příkladech.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Další informace o práci s mediálním obsahem najdete v tématu [grafika a multimédia](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Načítání slovníku prostředků z lokality původu

Slovníky prostředků<xref:System.Windows.ResourceDictionary>() lze použít k podpoře motivů aplikace. Jedním ze způsobů, jak vytvářet a spravovat motivy, je vytvořit několik motivů jako slovníky prostředků nacházející se v lokalitě aplikace, kde je původ. To umožňuje přidat a aktualizovat motivy bez nutnosti opětovné kompilace a opětovného nasazení aplikace. Tyto slovníky prostředků lze identifikovat a načíst pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], který je znázorněn v následujícím příkladu.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

Přehled motivů v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]naleznete v tématu [stylování a šablonování](../controls/styling-and-templating.md).

## <a name="see-also"></a>Viz také:

- [Prostředek, obsah a datové soubory aplikace WPF](wpf-application-resource-content-and-data-files.md)
