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
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="e93ae-102">Zdroj, obsah a datové soubory zdroje aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="e93ae-102">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="e93ae-103">Aplikace systému Microsoft Windows často závisí na souborech, které obsahují nespustitelná data, například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]obrázky, video a zvuk.</span><span class="sxs-lookup"><span data-stu-id="e93ae-103">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="e93ae-104">Windows Presentation Foundation (WPF) nabízí speciální podporu pro konfiguraci, identifikaci a používání těchto typů datových souborů, které se nazývají datové soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="e93ae-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="e93ae-105">Tato podpora se točí kolem konkrétní sadu typů datových souborů aplikace, včetně:</span><span class="sxs-lookup"><span data-stu-id="e93ae-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="e93ae-106">**Soubory prostředků**: Datové soubory, které jsou zkompilovány do spustitelného nebo knihovny WPF sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-106">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="e93ae-107">**Soubory obsahu**: Samostatné datové soubory, které mají explicitní přidružení ke spustitelnému sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="e93ae-107">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="e93ae-108">**Web souborů původu**: Samostatné datové soubory, které nemají žádnou souvislost s spustitelným sestavením WPF.</span><span class="sxs-lookup"><span data-stu-id="e93ae-108">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="e93ae-109">Jedním z důležitých rozdílů mezi těmito třemi typy souborů je, že soubory prostředků a soubory obsahu jsou známy v době sestavení; shromáždění o nich má výslovnou znalost.</span><span class="sxs-lookup"><span data-stu-id="e93ae-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="e93ae-110">Pro soubory původu webu však sestavení nemusí mít žádné znalosti o nich vůbec nebo implicitní znalosti prostřednictvím odkazu identifikátor u jednotného prostředku (pack). v tomto případě neexistuje žádná záruka, že odkazované místo původu skutečně existuje.</span><span class="sxs-lookup"><span data-stu-id="e93ae-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="e93ae-111">Chcete-li odkazovat na datové soubory aplikace, Windows Presentation Foundation (WPF) používá pack identifikátor identifikátor uuniform (URI) scheme, který je podrobně popsán v [balení URI v WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="e93ae-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="e93ae-112">Toto téma popisuje konfiguraci a použití datových souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="e93ae-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="e93ae-113">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="e93ae-113">Resource Files</span></span>  
 <span data-ttu-id="e93ae-114">Pokud datový soubor aplikace musí být vždy k dispozici pro aplikaci, jediný způsob, jak zaručit dostupnost je zkompilovat do hlavního spustitelného sestavení aplikace nebo jednoho z jeho odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="e93ae-115">Tento typ datového souboru aplikace se označuje jako *soubor prostředků*.</span><span class="sxs-lookup"><span data-stu-id="e93ae-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="e93ae-116">Soubory prostředků byste měli použít v:</span><span class="sxs-lookup"><span data-stu-id="e93ae-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="e93ae-117">Není nutné aktualizovat obsah souboru prostředků po kompilaci do sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="e93ae-118">Chcete zjednodušit složitost distribuce aplikací snížením počtu závislostí souborů.</span><span class="sxs-lookup"><span data-stu-id="e93ae-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="e93ae-119">Datový soubor aplikace musí být lokalizovatelný (viz [Přehled globalizace a lokalizace WPF).](../advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="e93ae-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e93ae-120">Soubory prostředků popsané v této části se liší od souborů prostředků popsaných v [prostředku XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) a liší se od vložených nebo propojených prostředků popsaných v [části Správa prostředků aplikace (.NET).](/visualstudio/ide/managing-application-resources-dotnet)</span><span class="sxs-lookup"><span data-stu-id="e93ae-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="e93ae-121">Konfigurace souborů prostředků</span><span class="sxs-lookup"><span data-stu-id="e93ae-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="e93ae-122">V WPF soubor prostředků je soubor, který je součástí projektu microsoft sestavení `Resource` modulu (MSBuild) jako položka.</span><span class="sxs-lookup"><span data-stu-id="e93ae-122">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="e93ae-123">V sadě Visual Studio vytvoříte soubor prostředků přidáním souboru do projektu a jeho nastavením `Build Action` na `Resource`.</span><span class="sxs-lookup"><span data-stu-id="e93ae-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="e93ae-124">Při vytváření projektu MSBuild zkompiluje prostředek do sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="e93ae-125">Použití souborů prostředků</span><span class="sxs-lookup"><span data-stu-id="e93ae-125">Using Resource Files</span></span>  
 <span data-ttu-id="e93ae-126">Chcete-li načíst soubor prostředků, můžete volat <xref:System.Windows.Application.GetResourceStream%2A> metodu <xref:System.Windows.Application> třídy a předat identifikátor URI balíčku, který identifikuje požadovaný soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="e93ae-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="e93ae-127"><xref:System.Windows.Application.GetResourceStream%2A>vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor <xref:System.IO.Stream> prostředků jako a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="e93ae-128">Následující kód například ukazuje, jak <xref:System.Windows.Application.GetResourceStream%2A> použít <xref:System.Windows.Controls.Page> k načtení souboru prostředků <xref:System.Windows.Controls.Frame> a`pageFrame`nastavit jej jako obsah ( ):</span><span class="sxs-lookup"><span data-stu-id="e93ae-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="e93ae-129">Při <xref:System.Windows.Application.GetResourceStream%2A> volání vám umožní <xref:System.IO.Stream>přístup k , je třeba provést další práci převodu na typ vlastnosti, které budete nastavení s.</span><span class="sxs-lookup"><span data-stu-id="e93ae-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="e93ae-130">Místo toho můžete nechat WPF postarat o <xref:System.IO.Stream> otevření a převod unavování souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-130">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="e93ae-131">Následující příklad ukazuje, jak <xref:System.Windows.Controls.Page> načíst <xref:System.Windows.Controls.Frame> `pageFrame`přímo do ( ) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="e93ae-132">Následující příklad je ekvivalent značky předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="e93ae-133">Soubory kódu aplikace jako soubory prostředků</span><span class="sxs-lookup"><span data-stu-id="e93ae-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="e93ae-134">Na speciální sadu souborů kódu aplikace WPF lze odkazovat pomocí identifikátorů URI balíčku, včetně oken, stránek, dokumentů toku a slovníků prostředků.</span><span class="sxs-lookup"><span data-stu-id="e93ae-134">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="e93ae-135">Můžete například nastavit <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> vlastnost pomocí identifikátoru URI balíčku, který odkazuje na okno nebo stránku, kterou chcete načíst při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e93ae-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="e93ae-136">Můžete to provést, pokud je soubor XAML součástí projektu `Page` MSBuild jako položka.</span><span class="sxs-lookup"><span data-stu-id="e93ae-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="e93ae-137">V sadě Visual Studio <xref:System.Windows.Window>přidáte <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page>nový <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.ResourceDictionary> , , `Build Action` nebo do projektu, pro `Page`soubor značek bude výchozí .</span><span class="sxs-lookup"><span data-stu-id="e93ae-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="e93ae-138">Při kompilaci `Page` projektu s položkami jsou položky převedeny do binárního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] formátu a zkompilovány do přidruženého sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="e93ae-139">V důsledku toho tyto soubory lze použít stejným způsobem jako typické soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="e93ae-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e93ae-140">Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor nakonfigurován jako `Resource` položka a nemá soubor s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódem na pozadí, je nezpracovaný soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]zkompilován do sestavení, nikoli do binární verze nezpracovaného souboru .</span><span class="sxs-lookup"><span data-stu-id="e93ae-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="e93ae-141">Soubory obsahu</span><span class="sxs-lookup"><span data-stu-id="e93ae-141">Content Files</span></span>  
 <span data-ttu-id="e93ae-142">*Soubor obsahu* je distribuován jako volný soubor vedle spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="e93ae-143">Přestože nejsou kompilovány do sestavení, sestavení jsou kompilovány s metadaty, která vytváří přidružení s každým souborem obsahu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="e93ae-144">Soubory obsahu byste měli použít, pokud vaše aplikace vyžaduje určitou sadu datových souborů aplikace, které chcete aktualizovat bez opětovné kompilace sestavení, které je spotřebovává.</span><span class="sxs-lookup"><span data-stu-id="e93ae-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="e93ae-145">Konfigurace souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="e93ae-145">Configuring Content Files</span></span>  
 <span data-ttu-id="e93ae-146">Chcete-li přidat soubor obsahu do projektu, musí být `Content` datový soubor aplikace zahrnut jako položka.</span><span class="sxs-lookup"><span data-stu-id="e93ae-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="e93ae-147">Navíc vzhledem k tomu, že soubor obsahu není kompilován přímo `CopyToOutputDirectory` do sestavení, je třeba nastavit prvek metadat MSBuild, který určí, že soubor obsahu je zkopírován do umístění, které je relativní vzhledem k sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="e93ae-148">Pokud chcete, aby byl prostředek zkopírován do výstupní složky sestavení `CopyToOutputDirectory` při každém `Always` sestavení projektu, nastavte prvek metadat s hodnotou.</span><span class="sxs-lookup"><span data-stu-id="e93ae-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="e93ae-149">V opačném případě můžete zajistit, že pouze nejnovější verze prostředku je zkopírován do výstupní složky sestavení pomocí `PreserveNewest` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e93ae-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="e93ae-150">Následující text ukazuje soubor, který je nakonfigurován jako soubor obsahu, který je zkopírován do výstupní složky sestavení pouze v případě, že je do projektu přidána nová verze zdroje.</span><span class="sxs-lookup"><span data-stu-id="e93ae-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="e93ae-151">V sadě Visual Studio vytvoříte soubor obsahu přidáním souboru do projektu `Copy to Output Directory` `Copy always` a jeho `Always`nastavením `Build Action` `Content`na `PreserveNewest`, a nastavíte jeho soubor na (stejné jako ) a `Copy if newer` (stejné jako ).</span><span class="sxs-lookup"><span data-stu-id="e93ae-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="e93ae-152">Při sestavení projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je atribut zkompilován do metadat sestavení pro každý soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="e93ae-153">Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> znamená cestu k souboru obsahu vzhledem k jeho umístění v projektu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="e93ae-154">Například pokud soubor obsahu byl umístěn v podsložce projektu, další informace <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> o cestě by být začleněny do hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e93ae-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="e93ae-155">Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je také hodnota cesty k souboru obsahu ve výstupní složce sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="e93ae-156">Použití souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="e93ae-156">Using Content Files</span></span>  
 <span data-ttu-id="e93ae-157">Chcete-li načíst soubor obsahu, můžete volat <xref:System.Windows.Application.GetContentStream%2A> metodu <xref:System.Windows.Application> třídy a předat identifikátor URI balíčku, který identifikuje požadovaný soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="e93ae-158"><xref:System.Windows.Application.GetContentStream%2A>vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor <xref:System.IO.Stream> obsahu jako a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="e93ae-159">Následující kód například ukazuje, jak <xref:System.Windows.Application.GetContentStream%2A> použít <xref:System.Windows.Controls.Page> k načtení souboru obsahu <xref:System.Windows.Controls.Frame> a`pageFrame`nastavit jej jako obsah ( ).</span><span class="sxs-lookup"><span data-stu-id="e93ae-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="e93ae-160">Při <xref:System.Windows.Application.GetContentStream%2A> volání vám umožní <xref:System.IO.Stream>přístup k , je třeba provést další práci převodu na typ vlastnosti, které budete nastavení s.</span><span class="sxs-lookup"><span data-stu-id="e93ae-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="e93ae-161">Místo toho můžete nechat WPF postarat o <xref:System.IO.Stream> otevření a převod unavování souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-161">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="e93ae-162">Následující příklad ukazuje, jak <xref:System.Windows.Controls.Page> načíst <xref:System.Windows.Controls.Frame> `pageFrame`přímo do ( ) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="e93ae-163">Následující příklad je ekvivalent značky předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="e93ae-164">Stránky souborů původu</span><span class="sxs-lookup"><span data-stu-id="e93ae-164">Site of Origin Files</span></span>  
 <span data-ttu-id="e93ae-165">Soubory prostředků mají explicitní vztah se sestaveními, která jsou distribuována společně, jak je definováno <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>v .</span><span class="sxs-lookup"><span data-stu-id="e93ae-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="e93ae-166">Existují však časy, kdy můžete chtít vytvořit implicitní nebo neexistující vztah mezi sestavením a datovým souborem aplikace, včetně případů, kdy:</span><span class="sxs-lookup"><span data-stu-id="e93ae-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="e93ae-167">Soubor neexistuje v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e93ae-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="e93ae-168">Nevíte, jaké soubory bude vaše sestavení vyžadovat až do běhu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="e93ae-169">Chcete mít možnost aktualizovat soubory bez opětovné kompilace sestavení, ke kterému jsou přidruženy.</span><span class="sxs-lookup"><span data-stu-id="e93ae-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="e93ae-170">Aplikace používá velké datové soubory, například zvuk a video, a chcete, aby si je uživatelé stáhli pouze v případě, že se tak rozhodnou.</span><span class="sxs-lookup"><span data-stu-id="e93ae-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="e93ae-171">Je možné načíst tyto typy souborů pomocí tradičních schémat URI, jako je například file:/// a schémata http://.</span><span class="sxs-lookup"><span data-stu-id="e93ae-171">It is possible to load these types of files by using traditional URI schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="e93ae-172">schémata file:/// a http:// však vyžadují, aby vaše aplikace měla plnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="e93ae-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="e93ae-173">Pokud je vaše aplikace aplikace xaml prohlížeč aplikace (XBAP), který byl spuštěn z Internetu nebo intranet, a požaduje pouze sadu oprávnění, která jsou povolena pro aplikace spouštěné z těchto umístění, volné soubory lze načíst pouze z místa původu aplikace (místo spuštění).</span><span class="sxs-lookup"><span data-stu-id="e93ae-173">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="e93ae-174">Tyto soubory jsou známé jako *soubory původu.*</span><span class="sxs-lookup"><span data-stu-id="e93ae-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="e93ae-175">Soubory původu jsou jedinou možností pro aplikace s částečnou důvěryhodností, i když nejsou omezeny na aplikace s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="e93ae-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="e93ae-176">Aplikace s úplným vztahem důvěryhodnosti mohou stále potřebovat načíst datové soubory aplikací, o kterých v době sestavení nevědí. zatímco aplikace s úplnou důvěryhodností mohou používat file:///, je pravděpodobné, že datové soubory aplikace budou nainstalovány ve stejné složce jako sestavení aplikace nebo podsložky.</span><span class="sxs-lookup"><span data-stu-id="e93ae-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="e93ae-177">V tomto případě je použití odkazování na místo původu jednodušší než použití file:///, protože použití file:/// vyžaduje, abyste vypracovali úplnou cestu souboru.</span><span class="sxs-lookup"><span data-stu-id="e93ae-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e93ae-178">Soubory původu webu nejsou ukládány do mezipaměti s aplikací prohlížeče XAML (XBAP) v klientském počítači, zatímco soubory obsahu jsou.</span><span class="sxs-lookup"><span data-stu-id="e93ae-178">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="e93ae-179">V důsledku toho jsou staženy pouze na žádost výslovně.</span><span class="sxs-lookup"><span data-stu-id="e93ae-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="e93ae-180">Pokud aplikace prohlížeče XAML (XBAP) má velké mediální soubory, jejich konfigurace jako soubory původu webu znamená, že počáteční spuštění aplikace je mnohem rychlejší a soubory jsou staženy pouze na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="e93ae-180">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="e93ae-181">Konfigurace souborů původu webu</span><span class="sxs-lookup"><span data-stu-id="e93ae-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="e93ae-182">Pokud vaše soubory původu neexistují nebo nejsou v době kompilace známy, je třeba použít tradiční mechanismy nasazení, které `XCopy` zajistí, že požadované soubory budou k dispozici za běhu, včetně použití programu příkazového řádku nebo Instalační služby systému Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="e93ae-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="e93ae-183">Pokud v době kompilace víte, že soubory, které chcete být umístěny v místě původu, ale přesto chcete vyhnout explicitní závislost, můžete přidat tyto soubory do projektu MSBuild jako `None` položku.</span><span class="sxs-lookup"><span data-stu-id="e93ae-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="e93ae-184">Stejně jako u souborů obsahu je `CopyToOutputDirectory` třeba nastavit atribut MSBuild, abyste určili, že soubor webu původu je zkopírován do umístění, které je relativní k sestavení, zadáním `Always` hodnoty nebo `PreserveNewest` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e93ae-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="e93ae-185">V sadě Visual Studio vytvoříte soubor původního webu přidáním `Build Action` souboru do projektu a nastavením jeho na `None`.</span><span class="sxs-lookup"><span data-stu-id="e93ae-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="e93ae-186">Při vytváření projektu MSBuild zkopíruje zadané soubory do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="e93ae-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="e93ae-187">Použití souborů webu původu</span><span class="sxs-lookup"><span data-stu-id="e93ae-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="e93ae-188">Chcete-li načíst soubor webu původu, můžete volat <xref:System.Windows.Application.GetRemoteStream%2A> metodu <xref:System.Windows.Application> třídy a předat identifikátor URI balíčku, který identifikuje požadovaný soubor původu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="e93ae-189"><xref:System.Windows.Application.GetRemoteStream%2A>vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor webu <xref:System.IO.Stream> původu jako a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="e93ae-190">Následující kód například ukazuje, jak <xref:System.Windows.Application.GetRemoteStream%2A> použít <xref:System.Windows.Controls.Page> k načtení souboru webu původu <xref:System.Windows.Controls.Frame> a`pageFrame`nastavit jej jako obsah ( ).</span><span class="sxs-lookup"><span data-stu-id="e93ae-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="e93ae-191">Při <xref:System.Windows.Application.GetRemoteStream%2A> volání vám umožní <xref:System.IO.Stream>přístup k , je třeba provést další práci převodu na typ vlastnosti, které budete nastavení s.</span><span class="sxs-lookup"><span data-stu-id="e93ae-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="e93ae-192">Místo toho můžete nechat WPF postarat o <xref:System.IO.Stream> otevření a převod unavování souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-192">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="e93ae-193">Následující příklad ukazuje, jak <xref:System.Windows.Controls.Page> načíst <xref:System.Windows.Controls.Frame> `pageFrame`přímo do ( ) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="e93ae-194">Následující příklad je ekvivalent značky předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="e93ae-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="e93ae-195">Opětovné sestavení po změně typu sestavení</span><span class="sxs-lookup"><span data-stu-id="e93ae-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="e93ae-196">Po změně typu sestavení datového souboru aplikace je třeba znovu sestavit celou aplikaci, abyste zajistili, že tyto změny budou použity.</span><span class="sxs-lookup"><span data-stu-id="e93ae-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="e93ae-197">Pokud vytvoříte pouze aplikaci, změny nebudou použity.</span><span class="sxs-lookup"><span data-stu-id="e93ae-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93ae-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="e93ae-198">See also</span></span>

- [<span data-ttu-id="e93ae-199">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="e93ae-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
