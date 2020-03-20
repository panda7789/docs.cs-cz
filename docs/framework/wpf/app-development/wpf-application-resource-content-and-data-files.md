---
title: Prostředky aplikace, obsah a datové soubory
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
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186193"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF
Aplikace systému Microsoft Windows často závisí na souborech, které obsahují nespustitelná data, například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]obrázky, video a zvuk. Windows Presentation Foundation (WPF) nabízí speciální podporu pro konfiguraci, identifikaci a používání těchto typů datových souborů, které se nazývají datové soubory aplikace. Tato podpora se točí kolem konkrétní sadu typů datových souborů aplikace, včetně:  
  
- **Soubory prostředků**: Datové soubory, které jsou zkompilovány do spustitelného nebo knihovny WPF sestavení.  
  
- **Soubory obsahu**: Samostatné datové soubory, které mají explicitní přidružení ke spustitelnému sestavení WPF.  
  
- **Web souborů původu**: Samostatné datové soubory, které nemají žádnou souvislost s spustitelným sestavením WPF.  
  
 Jedním z důležitých rozdílů mezi těmito třemi typy souborů je, že soubory prostředků a soubory obsahu jsou známy v době sestavení; shromáždění o nich má výslovnou znalost. Pro soubory původu webu však sestavení nemusí mít žádné znalosti o nich vůbec nebo implicitní znalosti prostřednictvím odkazu identifikátor u jednotného prostředku (pack). v tomto případě neexistuje žádná záruka, že odkazované místo původu skutečně existuje.  
  
 Chcete-li odkazovat na datové soubory aplikace, Windows Presentation Foundation (WPF) používá pack identifikátor identifikátor uuniform (URI) scheme, který je podrobně popsán v [balení URI v WPF](pack-uris-in-wpf.md)).  
  
 Toto téma popisuje konfiguraci a použití datových souborů aplikace.  

<a name="Resource_Files"></a>
## <a name="resource-files"></a>Zdrojové soubory  
 Pokud datový soubor aplikace musí být vždy k dispozici pro aplikaci, jediný způsob, jak zaručit dostupnost je zkompilovat do hlavního spustitelného sestavení aplikace nebo jednoho z jeho odkazovaných sestavení. Tento typ datového souboru aplikace se označuje jako *soubor prostředků*.  
  
 Soubory prostředků byste měli použít v:  
  
- Není nutné aktualizovat obsah souboru prostředků po kompilaci do sestavení.  
  
- Chcete zjednodušit složitost distribuce aplikací snížením počtu závislostí souborů.  
  
- Datový soubor aplikace musí být lokalizovatelný (viz [Přehled globalizace a lokalizace WPF).](../advanced/wpf-globalization-and-localization-overview.md)  
  
> [!NOTE]
> Soubory prostředků popsané v této části se liší od souborů prostředků popsaných v [prostředku XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) a liší se od vložených nebo propojených prostředků popsaných v [části Správa prostředků aplikace (.NET).](/visualstudio/ide/managing-application-resources-dotnet)  
  
### <a name="configuring-resource-files"></a>Konfigurace souborů prostředků  
 V WPF soubor prostředků je soubor, který je součástí projektu microsoft sestavení `Resource` modulu (MSBuild) jako položka.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> V sadě Visual Studio vytvoříte soubor prostředků přidáním souboru do projektu a jeho nastavením `Build Action` na `Resource`.  
  
 Při vytváření projektu MSBuild zkompiluje prostředek do sestavení.  
  
### <a name="using-resource-files"></a>Použití souborů prostředků  
 Chcete-li načíst soubor prostředků, můžete volat <xref:System.Windows.Application.GetResourceStream%2A> metodu <xref:System.Windows.Application> třídy a předat identifikátor URI balíčku, který identifikuje požadovaný soubor prostředků. <xref:System.Windows.Application.GetResourceStream%2A>vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor <xref:System.IO.Stream> prostředků jako a popisuje jeho typ obsahu.  
  
 Následující kód například ukazuje, jak <xref:System.Windows.Application.GetResourceStream%2A> použít <xref:System.Windows.Controls.Page> k načtení souboru prostředků <xref:System.Windows.Controls.Frame> a`pageFrame`nastavit jej jako obsah ( ):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Při <xref:System.Windows.Application.GetResourceStream%2A> volání vám umožní <xref:System.IO.Stream>přístup k , je třeba provést další práci převodu na typ vlastnosti, které budete nastavení s. Místo toho můžete nechat WPF postarat o <xref:System.IO.Stream> otevření a převod unavování souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.Page> načíst <xref:System.Windows.Controls.Frame> `pageFrame`přímo do ( ) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Následující příklad je ekvivalent značky předchozího příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Soubory kódu aplikace jako soubory prostředků  
 Na speciální sadu souborů kódu aplikace WPF lze odkazovat pomocí identifikátorů URI balíčku, včetně oken, stránek, dokumentů toku a slovníků prostředků. Můžete například nastavit <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> vlastnost pomocí identifikátoru URI balíčku, který odkazuje na okno nebo stránku, kterou chcete načíst při spuštění aplikace.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Můžete to provést, pokud je soubor XAML součástí projektu `Page` MSBuild jako položka.  
  
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
> V sadě Visual Studio <xref:System.Windows.Window>přidáte <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page>nový <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.ResourceDictionary> , , `Build Action` nebo do projektu, pro `Page`soubor značek bude výchozí .  
  
 Při kompilaci `Page` projektu s položkami jsou položky převedeny do binárního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] formátu a zkompilovány do přidruženého sestavení. V důsledku toho tyto soubory lze použít stejným způsobem jako typické soubory prostředků.  
  
> [!NOTE]
> Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor nakonfigurován jako `Resource` položka a nemá soubor s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódem na pozadí, je nezpracovaný soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]zkompilován do sestavení, nikoli do binární verze nezpracovaného souboru .  
  
<a name="Content_Files"></a>
## <a name="content-files"></a>Soubory obsahu  
 *Soubor obsahu* je distribuován jako volný soubor vedle spustitelného sestavení. Přestože nejsou kompilovány do sestavení, sestavení jsou kompilovány s metadaty, která vytváří přidružení s každým souborem obsahu.  
  
 Soubory obsahu byste měli použít, pokud vaše aplikace vyžaduje určitou sadu datových souborů aplikace, které chcete aktualizovat bez opětovné kompilace sestavení, které je spotřebovává.  
  
### <a name="configuring-content-files"></a>Konfigurace souborů obsahu  
 Chcete-li přidat soubor obsahu do projektu, musí být `Content` datový soubor aplikace zahrnut jako položka. Navíc vzhledem k tomu, že soubor obsahu není kompilován přímo `CopyToOutputDirectory` do sestavení, je třeba nastavit prvek metadat MSBuild, který určí, že soubor obsahu je zkopírován do umístění, které je relativní vzhledem k sestavení. Pokud chcete, aby byl prostředek zkopírován do výstupní složky sestavení `CopyToOutputDirectory` při každém `Always` sestavení projektu, nastavte prvek metadat s hodnotou. V opačném případě můžete zajistit, že pouze nejnovější verze prostředku je zkopírován do výstupní složky sestavení pomocí `PreserveNewest` hodnoty.  
  
 Následující text ukazuje soubor, který je nakonfigurován jako soubor obsahu, který je zkopírován do výstupní složky sestavení pouze v případě, že je do projektu přidána nová verze zdroje.  
  
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
> V sadě Visual Studio vytvoříte soubor obsahu přidáním souboru do projektu `Copy to Output Directory` `Copy always` a jeho `Always`nastavením `Build Action` `Content`na `PreserveNewest`, a nastavíte jeho soubor na (stejné jako ) a `Copy if newer` (stejné jako ).  
  
 Při sestavení projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je atribut zkompilován do metadat sestavení pro každý soubor obsahu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> znamená cestu k souboru obsahu vzhledem k jeho umístění v projektu. Například pokud soubor obsahu byl umístěn v podsložce projektu, další informace <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> o cestě by být začleněny do hodnoty.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je také hodnota cesty k souboru obsahu ve výstupní složce sestavení.  
  
### <a name="using-content-files"></a>Použití souborů obsahu  
 Chcete-li načíst soubor obsahu, můžete volat <xref:System.Windows.Application.GetContentStream%2A> metodu <xref:System.Windows.Application> třídy a předat identifikátor URI balíčku, který identifikuje požadovaný soubor obsahu. <xref:System.Windows.Application.GetContentStream%2A>vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor <xref:System.IO.Stream> obsahu jako a popisuje jeho typ obsahu.  
  
 Následující kód například ukazuje, jak <xref:System.Windows.Application.GetContentStream%2A> použít <xref:System.Windows.Controls.Page> k načtení souboru obsahu <xref:System.Windows.Controls.Frame> a`pageFrame`nastavit jej jako obsah ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Při <xref:System.Windows.Application.GetContentStream%2A> volání vám umožní <xref:System.IO.Stream>přístup k , je třeba provést další práci převodu na typ vlastnosti, které budete nastavení s. Místo toho můžete nechat WPF postarat o <xref:System.IO.Stream> otevření a převod unavování souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.Page> načíst <xref:System.Windows.Controls.Frame> `pageFrame`přímo do ( ) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Následující příklad je ekvivalent značky předchozího příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a>Stránky souborů původu  
 Soubory prostředků mají explicitní vztah se sestaveními, která jsou distribuována společně, jak je definováno <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>v . Existují však časy, kdy můžete chtít vytvořit implicitní nebo neexistující vztah mezi sestavením a datovým souborem aplikace, včetně případů, kdy:  
  
- Soubor neexistuje v době kompilace.  
  
- Nevíte, jaké soubory bude vaše sestavení vyžadovat až do běhu.  
  
- Chcete mít možnost aktualizovat soubory bez opětovné kompilace sestavení, ke kterému jsou přidruženy.  
  
- Aplikace používá velké datové soubory, například zvuk a video, a chcete, aby si je uživatelé stáhli pouze v případě, že se tak rozhodnou.  
  
 Je možné načíst tyto typy souborů pomocí tradičních schémat URI, jako je například file:/// a schémata http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 schémata file:/// a http:// však vyžadují, aby vaše aplikace měla plnou důvěryhodnost. Pokud je vaše aplikace aplikace xaml prohlížeč aplikace (XBAP), který byl spuštěn z Internetu nebo intranet, a požaduje pouze sadu oprávnění, která jsou povolena pro aplikace spouštěné z těchto umístění, volné soubory lze načíst pouze z místa původu aplikace (místo spuštění). Tyto soubory jsou známé jako *soubory původu.*  
  
 Soubory původu jsou jedinou možností pro aplikace s částečnou důvěryhodností, i když nejsou omezeny na aplikace s částečnou důvěryhodností. Aplikace s úplným vztahem důvěryhodnosti mohou stále potřebovat načíst datové soubory aplikací, o kterých v době sestavení nevědí. zatímco aplikace s úplnou důvěryhodností mohou používat file:///, je pravděpodobné, že datové soubory aplikace budou nainstalovány ve stejné složce jako sestavení aplikace nebo podsložky. V tomto případě je použití odkazování na místo původu jednodušší než použití file:///, protože použití file:/// vyžaduje, abyste vypracovali úplnou cestu souboru.  
  
> [!NOTE]
> Soubory původu webu nejsou ukládány do mezipaměti s aplikací prohlížeče XAML (XBAP) v klientském počítači, zatímco soubory obsahu jsou. V důsledku toho jsou staženy pouze na žádost výslovně. Pokud aplikace prohlížeče XAML (XBAP) má velké mediální soubory, jejich konfigurace jako soubory původu webu znamená, že počáteční spuštění aplikace je mnohem rychlejší a soubory jsou staženy pouze na vyžádání.  
  
### <a name="configuring-site-of-origin-files"></a>Konfigurace souborů původu webu  
 Pokud vaše soubory původu neexistují nebo nejsou v době kompilace známy, je třeba použít tradiční mechanismy nasazení, které `XCopy` zajistí, že požadované soubory budou k dispozici za běhu, včetně použití programu příkazového řádku nebo Instalační služby systému Microsoft Windows.  
  
 Pokud v době kompilace víte, že soubory, které chcete být umístěny v místě původu, ale přesto chcete vyhnout explicitní závislost, můžete přidat tyto soubory do projektu MSBuild jako `None` položku. Stejně jako u souborů obsahu je `CopyToOutputDirectory` třeba nastavit atribut MSBuild, abyste určili, že soubor webu původu je zkopírován do umístění, které je relativní k sestavení, zadáním `Always` hodnoty nebo `PreserveNewest` hodnoty.  
  
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
> V sadě Visual Studio vytvoříte soubor původního webu přidáním `Build Action` souboru do projektu a nastavením jeho na `None`.  
  
 Při vytváření projektu MSBuild zkopíruje zadané soubory do výstupní složky sestavení.  
  
### <a name="using-site-of-origin-files"></a>Použití souborů webu původu  
 Chcete-li načíst soubor webu původu, můžete volat <xref:System.Windows.Application.GetRemoteStream%2A> metodu <xref:System.Windows.Application> třídy a předat identifikátor URI balíčku, který identifikuje požadovaný soubor původu. <xref:System.Windows.Application.GetRemoteStream%2A>vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor webu <xref:System.IO.Stream> původu jako a popisuje jeho typ obsahu.  
  
 Následující kód například ukazuje, jak <xref:System.Windows.Application.GetRemoteStream%2A> použít <xref:System.Windows.Controls.Page> k načtení souboru webu původu <xref:System.Windows.Controls.Frame> a`pageFrame`nastavit jej jako obsah ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Při <xref:System.Windows.Application.GetRemoteStream%2A> volání vám umožní <xref:System.IO.Stream>přístup k , je třeba provést další práci převodu na typ vlastnosti, které budete nastavení s. Místo toho můžete nechat WPF postarat o <xref:System.IO.Stream> otevření a převod unavování souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.Page> načíst <xref:System.Windows.Controls.Frame> `pageFrame`přímo do ( ) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Následující příklad je ekvivalent značky předchozího příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a>Opětovné sestavení po změně typu sestavení  
 Po změně typu sestavení datového souboru aplikace je třeba znovu sestavit celou aplikaci, abyste zajistili, že tyto změny budou použity. Pokud vytvoříte pouze aplikaci, změny nebudou použity.  
  
## <a name="see-also"></a>Viz také

- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
