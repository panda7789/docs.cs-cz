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
ms.openlocfilehash: d966116db09c2baef7deabf5d01138e8445098be
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636260"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF
Aplikace Microsoft Windows jsou často závislé na souborech, které obsahují data, která nejsou spustitelná, například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrázky, videa a zvuky. Windows Presentation Foundation (WPF) nabízí speciální podporu pro konfiguraci, identifikaci a používání těchto typů datových souborů, které se nazývají datové soubory aplikace. Tato podpora se otáčí kolem konkrétní sady typů datových souborů aplikace, včetně:  
  
- **Soubory prostředků**: datové soubory, které jsou kompilovány buď do spustitelného souboru, nebo do knihovny WPF sestavení.  
  
- **Soubory obsahu**: samostatné datové soubory, které mají explicitní přidružení se spustitelným sestavením WPF.  
  
- **Lokalita se zdrojovými soubory**: samostatné datové soubory, které nemají žádné spojení se spustitelným sestavením WPF.  
  
 Jedním z důležitých rozdílů mezi těmito třemi typy souborů je, že soubory prostředků a soubory obsahu jsou známy v době sestavování. sestavení má explicitní znalosti. Pro weby, které mají zdrojové soubory, ale sestavení nemusí mít žádná vědomí vůbec nebo implicitně znát odkaz na identifikátor URI (Uniform Resource Identifier). v opačném případě není nijak zaručeno, že již existuje odkazovaná lokalita zdrojového souboru.  
  
 Chcete-li odkazovat na datové soubory aplikace Windows Presentation Foundation (WPF), používá schéma identifikátoru URI (Uniform Resource Identifier), které je podrobněji popsáno v [balíčku identifikátory URI v](pack-uris-in-wpf.md)subsystému WPF.  
  
 Toto téma popisuje, jak nakonfigurovat a používat datové soubory aplikace.  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Zdrojové soubory  
 Pokud datový soubor aplikace musí být vždy k dispozici aplikaci, jediným způsobem, jak zaručit dostupnost, je jeho kompilace do hlavního spustitelného sestavení aplikace nebo do jednoho z jeho odkazovaných sestavení. Tento typ datového souboru aplikace je známý jako *soubor prostředků*.  
  
 Soubory prostředků byste měli používat v těchto případech:  
  
- Po zkompilování do sestavení nemusíte aktualizovat obsah zdrojového souboru.  
  
- Chcete zjednodušit distribuci aplikací tím, že snížíte počet závislostí souborů.  
  
- Váš datový soubor aplikace musí být Lokalizovatelný (viz [Přehled globalizace a lokalizace WPF](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
> Soubory prostředků popsané v této části se liší od souborů prostředků popsaných v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) a liší se od vložených nebo propojených prostředků popsaných v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
### <a name="configuring-resource-files"></a>Konfigurace souborů prostředků  
 V WPF je soubor prostředků soubor, který je součástí projektu nástroje Microsoft Build Engine (MSBuild) jako položka `Resource`.  
  
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
> V aplikaci Visual Studio vytvoříte soubor prostředků přidáním souboru do projektu a nastavením jeho `Build Action` na `Resource`.  
  
 Když je projekt sestaven, MSBuild zkompiluje prostředek do sestavení.  
  
### <a name="using-resource-files"></a>Použití souborů prostředků  
 Chcete-li načíst soubor prostředků, můžete zavolat metodu <xref:System.Windows.Application.GetResourceStream%2A> třídy <xref:System.Windows.Application> a předat identifikátor URI balíčku, který identifikuje požadovaný soubor prostředků. <xref:System.Windows.Application.GetResourceStream%2A> vrátí objekt <xref:System.Windows.Resources.StreamResourceInfo>, který zpřístupňuje soubor prostředků jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.  
  
 Například následující kód ukazuje, jak pomocí <xref:System.Windows.Application.GetResourceStream%2A> načíst soubor prostředků <xref:System.Windows.Controls.Page> a nastavit jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Když zavoláte <xref:System.Windows.Application.GetResourceStream%2A> máte přístup k <xref:System.IO.Stream>, je nutné provést další práci, která je převedená na typ vlastnosti, se kterou budete nastavovat. Místo toho je možné nechat, aby se WPF postaral o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 V následujícím příkladu je ekvivalent kódu v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Soubory s kódem aplikace jako soubory prostředků  
 Pomocí identifikátorů URI balíčků, včetně oken, stránek, toků dokumentů a slovníků prostředků, se dá odkazovat speciální sada souborů s kódem aplikace WPF. Můžete například nastavit vlastnost <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> s identifikátorem URI balíčku, který odkazuje na okno nebo stránku, které chcete načíst při spuštění aplikace.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 To lze provést, pokud je soubor XAML obsažen v projektu MSBuild jako položka `Page`.  
  
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
> V aplikaci Visual Studio přidáte do projektu novou <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>nebo <xref:System.Windows.ResourceDictionary>, `Build Action` pro soubor označení bude standardně `Page`.  
  
 Když je zkompilován projekt s `Page`mi položkami, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] položky jsou převedeny do binárního formátu a zkompilovány do přidruženého sestavení. V důsledku toho lze tyto soubory použít stejným způsobem jako typické soubory prostředků.  
  
> [!NOTE]
> Pokud je soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nakonfigurovaný jako `Resource` položka a nemá soubor s kódem na pozadí, nezpracovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se zkompiluje do sestavení namísto binární verze nezpracovaného [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Soubory obsahu  
 *Soubor obsahu* je distribuován jako volný soubor společně se spustitelným sestavením. I když nejsou zkompilovány do sestavení, sestavení jsou kompilována s metadaty, která vytváří přidružení ke každému souboru obsahu.  
  
 Soubory obsahu byste měli použít, pokud vaše aplikace vyžaduje konkrétní sadu datových souborů aplikace, které chcete aktualizovat, aniž by bylo nutné znovu kompilovat sestavení, které je využívá.  
  
### <a name="configuring-content-files"></a>Konfigurace souborů obsahu  
 Chcete-li přidat soubor obsahu do projektu, je třeba zahrnout datový soubor aplikace jako položku `Content`. Vzhledem k tomu, že soubor obsahu není zkompilován přímo do sestavení, je nutné nastavit prvek metadat `CopyToOutputDirectory` MSBuild pro určení, zda je soubor obsahu zkopírován do umístění, které je relativní k sestavenému sestavení. Pokud chcete, aby byl prostředek zkopírován do výstupní složky sestavení pokaždé, když je projekt sestaven, nastavíte `CopyToOutputDirectory` element metadata s hodnotou `Always`. V opačném případě můžete zajistit, aby byla do výstupní složky sestavení zkopírována pouze nejnovější verze prostředku pomocí `PreserveNewest` hodnoty.  
  
 Následující příklad ukazuje soubor, který je nakonfigurován jako soubor obsahu, který je zkopírován do výstupní složky sestavení pouze v případě, že je do projektu přidána nová verze prostředku.  
  
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
> V sadě Visual Studio vytvoříte soubor obsahu přidáním souboru do projektu a nastavením jeho `Build Action` na `Content`a nastavíte jeho `Copy to Output Directory` na `Copy always` (totéž jako `Always`) a `Copy if newer` (totéž jako `PreserveNewest`).  
  
 Při sestavení projektu je atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> zkompilován do metadat sestavení pro každý soubor obsahu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implikuje cestu k souboru obsahu relativně k jeho umístění v projektu. Například pokud se soubor obsahu nachází v podsložce projektu, další informace o cestě budou začleněny do <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> hodnoty.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je také hodnotou cesty k souboru obsahu ve výstupní složce sestavení.  
  
### <a name="using-content-files"></a>Používání souborů obsahu  
 Chcete-li načíst soubor obsahu, můžete zavolat metodu <xref:System.Windows.Application.GetContentStream%2A> třídy <xref:System.Windows.Application> a předat identifikátor URI balíčku, který identifikuje požadovaný soubor obsahu. <xref:System.Windows.Application.GetContentStream%2A> vrátí objekt <xref:System.Windows.Resources.StreamResourceInfo>, který zpřístupňuje soubor obsahu jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.  
  
 Například následující kód ukazuje, jak použít <xref:System.Windows.Application.GetContentStream%2A> k načtení <xref:System.Windows.Controls.Page> souboru obsahu a jeho nastavení jako obsahu <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Když zavoláte <xref:System.Windows.Application.GetContentStream%2A> máte přístup k <xref:System.IO.Stream>, je nutné provést další práci, která je převedená na typ vlastnosti, se kterou budete nastavovat. Místo toho je možné nechat, aby se WPF postaral o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 V následujícím příkladu je ekvivalent kódu v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Lokalita se zdrojovými soubory  
 Soubory prostředků mají explicitní vztah se sestaveními, která jsou distribuována společně, jak je definováno <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Existují však situace, kdy může být vhodné vytvořit implicitní nebo neexistující relaci mezi sestavením a datovým souborem aplikace, včetně:  
  
- Soubor v době kompilace neexistuje.  
  
- Nevíte, které soubory bude vaše sestavení vyžadovat až do doby běhu.  
  
- Chcete být schopni aktualizovat soubory bez opětovné kompilace sestavení, ke kterému jsou přidruženy.  
  
- Vaše aplikace používá velké datové soubory, jako je například zvuk a video, a chcete, aby je uživatelé stáhli, pouze pokud si zvolí.  
  
 Tyto typy souborů je možné načíst pomocí tradičních schémat identifikátorů URI, jako jsou file:///a http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Schémata file:///a http://však vyžadují, aby vaše aplikace měla úplný vztah důvěryhodnosti. Pokud je vaše aplikace aplikace prohlížeče XAML (XBAP), která byla spuštěna z Internetu nebo intranetu, a žádá o ni pouze sada oprávnění povolených pro aplikace spuštěné z těchto umístění, volné soubory lze načíst pouze z původní lokalita aplikace (umístění pro spuštění). Takové soubory se označují jako *weby se zdrojovými* soubory.  
  
 Lokalita počátečních souborů je jedinou možností pro aplikace s částečným vztahem důvěryhodnosti, i když nejsou omezeny na aplikace s částečným vztahem důvěryhodnosti. Aplikace s plnou důvěryhodností stále můžou potřebovat načíst datové soubory aplikace, které neznají v době sestavení. zatímco aplikace s plnou důvěryhodností můžou používat file:///, je nejspíš, že se soubory dat aplikace nainstalují do stejné složky jako nebo z podsložky sestavení aplikace. V takovém případě je používání webu s odkazem na počátek snazší než použití file:///, protože použití file:///vyžaduje, abyste si vypracovali celou cestu k souboru.  
  
> [!NOTE]
> Web se zdrojovými soubory není uložen v mezipaměti aplikace prohlížeče XAML (XBAP) na klientském počítači, zatímco soubory obsahu jsou. V důsledku toho se stáhnou jenom v případě, že je to výslovně požadováno. Pokud aplikace prohlížeče XAML (XBAP) obsahuje velké mediální soubory, nakonfigurujete je jako lokalita původních souborů znamená, že počáteční spuštění aplikace je mnohem rychlejší a soubory se stáhnou jenom na vyžádání.  
  
### <a name="configuring-site-of-origin-files"></a>Probíhá konfigurace serveru počátečních souborů  
 Pokud je vaše lokalita se zdrojovými soubory v době kompilace neexistující nebo neznámá, je nutné použít tradiční mechanismy nasazení, aby bylo zajištěno, že požadované soubory jsou k dispozici v době běhu, včetně buď `XCopy` programu příkazového řádku nebo Instalační služba systému Windows společnosti Microsoft.  
  
 Pokud v době kompilace znáte soubory, které by měly být umístěny v lokalitě původu, ale přesto chcete se vyhnout explicitní závislosti, můžete tyto soubory přidat do projektu MSBuild jako položku `None`. Stejně jako u souborů obsahu je potřeba nastavit atribut MSBuild `CopyToOutputDirectory`, abyste určili, že je lokalita zdrojového souboru zkopírována do umístění, které je relativní k sestavenému sestavení, zadáním hodnoty `Always` nebo `PreserveNewest` hodnoty.  
  
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
> V aplikaci Visual Studio vytvoříte web se zdrojovým souborem přidáním souboru do projektu a nastavením jeho `Build Action` na `None`.  
  
 Po sestavení projektu nástroj MSBuild zkopíruje zadané soubory do výstupní složky sestavení.  
  
### <a name="using-site-of-origin-files"></a>Použití serveru původních souborů  
 Chcete-li načíst web se zdrojovým souborem, můžete zavolat metodu <xref:System.Windows.Application.GetRemoteStream%2A> třídy <xref:System.Windows.Application> a předat identifikátor URI balíčku, který identifikuje požadovaný web se zdrojovým souborem. <xref:System.Windows.Application.GetRemoteStream%2A> vrátí objekt <xref:System.Windows.Resources.StreamResourceInfo>, který zpřístupňuje web zdrojového souboru jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.  
  
 Například následující kód ukazuje, jak použít <xref:System.Windows.Application.GetRemoteStream%2A> k načtení <xref:System.Windows.Controls.Page> lokality zdrojového kódu a jejich nastavení jako obsahu <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Když zavoláte <xref:System.Windows.Application.GetRemoteStream%2A> máte přístup k <xref:System.IO.Stream>, je nutné provést další práci, která je převedená na typ vlastnosti, se kterou budete nastavovat. Místo toho je možné nechat, aby se WPF postaral o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.  
  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 V následujícím příkladu je ekvivalent kódu v předchozím příkladu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Opětovné sestavení po změně typu sestavení  
 Po změně typu sestavení datového souboru aplikace je nutné znovu sestavit celou aplikaci, abyste zajistili, že tyto změny budou provedeny. Pokud sestavíte pouze aplikaci, změny se neprojeví.  
  
## <a name="see-also"></a>Viz také:

- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
