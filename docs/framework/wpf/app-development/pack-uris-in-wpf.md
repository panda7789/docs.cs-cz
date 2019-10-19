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
ms.openlocfilehash: 59c72d9ae12a014a8c47cb3b2852b337b173446c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580621"
---
# <a name="pack-uris-in-wpf"></a>Sbalení URI v technologii WPF

V Windows Presentation Foundation (WPF) se k identifikaci a načítání souborů v mnoha různých způsobech používají identifikátory URI (Uniform Resource Identifier), včetně následujících:

- Určení [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], který se má zobrazit při prvním spuštění aplikace

- Načítají se obrázky.

- Navigace na stránky.

- Načítání nespustitelných datových souborů.

Identifikátory URI se navíc dají použít k identifikaci a načítání souborů z různých umístění, včetně následujících:

- Aktuální sestavení.

- Odkazované sestavení.

- Umístění relativní k sestavení

- Původní lokalita aplikace.

Pro zajištění konzistentního mechanismu pro identifikaci a načítání těchto typů souborů z těchto umístění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá rozšiřitelnost *schématu identifikátoru URI*. Toto téma obsahuje přehled schématu, popisuje, jak vytvořit identifikátory URI balíčku pro celou řadu scénářů, popisuje absolutní a relativní identifikátory URI a rozlišení identifikátoru URI před zobrazením způsobu použití identifikátorů URI balíčku z kódu a kódu.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Schéma identifikátoru URI balíčku

Schéma URI balíčku se používá ve specifikaci OPC ( [Open balení Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) ), která popisuje model pro organizování a identifikaci obsahu. Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíček* je logický kontejner pro jednu nebo více logických *částí*. Tento koncept znázorňuje následující obrázek.

![Diagram balíčků a částí](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

Pro identifikaci částí používá specifikace OPC rozšiřitelnost RFC 2396 (Uniform resource identifiers (URI): Generic Syntax) k definování schématu identifikátoru URI balíčku.

Schéma, které je určeno identifikátorem URI, je definováno jeho předponou; protokol HTTP, FTP a soubor jsou známé příklady. Schéma identifikátoru URI balíčku používá jako své schéma "sadu" a obsahuje dvě komponenty: autorita a cesta. Následuje formát pro identifikátor URI balíčku.

*cesta* /*autority* Pack://

*Autorita* určuje typ balíčku, který součást obsahuje, zatímco *cesta* určuje umístění součásti v rámci balíčku.

Tento koncept je znázorněný na následujícím obrázku:

![Vztah mezi balíčkem, autoritou a cestou](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Balíčky a části jsou analogické pro aplikace a soubory, kde aplikace (balíček) může obsahovat jeden nebo více souborů (částí), včetně:

- Soubory prostředků, které jsou zkompilovány do místního sestavení.

- Soubory prostředků, které jsou zkompilovány do odkazovaného sestavení.

- Soubory prostředků, které jsou zkompilovány do odkazujícího sestavení.

- Soubory obsahu.

- Lokalita se zdrojovými soubory.

Pro přístup k těmto typům souborů podporuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dva autority: application:///a siteoforigin:///. Autorita application:///identifikuje datové soubory aplikace, které jsou známy v době kompilace, včetně souborů prostředků a obsahu. Autorita siteoforigin:///identifikuje web se zdrojovými soubory. Rozsah jednotlivých autorit je znázorněn na následujícím obrázku.

![Diagram identifikátoru URI balíčku](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Součást autority identifikátoru URI balíčku je vložený identifikátor URI, který odkazuje na balíček a musí odpovídat specifikaci RFC 2396. Kromě toho musí být znak "/" nahrazen znakem "," a vyhrazené znaky, například "%" a "?" musí být uvozeny řídicím znakem. Podrobnosti najdete v OPC.

V následujících částech se dozvíte, jak vytvořit identifikátory URI balíčků pomocí těchto dvou úřadů ve spojení s příslušnými cestami k identifikaci prostředků, obsahu a umístění původních souborů.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>Identifikátory URI sad prostředků souboru

Soubory prostředků jsou nakonfigurovány jako MSBuild `Resource` položky a jsou zkompilovány do sestavení. WPF podporuje konstrukci identifikátorů URI balíčku, které lze použít k identifikaci souborů prostředků, které jsou zkompilovány do místního sestavení nebo zkompilovány do sestavení, které je odkazováno z místního sestavení.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Soubor prostředků místního sestavení

Identifikátor URI balíčku pro soubor prostředků kompilovaný do místního sestavení používá následující autoritu a cestu:

- **Autorita**: Application:///.

- **Cesta**: název souboru prostředků, včetně jeho cesty, relativní vzhledem k místnímu kořenu složky sestavení projektu.

Následující příklad ukazuje identifikátor URI balíčku pro soubor prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], který je umístěn v kořenovém adresáři složky projektu místního sestavení.

`pack://application:,,,/ResourceFile.xaml`

Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v podsložce složky projektu místního sestavení.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Odkazovaný soubor prostředků sestavení

Identifikátor URI balíčku pro soubor prostředků kompilovaný do odkazovaného sestavení používá následující autoritu a cestu:

- **Autorita**: Application:///.

- **Cesta**: název souboru prostředků, který je zkompilován do odkazovaného sestavení. Cesta musí odpovídat následujícímu formátu:

  *AssemblyShortName*{ *; Verze*] { *; PublicKey*]; součást/*cesta*

  - **AssemblyShortName**: krátký název odkazovaného sestavení.

  - **; Verze** [volitelné]: verze odkazovaného sestavení, které obsahuje soubor prostředků. To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.

  - **; PublicKey** [volitelné]: veřejný klíč, který se použil k podepsání odkazovaného sestavení. To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.

  - **; Component**: Určuje, zda je na odkazované sestavení odkazováno z místního sestavení.

  - **/Path**: název souboru prostředků, včetně jeho cesty, vzhledem k kořenu složky projektu odkazovaného sestavení.

Následující příklad ukazuje identifikátor URI balíčku pro soubor prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], který je umístěn v kořenovém adresáři složky projektu odkazovaného sestavení.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v podsložce složky projektu odkazovaného sestavení.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

Následující příklad ukazuje identifikátor URI balíčku pro soubor prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], který je umístěn v kořenové složce odkazované složky projektu pro specifické verze sestavení.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Všimněte si, že syntaxe identifikátoru URI balíčku pro odkazované soubory prostředků sestavení se dá použít jenom s autoritou application:///. Například následující příkaz není podporován v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>Identifikátory URI sady souborů obsahu

Identifikátor URI balíčku pro soubor obsahu používá následující autoritu a cestu:

- **Autorita**: Application:///.

- **Cesta**: název souboru obsahu, včetně jeho cesty relativního k umístění systému souborů v hlavním spustitelném sestavení aplikace.

Následující příklad ukazuje identifikátor URI balíčku pro soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu umístěný ve stejné složce jako spustitelné sestavení.

`pack://application:,,,/ContentFile.xaml`

Následující příklad ukazuje identifikátor URI balíčku pro soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu umístěný v podsložce, která je relativní vzhledem k spustitelnému sestavení aplikace.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> Soubory obsahu HTML nelze přejít na. Schéma identifikátoru URI podporuje pouze navigaci na soubory HTML, které jsou umístěny v lokalitě původu.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>Server sad identifikátorů URI pro původní sadu

Identifikátor URI balíčku pro lokalitu zdrojového souboru používá následující autoritu a cestu:

- **Autorita**: siteoforigin:///.

- **Cesta**: název lokality zdrojového souboru, včetně cesty relativního k umístění, ze kterého se spustilo spustitelné sestavení.

Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] web zdrojového souboru uložený v umístění, ze kterého se spouští spustitelné sestavení.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] web zdrojového souboru, uložený v podsložce, která je relativní k umístění, ze kterého se spouští sestavení spustitelného souboru aplikace.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Stránkovací soubory

Soubory XAML, které jsou konfigurovány jako MSBuild `Page` položky, jsou zkompilovány do sestavení stejným způsobem jako soubory prostředků. V důsledku toho mohou být MSBuild `Page` položky identifikovány pomocí identifikátorů URI Pack pro soubory prostředků.

Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů, které jsou běžně nakonfigurované jako MSBuild `Page` položky, mají jako svůj kořenový prvek jednu z následujících hodnot:

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>Absolutní identifikátory URI sady vs. relativní Pack

Plně kvalifikovaný identifikátor URI balíčku zahrnuje schéma, autoritu a cestu a je považován za absolutní identifikátor URI balíčku. V rámci zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky obvykle umožňují nastavit příslušné atributy s identifikátorem URI relativního balíčku, který obsahuje pouze cestu.

Zvažte například následující absolutní identifikátor URI balíčku pro soubor prostředků v místním sestavení.

`pack://application:,,,/ResourceFile.xaml`

Identifikátor URI relativního balíčku, který se vztahuje k tomuto souboru prostředků, by byl následující.

`/ResourceFile.xaml`

> [!NOTE]
> Vzhledem k tomu, že lokalita původních souborů není přidružena k sestavením, mohou být pouze odkazována pouze pomocí absolutních identifikátorů URI Pack.

Ve výchozím nastavení se identifikátor URI relativního balíčku považuje za relativní k umístění značky nebo kódu, který obsahuje odkaz. Pokud se použije počáteční zpětné lomítko, pak se odkaz na identifikátor URI relativního balíčku považuje za relativní ke kořenu aplikace. Zvažte například následující strukturu projektu.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Pokud Page1. XAML obsahuje identifikátor URI, který odkazuje na *kořenový*\SubFolder\Page2.XAML, může odkaz použít následující identifikátor URI relativního balíčku.

`Page2.xaml`

Pokud Page1. XAML obsahuje identifikátor URI, který odkazuje na *kořenový*\Page2.XAML, může odkaz použít následující identifikátor URI relativního balíčku.

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Rozlišení URI balíčku

Formát identifikátorů URI Pack umožňuje, aby identifikátory URI balíčku pro různé typy souborů vypadaly stejně. Zvažte například následující absolutní identifikátor URI balíčku.

`pack://application:,,,/ResourceOrContentFile.xaml`

Tento identifikátor URI absolutního balíčku může odkazovat buď na soubor prostředků v místním sestavení, nebo v souboru obsahu. Totéž platí pro následující relativní identifikátor URI.

`/ResourceOrContentFile.xaml`

Aby bylo možné určit typ souboru, na který odkazuje identifikátor URI balíčku, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přeložit identifikátory URI pro soubory prostředků v místních sestaveních a souborech obsahu pomocí následujících heuristik:

1. Sondujte metadata sestavení pro atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, který se shoduje s identifikátorem URI balíčku.

2. Pokud je nalezen atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, cesta k identifikátoru URI balíčku odkazuje na soubor obsahu.

3. Pokud atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> nebyl nalezen, proveďte test souborů prostředků sady, které jsou zkompilovány do místního sestavení.

4. Pokud je nalezen soubor prostředků odpovídající cestě k identifikátoru URI balíčku, cesta k identifikátoru URI balíčku odkazuje na soubor prostředků.

5. Pokud se prostředek nenajde, interně vytvořené <xref:System.Uri> je neplatné.

Rozlišení identifikátoru URI se nevztahuje na identifikátory URI, které odkazují na následující:

- Soubory obsahu v odkazovaných sestaveních: tyto typy souborů nejsou [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporovány.

- Vložené soubory v odkazovaných sestaveních: identifikátory URI, které je identifikují, jsou jedinečné, protože zahrnují název odkazovaného sestavení a příponu `;component`.

- Lokalita se zdrojovými soubory: identifikátory URI, které je identifikují, jsou jedinečné, protože se jedná o jediné soubory, které je možné identifikovat pomocí identifikátorů URI balíčků, které obsahují siteoforigin:///autoritu.

Jedno zjednodušení, které umožňuje rozlišení URI balíčku, je, že kód může být trochu nezávislý na umístění souborů prostředků a obsahu. Například pokud máte soubor prostředků v lokálním sestavení, které je překonfigurováno na soubor obsahu, identifikátor URI balíčku pro prostředek zůstane stejný, jako kód, který používá identifikátor URI balíčku.

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Programování s identifikátory URI balíčku

Mnoho tříd [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje vlastnosti, které lze nastavit pomocí identifikátorů URI Pack, včetně:

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Tyto vlastnosti lze nastavit z kódu i kódu. Tato část ukazuje základní konstrukce pro obojí a pak ukazuje příklady běžných scénářů.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Použití identifikátorů URI Pack v kódu

Identifikátor URI balíku je zadán v označení nastavením elementu atributu s identifikátorem URI balíčku. Příklad:

`<element attribute="pack://application:,,,/File.xaml" />`

Tabulka 1 znázorňuje různé identifikátory URI absolutních balíčků, které lze zadat v označení.

Tabulka 1: identifikátory URI absolutních balíčků v kódu

|Soubor|Identifikátor URI absolutního balíčku|
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

Tabulka 2 znázorňuje různé identifikátory URI pro relativní balíčky, které lze zadat v označení.

Tabulka 2: identifikátory URI relativních balíčků v kódu

|Soubor|Identifikátor URI relativního balíčku|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Soubor prostředků v místním sestavení|`"/ResourceFile.xaml"`|
|Soubor prostředků v podsložce místního sestavení|`"/Subfolder/ResourceFile.xaml"`|
|Soubor prostředků v odkazovaném sestavení|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Soubor prostředků v podsložce odkazovaného sestavení|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Soubor obsahu|`"/ContentFile.xaml"`|
|Soubor obsahu v podsložce|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Použití identifikátorů URI Pack v kódu

Identifikátor URI balíčku zadáte v kódu vytvořením instance třídy <xref:System.Uri> a předáním identifikátoru URI balíčku jako parametru konstruktoru. To je patrné z následujícího příkladu.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Ve výchozím nastavení třída <xref:System.Uri> považuje identifikátory URI balíčku za absolutní. V důsledku toho je vyvolána výjimka, když je vytvořena instance třídy <xref:System.Uri> s identifikátorem URI relativního balíčku.

```csharp
Uri uri = new Uri("/File.xaml");
```

Naštěstí <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> přetížení konstruktoru <xref:System.Uri> třídy přijímá parametr typu <xref:System.UriKind>, který umožňuje určit, zda je identifikátor URI balíčku buď absolutní, nebo relativní.

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Pokud jste si jisti, že poskytnutý identifikátor URI Pack je jeden nebo druhý, je třeba zadat pouze <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative>. Pokud neznáte typ identifikátoru URI balíčku, který se používá, například když uživatel zadá identifikátor URI balíčku za běhu, použijte místo toho <xref:System.UriKind.RelativeOrAbsolute>.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Tabulka 3 znázorňuje různé identifikátory URI relativních balíčků, které můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.

Tabulka 3: identifikátory URI absolutních balíčků v kódu

|Soubor|Identifikátor URI absolutního balíčku|
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

Tabulka 4 znázorňuje různé identifikátory URI relativních balíčků, které můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.

Tabulka 4: identifikátory URI relativních balíčků v kódu

|Soubor|Identifikátor URI relativního balíčku|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Místní sestavení souboru prostředků|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Soubor prostředků v sestavení místních podsložek|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Soubor prostředků – odkazované sestavení|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Soubor prostředků v sestavení odkazovaném podsložkou|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Soubor obsahu|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Soubor obsahu v podsložce|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Scénáře identifikátoru URI pro Common Pack

V předchozích částech byly popsány postupy sestavení identifikátorů URI pro identifikaci prostředků, obsahu a umístění původních souborů. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou tyto konstrukce používány různými způsoby a následující oddíly obsahují několik běžných použití.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Určení uživatelského rozhraní, které se zobrazí při spuštění aplikace

<xref:System.Windows.Application.StartupUri%2A> určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který se má zobrazit při spuštění aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Pro samostatné aplikace může být [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] okno, jak je znázorněno v následujícím příkladu.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] mohou také určit stránku jako počáteční uživatelské rozhraní, jak je znázorněno v následujícím příkladu.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Pokud je aplikace samostatnou aplikací a je určena Stránka s <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otevře <xref:System.Windows.Navigation.NavigationWindow> pro hostování stránky. V případě [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] se stránka zobrazuje v prohlížeči hostitele.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Navigace na stránku

Následující příklad ukazuje, jak přejít na stránku.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Další informace o různých způsobech navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] najdete v tématu [Přehled navigace](navigation-overview.md).

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Určení ikony okna

Následující příklad ukazuje, jak použít identifikátor URI k určení ikony okna.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Další informace najdete v tématu <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Načítání obrázků, zvukových souborů a videosouborů

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje aplikacím využívat širokou škálu typů médií, které je možné identifikovat a načíst pomocí identifikátorů URI Pack, jak je znázorněno v následujících příkladech.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Další informace o práci s mediálním obsahem najdete v tématu [grafika a multimédia](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Načítání slovníku prostředků z lokality původu

Slovníky prostředků (<xref:System.Windows.ResourceDictionary>) lze použít k podpoře motivů aplikace. Jedním ze způsobů, jak vytvářet a spravovat motivy, je vytvořit několik motivů jako slovníky prostředků nacházející se v lokalitě aplikace, kde je původ. To umožňuje přidat a aktualizovat motivy bez nutnosti opětovné kompilace a opětovného nasazení aplikace. Tyto slovníky prostředků je možné identifikovat a načíst pomocí identifikátorů URI Pack, který je znázorněn v následujícím příkladu.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

Přehled motivů v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] naleznete v tématu [stylování a šablonování](../controls/styling-and-templating.md).

## <a name="see-also"></a>Viz také:

- [Prostředek, obsah a datové soubory aplikace WPF](wpf-application-resource-content-and-data-files.md)
