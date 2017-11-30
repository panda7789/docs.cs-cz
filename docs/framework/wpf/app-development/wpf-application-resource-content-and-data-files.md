---
title: "Zdroj, obsah a datové soubory zdroje aplikací WPF"
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19fd82daabd5ed12776b2deee6bc850529a6ef23
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]aplikace často závisí na soubory, které obsahují data spustitelný soubor, jako například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrázky, videa a zvuku. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]nabízí zvláštní podporu pro konfiguraci, identifikace a použití těchto typů datových souborů, které se nazývají datové soubory aplikace. Tato podpora se pohybuje kolem konkrétní sadu typy souborů dat aplikace, včetně:  
  
-   **Soubory prostředků**: datové soubory, které jsou zkompilovány do buď spustitelný soubor nebo knihovna [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.  
  
-   **Soubory obsahu**: samostatné datové soubory, které mají explicitní přidružení se spustitelný soubor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.  
  
-   **Lokality počátek souborů**: samostatné datové soubory, které mají souvislost se spustitelný soubor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.  
  
 Jeden rozlišení, aby mezi tyto tři typy souborů je, že zdrojových souborů a soubory obsahu se ví, že v čase vytvoření buildu; sestavení má explicitní znalosti z nich. Pro lokalitu zdroji souborů, ale sestavení může mít žádné znalosti z nich, nebo implicitní znalosti prostřednictvím sadu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz; v případě, není zaručeno, že odkazovaného webu zdrojový soubor skutečně existuje.  
  
 Chcete-li datové soubory aplikace [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] používá sada [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] schéma, které je podrobně popsaná v [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 Toto téma popisuje, jak konfigurovat a používat soubory dat aplikace.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Zdrojové soubory  
 Pokud datového souboru aplikace musí být vždy k dispozici pro aplikace, je jediným způsobem, jak zajistit dostupnost kompilována hlavní spustitelný soubor sestavení aplikace nebo jednoho z jeho odkazovaná sestavení. Tento typ datového souboru aplikace se označuje jako *souboru prostředků*.  
  
 Měli byste použít prostředků soubory, když:  
  
-   Nemusíte aktualizovat obsah souboru prostředků poté, co se zkompiluje do sestavení.  
  
-   Chcete zjednodušit složitost distribuce aplikací snížením počtu závislostech souborů.  
  
-   Vašeho datového souboru aplikace, je potřeba lokalizovatelný (viz [WPF globalizace a lokalizace přehled](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Soubory prostředků, které jsou popsané v této části jsou jiné než soubory prostředků popsaných v [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md) a jiné než vložené nebo propojené prostředky, které jsou popsané v [Správa prostředků aplikace (.NET) ](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Konfigurace soubory prostředků  
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
>  V [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vytvořte soubor prostředků přidáním souboru do projektu a nastavení jeho `Build Action` k `Resource`.  
  
 Při sestavení projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kompilovaný prostředku do sestavení.  
  
### <a name="using-resource-files"></a>Pomocí soubory prostředků  
 Chcete-li načíst soubor prostředků, můžete zavolat <xref:System.Windows.Application.GetResourceStream%2A> metodu <xref:System.Windows.Application> třídy a předejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující souboru požadovaného prostředku. <xref:System.Windows.Application.GetResourceStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zveřejňuje soubor prostředků jako <xref:System.IO.Stream> a popisuje typ obsahu.  
  
 Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetResourceStream%2A> načíst <xref:System.Windows.Controls.Page> prostředků souborů a nastavte jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Při volání <xref:System.Windows.Application.GetResourceStream%2A> dává vám přístup k <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, který jste budete nastavení, je další práci. Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnost typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Následující příklad je kód ekvivalentní v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Soubory aplikace kódu jako soubory prostředků  
 Speciální sadu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] soubory kódu aplikace můžete odkazovat pomocí pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně systému windows, stránky, tok dokumenty a slovnících prostředků. Například můžete nastavit <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> vlastnost s sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] okno nebo stránka, která se má načíst při spuštění aplikace, který odkazuje.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Můžete provést při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je součástí [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Page` položky.  
  
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
>  V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], můžete přidat novou <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, nebo <xref:System.Windows.ResourceDictionary> do projektu, `Build Action` pro značku použije výchozí soubor `Page`.  
  
 Když na projekt s `Page` kompiluje položky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] položky jsou převedeny na binární formát a zkompilovat do přidružené sestavení. V důsledku toho tyto soubory můžete použít stejným způsobem jako soubory typické prostředků.  
  
> [!NOTE]
>  Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru je nakonfigurovaný jako `Resource` položky a nemá souboru kódu na pozadí, nezpracovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zkompilován sestavení spíše než binární verzi nezpracovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Soubory obsahu  
 A *obsahu souboru* je distribuován jako soubor přijít společně se spustitelný soubor sestavení. I když nejsou se zkompiluje do sestavení, sestavení jsou kompilovat s metadata, která vytvoří přidružení se jednotlivé soubory obsahu.  
  
 Měli byste použít soubory obsahu, když vaše aplikace vyžaduje konkrétní sadu datové soubory aplikace, které chcete mít možnost aktualizovat bez nutnosti rekompilace sestavení, které využívá je.  
  
### <a name="configuring-content-files"></a>Konfigurace souborů obsahu  
 Pokud chcete přidat do projektu soubor obsahu, musí být zahrnut jako datového souboru aplikace `Content` položky. Kromě toho, protože soubor obsahu není zkompilovat přímo do sestavení, je nutné nastavit [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` element metadat k určení, zda soubor obsahu zkopírován do umístění, která je relativní k integrovaný sestavení. Pokud chcete prostředek zkopírovány do výstupní složky sestavení pokaždé, když je založený na projekt, nastavíte `CopyToOutputDirectory` element metadat s `Always` hodnotu. Jinak, můžete zajistit, že je pouze nejnovější verzi prostředku zkopírovány do výstupní složky sestavení pomocí `PreserveNewest` hodnotu.  
  
 Na obrázku je soubor, který je konfigurován jako soubor obsahu, který se zkopíruje do sestavení výstupu složky pouze v případě, že nová verze prostředku se přidá do projektu.  
  
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
>  V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vytvořte soubor obsahu přidáním souboru do projektu a nastavení jeho `Build Action` k `Content`a nastavit jeho `Copy to Output Directory` k `Copy always` (stejné jako `Always`) a `Copy if newer` (stejné jako `PreserveNewest`).  
  
 Při sestavení projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut kompiluje na metadata sestavení pro jednotlivé soubory obsahu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> znamená cestu k souboru obsahu vzhledem ke své pozici v projektu. Například pokud byl soubor obsahu umístěné v podsložce projektu, další informace o cestě by být součástí <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> hodnotu.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Hodnota je také s hodnotou obsahující cestu k souboru obsahu do výstupní složky sestavení.  
  
### <a name="using-content-files"></a>Pomocí souborů obsahu  
 Chcete-li načíst soubor obsahu, můžete zavolat <xref:System.Windows.Application.GetContentStream%2A> metodu <xref:System.Windows.Application> třídy a předejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující soubor požadovaného obsahu. <xref:System.Windows.Application.GetContentStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zveřejňuje soubor obsahu jako <xref:System.IO.Stream> a popisuje typ obsahu.  
  
 Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetContentStream%2A> načíst <xref:System.Windows.Controls.Page> obsahu souboru a nastavte jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Při volání <xref:System.Windows.Application.GetContentStream%2A> dává vám přístup k <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, který jste budete nastavení, je další práci. Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnost typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Následující příklad je kód ekvivalentní v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Lokality počátek souborů  
 Soubory prostředků mít relaci explicitní s sestavení, které jsou distribuovány společně, podle definice <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Ale existují časy, kdy můžete chtít vytvořit buď neexistující nebo implicitní vztah mezi sestavení a souboru dat aplikace, včetně při:  
  
-   Soubor neexistuje, když v době kompilace.  
  
-   Nevíte, jaké soubory vaše sestavení bude vyžadovat až při spuštění.  
  
-   Chcete mít možnost aktualizovat soubory bez nutnosti rekompilace sestavení, které jsou přidruženy.  
  
-   Vaše aplikace používá velké datové soubory, jako je například audio a video, a chcete pouze uživatelům, pokud se rozhodnete je stáhnout.  
  
 Je možné načíst tyto typy souborů pomocí tradiční [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schémata, jako je například schémata file:/// a http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Schémata file:/// a http:// ale vyžadují vaše aplikace měla úplný vztah důvěryhodnosti. Pokud je vaše aplikace [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] který byl spuštěn z Internetu nebo intranetu, a požaduje jenom na sadu oprávnění, která jsou povoleny pro spuštění z těchto umístění aplikace volné soubory mohou být načteny pouze ze serveru aplikace z původu ( Spusťte umístění). Tyto soubory se označují jako *lokality původu* soubory.  
  
 Lokality počátek soubory jsou jenom možnosti pro aplikace s částečnou důvěryhodností, i když jsou mimo jiné aplikace s částečnou důvěryhodností. Aplikace úplný vztah důvěryhodnosti je stále nutné načíst soubory dat aplikace, které budou neznáte o v čase vytvoření buildu; Při úplný vztah důvěryhodnosti aplikace může používat file:///, je pravděpodobné, že datové soubory aplikace se nainstaluje ve stejné složce jako, nebo na podsložku ve sestavení aplikace. V takovém případě pomocí lokality odkazující na počátku je jednodušší než použití file:///, protože pomocí file:/// vyžaduje, abyste vycházejí úplnou cestu souboru.  
  
> [!NOTE]
>  Lokality původu soubory se neukládají do mezipaměti s [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] na klientský počítač, když jsou soubory obsahu. V důsledku toho pouze stáhnou se konkrétně vyžádání. Pokud [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] aplikace má velké soubory médií, je konfigurace, protože lokality počátek souborů znamená spuštění počáteční aplikace je mnohem rychlejší a soubory staženy pouze na vyžádání.  
  
### <a name="configuring-site-of-origin-files"></a>Konfigurace lokality počátek souborů  
 Pokud váš web počátek soubory jsou neexistující nebo neznámé v době kompilace, budete muset použít tradiční nasazení mechanismy pro zajištění požadované soubory jsou k dispozici v době běhu, včetně použití buď `XCopy` příkazového řádku programu nebo [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Pokud znáte v době kompilace soubory, které byste chtěli být umístěny v lokalitě původu, ale stále se chcete vyhnout explicitní závislosti, můžete přidat těchto souborů do [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `None` položky. Jak se soubory obsahu, musíte nastavit [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` atribut k určení, zda webu zdrojový soubor zkopírován do umístění, která je relativní k integrovaný sestavení zadáním buď `Always` hodnotu nebo `PreserveNewest` hodnotu.  
  
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
>  V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vytvoření webu zdrojový soubor přidáním souboru do projektu a nastavení jeho `Build Action` k `None`.  
  
 Při sestavení projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] zkopíruje zadané soubory do výstupní složky sestavení.  
  
### <a name="using-site-of-origin-files"></a>Pomocí lokality počátek souborů  
 Chcete-li načíst lokality zdrojový soubor, můžete zavolat <xref:System.Windows.Application.GetRemoteStream%2A> metodu <xref:System.Windows.Application> třídy a předejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující požadovaného webu zdrojový soubor. <xref:System.Windows.Application.GetRemoteStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zveřejňuje lokalitě jako zdrojový soubor <xref:System.IO.Stream> a popisuje typ obsahu.  
  
 Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetRemoteStream%2A> načíst <xref:System.Windows.Controls.Page> lokality původu souboru a nastavte jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Při volání <xref:System.Windows.Application.GetRemoteStream%2A> dává vám přístup k <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, který jste budete nastavení, je další práci. Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnost typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Následující příklad je kód ekvivalentní v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Opětovné sestavení po změně typu sestavení  
 Po provedení změny sestavení typ datového souboru aplikace, budete muset znovu sestavte celé aplikace k zajištění, že tyto změny se použijí. Pokud vytvoříte pouze aplikace, nejsou použity změny.  
  
## <a name="see-also"></a>Viz také  
 [Identifikátory URI Pack v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
