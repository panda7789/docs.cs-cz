---
title: Zdroj, obsah a datové soubory zdroje aplikací WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: 5bf1a0e1d4d8f620f83aab50aa50009a0f6a6cf4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417512"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] aplikace jsou často závislé na souborech, které obsahují data – spustitelný soubor, například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrázky, videa a zvuku. Windows Presentation Foundation (WPF) nabízí zvláštní podporu pro konfiguraci, identifikaci a použití těchto typů datových souborů, které se nazývají datových souborů aplikací. Tato podpora zásadní kolem konkrétní sadu typů souborů dat aplikace, včetně:  
  
-   **Soubory prostředků**: datové soubory, které jsou kompilovány do spustitelný soubor nebo knihovna [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.  
  
-   **Obsah souborů**: samostatné datové soubory, které mají přidružený spustitelný soubor k explicitní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.  
  
-   **Lokality původu souborů**: samostatné datové soubory, které mají žádné jejich spojení se spustitelný soubor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.  
  
 Jeden rozlišení, aby se mezi tyto tři typy souborů je, že jsou zdrojové soubory a soubory obsahu v okamžiku sestavení; známé sestavení má explicitní znalosti z nich. Ke stránce původu soubory, ale sestavení můžou nemají žádné informace o jejich vůbec, nebo implicitní znalosti prostřednictvím sadu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkazu; v případě, není zaručeno, že odkazované web zdrojový soubor skutečně existuje.  
  
 Chcete-li datové soubory aplikace, používá Windows Presentation Foundation (WPF) této sady [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] schématu, která je popsána v části [identifikátory Pack URI v subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 Toto téma popisuje, jak nakonfigurovat a používat datové soubory aplikace.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Zdrojové soubory  
 Pokud datový soubor aplikace musí být vždy k dispozici pro aplikace, je jediný způsob, jak zajistit dostupnost zkompilovat do sestavení hlavní spustitelný soubor aplikace nebo jeden z jejích odkazovaných sestavení. Tento typ souboru aplikace, data se označuje jako *soubor prostředků*.  
  
 Měli byste použít prostředek souborů při:  
  
-   Není nutné aktualizovat obsah souboru prostředků po kompilaci do sestavení.  
  
-   Chcete zjednodušit složitost distribuce aplikací snížením počtu závislostem.  
  
-   Datový soubor aplikace musí být lokalizovatelný (viz [přehled WPF globalizace a lokalizace](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Soubory prostředků, které jsou popsané v této části se liší podle soubory prostředků [prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) a jiné než vložené nebo propojené prostředky podle [Správa prostředků aplikace (.NET) ](https://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Konfigurace zdrojových souborů  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], soubor prostředků je soubor, který je součástí [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Resource` položky.  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  V [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vytvořit soubor prostředků tak, že přidáte soubor projektu a nastavení jeho `Build Action` k `Resource`.  
  
 Při sestavení projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] zkompiluje prostředek do sestavení.  
  
### <a name="using-resource-files"></a>Použití souborů prostředků  
 Načíst soubor prostředků, můžete volat <xref:System.Windows.Application.GetResourceStream%2A> metodu <xref:System.Windows.Application> třídy, prochází sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který identifikuje soubor požadovaný prostředek. <xref:System.Windows.Application.GetResourceStream%2A> Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objektu, který zveřejňuje soubor prostředků jako <xref:System.IO.Stream> a popisuje typ obsahu.  
  
 Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetResourceStream%2A> načíst <xref:System.Windows.Controls.Page> prostředků souboru a nastavit ho jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Při volání <xref:System.Windows.Application.GetResourceStream%2A> vám poskytne přístup ke <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, která vám bude nastavení, s další práci. Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 V následujícím příkladu kódu je rovnocenné v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Soubory s kódem aplikace jako soubory prostředků  
 Speciální sadu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] soubory kódu aplikace může být odkazováno pomocí balíčku [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně windows, stránkami, dokumenty toku a slovníky prostředků. Například můžete nastavit <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> vlastnost s pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který odkazuje na okno nebo stránka, která chcete načíst při spuštění aplikace.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Vám pomůžou při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je součástí [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Page` položky.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], přidáte nový <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, nebo <xref:System.Windows.ResourceDictionary> do projektu, `Build Action` pro značky souboru budou ve výchozím nastavení `Page`.  
  
 Když projekt s `Page` kompilaci položky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] položky jsou převést do binárního formátu a zkompilovány do přidružené sestavení. V důsledku toho tyto soubory lze použít stejným způsobem jako typický zdrojové soubory.  
  
> [!NOTE]
>  Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru je nakonfigurovaný jako `Resource` položky a nemá soubor kódu na pozadí, nezpracovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se zkompiluje do sestavení, nikoli binární verzi nezpracovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Soubory obsahu  
 A *obsahu souboru* je distribuován jako volné souboru spolu s spustitelného sestavení. I když nejsou jsou kompilovány do sestavení, sestavení jsou zkompilovaná metadata, která vytvoří přidružení s jednotlivé soubory obsahu.  
  
 Když vaše aplikace vyžaduje určitou sadu datových souborů aplikací, které chcete aktualizovat bez nutnosti rekompilace sestavení, která využívá, je možné, měli byste použít soubory obsahu.  
  
### <a name="configuring-content-files"></a>Konfigurace souborů obsahu  
 Přidání obsahu souboru do projektu, musí být zahrnut jako soubor dat aplikace `Content` položky. Navíc vzhledem k tomu, že soubor s obsahem není zkompilován přímo do sestavení, je nutné nastavit [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` prvek metadat k určení, že obsahu soubor je zkopírován do umístění, která je relativní vzhledem k sestavení. Pokud chcete prostředek, který má být zkopírován do výstupní složka sestavení pokaždé, když je sestaven projekt, můžete nastavit `CopyToOutputDirectory` metadat element s `Always` hodnotu. V opačném případě můžete zajistit, pouze nejnovější verzi prostředku je zkopírována do výstupní složka sestavení s použitím `PreserveNewest` hodnotu.  
  
 Následující uvádí soubor, který je nakonfigurovaný jako soubor obsahu, který se zkopíruje do sestavení výstupní složky pouze v případě, že nová verze prostředku se přidá do projektu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vytvořit soubor obsahu tak, že přidáte soubor projektu a nastavení jeho `Build Action` k `Content`a nastavte jeho `Copy to Output Directory` k `Copy always` (stejné jako `Always`) a `Copy if newer` (stejné jako `PreserveNewest`).  
  
 Při sestavení projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut je zkompilován do metadat sestavení pro jednotlivé soubory obsahu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> znamená cestu k obsahu souboru relativní vzhledem k jeho pozice v projektu. Například pokud byl soubor s obsahem umístěné v podsložce projektu, další informace o cestě by být součástí <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> hodnotu.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Hodnota je také hodnota cestu k obsahu souboru ve výstupní složce sestavení.  
  
### <a name="using-content-files"></a>Pomocí souborů obsahu  
 K načtení obsahu souboru, můžete volat <xref:System.Windows.Application.GetContentStream%2A> metodu <xref:System.Windows.Application> třídy, prochází sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který identifikuje požadovaný obsah souboru. <xref:System.Windows.Application.GetContentStream%2A> Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objektu, který zveřejňuje soubor obsahu jako <xref:System.IO.Stream> a popisuje typ obsahu.  
  
 Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetContentStream%2A> načíst <xref:System.Windows.Controls.Page> obsah souboru a nastavte ji jako obsahu <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Při volání <xref:System.Windows.Application.GetContentStream%2A> vám poskytne přístup ke <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, která vám bude nastavení, s další práci. Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 V následujícím příkladu kódu je rovnocenné v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Lokality původu souborů  
 Soubory prostředků mají explicitního vztahu s sestavení, která se distribuují podél, podle definice <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Ale existují situace, kdy můžete chtít vytvořit buď implicitní nebo neexistuje vztah sestavení a soubor dat aplikace, včetně:  
  
-   Soubor neexistuje v době kompilace.  
  
-   Nevíte, jaké soubory sestavení bude vyžadovat až do spuštění.  
  
-   Chcete mít možnost aktualizovat soubory bez nutnosti rekompilace sestavení, které jsou přidruženy.  
  
-   Vaše aplikace používá velkých datových souborů, jako je například zvuku a videa, a chcete jenom uživatelé si je stáhnout, pokud se rozhodnete.  
  
 Je možné načíst tyto typy souborů s využitím tradičních [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schémata, jako jsou schémata file:/// a http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Schémata file:/// a http:// však vyžaduje vaše aplikace měla úplný vztah důvěryhodnosti. Pokud je vaše aplikace [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] , který byl spuštěn z Internetu nebo intranetu, a vyžaduje pouze sadu oprávnění, které jsou povoleny pro aplikace, které jsou spouštěny z těchto umístění volné soubory mohou být načteny pouze z lokality aplikace původu ( Spustit umístění). Tyto soubory jsou označovány jako *webovou stránku původu* soubory.  
  
 Lokalita zdroje souborů jsou jedinou možností pro aplikace s částečnou důvěryhodností, i když jsou mimo jiné aplikace s částečnou důvěryhodností. Úplný vztah důvěryhodnosti aplikace může stále potřebují načíst datových souborů aplikací, které není ví o v okamžiku sestavení; Při úplném vztahu důvěryhodnosti aplikace může používat file:///, je pravděpodobné, že datové soubory aplikace se nainstaluje ve stejné složce jako nebo na podsložku, sestavení aplikace. V takovém případě použití lokalita odkazuje na původní je jednodušší než při použití file:///, protože pomocí file:/// vyžaduje, abyste tak úplnou cestu souboru.  
  
> [!NOTE]
>  Umístění původních souborů se neukládají do mezipaměti pomocí [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] na klientském počítači, když jsou soubory obsahu. V důsledku toho se jsou staženy pouze při výslovně požadovány. Pokud [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] aplikace má velké soubory médií, jejich konfiguraci, jako je mnohem rychlejší spuštění počáteční aplikace a soubory se stáhnou pouze na vyžádání znamená, že lokality původní soubory.  
  
### <a name="configuring-site-of-origin-files"></a>Konfigurace serveru původu souborů  
 Pokud váš web původu soubory jsou neexistující nebo neznámé v době kompilace, budete muset použít tradiční nasazení mechanismy pro zajištění požadované soubory jsou k dispozici v době běhu, včetně použití buď `XCopy` program v příkazovém řádku nebo [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Pokud víte, v době kompilace soubory, které by má být umístěn v lokalitě původu, ale přesto chcete vyhnout explicitní závislosti, můžete přidat tyto soubory [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `None` položky. Jak se soubory obsahu, je nutné nastavit [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` atribut k určení, že lokality zdrojový soubor je zkopírován do umístění, která je relativní vzhledem k sestavení, zadáním buď `Always` hodnotu nebo `PreserveNewest` hodnotu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vytvoření webu původ souboru přidejte soubor do projektu a nastavení jeho `Build Action` k `None`.  
  
 Při sestavení projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] zkopíruje soubory zadané výstupní složce sestavení.  
  
### <a name="using-site-of-origin-files"></a>Pomocí lokality původu souborů  
 Načíst lokality zdrojový soubor, můžete volat <xref:System.Windows.Application.GetRemoteStream%2A> metodu <xref:System.Windows.Application> třídy, prochází sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který identifikuje požadovaný lokality zdrojový soubor. <xref:System.Windows.Application.GetRemoteStream%2A> Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objektu, který uvádí lokalitě jako zdrojový soubor <xref:System.IO.Stream> a popisuje typ obsahu.  
  
 Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetRemoteStream%2A> načíst <xref:System.Windows.Controls.Page> webovou stránku původu souboru a nastavit ho jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Při volání <xref:System.Windows.Application.GetRemoteStream%2A> vám poskytne přístup ke <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, která vám bude nastavení, s další práci. Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 V následujícím příkladu kódu je rovnocenné v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Znovu sestavit po změně typ sestavení  
 Po změně sestavení typu datového souboru aplikace, budete muset znovu vytvořit celé aplikace, ujistěte se, že tyto změny se použijí. Pokud vytváříte pouze aplikace, nepoužijí se změny.  
  
## <a name="see-also"></a>Viz také  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
