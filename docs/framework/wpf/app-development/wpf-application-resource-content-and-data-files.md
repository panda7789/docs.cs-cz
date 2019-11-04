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
ms.openlocfilehash: 6b1a78ec56032d84d9699c2ecda89308779ee2da
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421139"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="712ed-102">Zdroj, obsah a datové soubory zdroje aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="712ed-102">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="712ed-103">Aplikace Microsoft Windows jsou často závislé na souborech, které obsahují data, která nejsou spustitelná, například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrázky, videa a zvuky.</span><span class="sxs-lookup"><span data-stu-id="712ed-103">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="712ed-104">Windows Presentation Foundation (WPF) nabízí speciální podporu pro konfiguraci, identifikaci a používání těchto typů datových souborů, které se nazývají datové soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="712ed-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="712ed-105">Tato podpora se otáčí kolem konkrétní sady typů datových souborů aplikace, včetně:</span><span class="sxs-lookup"><span data-stu-id="712ed-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="712ed-106">**Soubory prostředků**: datové soubory, které jsou zkompilovány buď do spustitelného souboru, nebo knihovny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-106">**Resource Files**: Data files that are compiled into either an executable or library [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
- <span data-ttu-id="712ed-107">**Soubory obsahu**: samostatné datové soubory, které mají explicitní přidružení se spustitelným souborem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-107">**Content Files**: Standalone data files that have an explicit association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
- <span data-ttu-id="712ed-108">**Lokalita se zdrojovými soubory**: samostatné datové soubory, které nemají žádné spojení se spustitelným souborem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-108">**Site of Origin Files**: Standalone data files that have no association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
 <span data-ttu-id="712ed-109">Jedním z důležitých rozdílů mezi těmito třemi typy souborů je, že soubory prostředků a soubory obsahu jsou známy v době sestavování. sestavení má explicitní znalosti.</span><span class="sxs-lookup"><span data-stu-id="712ed-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="712ed-110">Pro weby, které mají zdrojové soubory, ale sestavení nemusí mít žádná vědomí vůbec nebo implicitně znát odkaz na identifikátor URI (Uniform Resource Identifier). v opačném případě není nijak zaručeno, že již existuje odkazovaná lokalita zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="712ed-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="712ed-111">Chcete-li odkazovat na datové soubory aplikace Windows Presentation Foundation (WPF), používá schéma identifikátoru URI (Uniform Resource Identifier), které je podrobněji popsáno v [balíčku identifikátory URI v](pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="712ed-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="712ed-112">Toto téma popisuje, jak nakonfigurovat a používat datové soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="712ed-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a><span data-ttu-id="712ed-113">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="712ed-113">Resource Files</span></span>  
 <span data-ttu-id="712ed-114">Pokud datový soubor aplikace musí být vždy k dispozici aplikaci, jediným způsobem, jak zaručit dostupnost, je jeho kompilace do hlavního spustitelného sestavení aplikace nebo do jednoho z jeho odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="712ed-115">Tento typ datového souboru aplikace je známý jako *soubor prostředků*.</span><span class="sxs-lookup"><span data-stu-id="712ed-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="712ed-116">Soubory prostředků byste měli používat v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="712ed-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="712ed-117">Po zkompilování do sestavení nemusíte aktualizovat obsah zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="712ed-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="712ed-118">Chcete zjednodušit distribuci aplikací tím, že snížíte počet závislostí souborů.</span><span class="sxs-lookup"><span data-stu-id="712ed-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="712ed-119">Váš datový soubor aplikace musí být Lokalizovatelný (viz [Přehled globalizace a lokalizace WPF](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="712ed-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="712ed-120">Soubory prostředků popsané v této části se liší od souborů prostředků popsaných v tématu [prostředky XAML](../advanced/xaml-resources.md) a liší se od vložených nebo propojených prostředků popsaných v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="712ed-120">The resource files described in this section are different than the resource files described in [XAML Resources](../advanced/xaml-resources.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="712ed-121">Konfigurace souborů prostředků</span><span class="sxs-lookup"><span data-stu-id="712ed-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="712ed-122">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]soubor prostředků je soubor, který je součástí projektu nástroje Microsoft Build Engine (MSBuild) jako položka `Resource`.</span><span class="sxs-lookup"><span data-stu-id="712ed-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="712ed-123">V aplikaci Visual Studio vytvoříte soubor prostředků přidáním souboru do projektu a nastavením jeho `Build Action` na `Resource`.</span><span class="sxs-lookup"><span data-stu-id="712ed-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="712ed-124">Když je projekt sestaven, MSBuild zkompiluje prostředek do sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="712ed-125">Použití souborů prostředků</span><span class="sxs-lookup"><span data-stu-id="712ed-125">Using Resource Files</span></span>  
 <span data-ttu-id="712ed-126">Chcete-li načíst soubor prostředků, můžete zavolat metodu <xref:System.Windows.Application.GetResourceStream%2A> třídy <xref:System.Windows.Application> a předat identifikátor URI balíčku, který identifikuje požadovaný soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="712ed-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="712ed-127"><xref:System.Windows.Application.GetResourceStream%2A> vrátí objekt <xref:System.Windows.Resources.StreamResourceInfo>, který zpřístupňuje soubor prostředků jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="712ed-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="712ed-128">Například následující kód ukazuje, jak pomocí <xref:System.Windows.Application.GetResourceStream%2A> načíst soubor prostředků <xref:System.Windows.Controls.Page> a nastavit jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`):</span><span class="sxs-lookup"><span data-stu-id="712ed-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="712ed-129">Když zavoláte <xref:System.Windows.Application.GetResourceStream%2A> máte přístup k <xref:System.IO.Stream>, je nutné provést další práci, která je převedená na typ vlastnosti, se kterou budete nastavovat.</span><span class="sxs-lookup"><span data-stu-id="712ed-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="712ed-130">Místo toho můžete [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postarat o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="712ed-130">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="712ed-131">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="712ed-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="712ed-132">V následujícím příkladu je ekvivalent kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="712ed-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="712ed-133">Soubory s kódem aplikace jako soubory prostředků</span><span class="sxs-lookup"><span data-stu-id="712ed-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="712ed-134">Pomocí identifikátorů URI balíčků, včetně oken, stránek, toků dokumentů a slovníků prostředků, se dají odkazovat speciální sady [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ch souborů s kódem aplikace.</span><span class="sxs-lookup"><span data-stu-id="712ed-134">A special set of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="712ed-135">Můžete například nastavit vlastnost <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> s identifikátorem URI balíčku, který odkazuje na okno nebo stránku, které chcete načíst při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="712ed-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="712ed-136">To lze provést, pokud je soubor XAML obsažen v projektu MSBuild jako položka `Page`.</span><span class="sxs-lookup"><span data-stu-id="712ed-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="712ed-137">V aplikaci Visual Studio přidáte do projektu novou <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>nebo <xref:System.Windows.ResourceDictionary>, `Build Action` pro soubor označení bude standardně `Page`.</span><span class="sxs-lookup"><span data-stu-id="712ed-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="712ed-138">Když je zkompilován projekt s `Page`mi položkami, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] položky jsou převedeny do binárního formátu a zkompilovány do přidruženého sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="712ed-139">V důsledku toho lze tyto soubory použít stejným způsobem jako typické soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="712ed-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="712ed-140">Pokud je soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nakonfigurovaný jako `Resource` položka a nemá soubor s kódem na pozadí, nezpracovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se zkompiluje do sestavení namísto binární verze nezpracovaného [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="712ed-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a><span data-ttu-id="712ed-141">Soubory obsahu</span><span class="sxs-lookup"><span data-stu-id="712ed-141">Content Files</span></span>  
 <span data-ttu-id="712ed-142">*Soubor obsahu* je distribuován jako volný soubor společně se spustitelným sestavením.</span><span class="sxs-lookup"><span data-stu-id="712ed-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="712ed-143">I když nejsou zkompilovány do sestavení, sestavení jsou kompilována s metadaty, která vytváří přidružení ke každému souboru obsahu.</span><span class="sxs-lookup"><span data-stu-id="712ed-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="712ed-144">Soubory obsahu byste měli použít, pokud vaše aplikace vyžaduje konkrétní sadu datových souborů aplikace, které chcete aktualizovat, aniž by bylo nutné znovu kompilovat sestavení, které je využívá.</span><span class="sxs-lookup"><span data-stu-id="712ed-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="712ed-145">Konfigurace souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="712ed-145">Configuring Content Files</span></span>  
 <span data-ttu-id="712ed-146">Chcete-li přidat soubor obsahu do projektu, je třeba zahrnout datový soubor aplikace jako položku `Content`.</span><span class="sxs-lookup"><span data-stu-id="712ed-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="712ed-147">Vzhledem k tomu, že soubor obsahu není zkompilován přímo do sestavení, je nutné nastavit prvek metadat `CopyToOutputDirectory` MSBuild pro určení, zda je soubor obsahu zkopírován do umístění, které je relativní k sestavenému sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="712ed-148">Pokud chcete, aby byl prostředek zkopírován do výstupní složky sestavení pokaždé, když je projekt sestaven, nastavíte `CopyToOutputDirectory` element metadata s hodnotou `Always`.</span><span class="sxs-lookup"><span data-stu-id="712ed-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="712ed-149">V opačném případě můžete zajistit, aby byla do výstupní složky sestavení zkopírována pouze nejnovější verze prostředku pomocí `PreserveNewest` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="712ed-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="712ed-150">Následující příklad ukazuje soubor, který je nakonfigurován jako soubor obsahu, který je zkopírován do výstupní složky sestavení pouze v případě, že je do projektu přidána nová verze prostředku.</span><span class="sxs-lookup"><span data-stu-id="712ed-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="712ed-151">V sadě Visual Studio vytvoříte soubor obsahu přidáním souboru do projektu a nastavením jeho `Build Action` na `Content`a nastavíte jeho `Copy to Output Directory` na `Copy always` (totéž jako `Always`) a `Copy if newer` (totéž jako `PreserveNewest`).</span><span class="sxs-lookup"><span data-stu-id="712ed-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="712ed-152">Při sestavení projektu je atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> zkompilován do metadat sestavení pro každý soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="712ed-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="712ed-153">Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implikuje cestu k souboru obsahu relativně k jeho umístění v projektu.</span><span class="sxs-lookup"><span data-stu-id="712ed-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="712ed-154">Například pokud se soubor obsahu nachází v podsložce projektu, další informace o cestě budou začleněny do <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="712ed-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="712ed-155">Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je také hodnotou cesty k souboru obsahu ve výstupní složce sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="712ed-156">Používání souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="712ed-156">Using Content Files</span></span>  
 <span data-ttu-id="712ed-157">Chcete-li načíst soubor obsahu, můžete zavolat metodu <xref:System.Windows.Application.GetContentStream%2A> třídy <xref:System.Windows.Application> a předat identifikátor URI balíčku, který identifikuje požadovaný soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="712ed-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="712ed-158"><xref:System.Windows.Application.GetContentStream%2A> vrátí objekt <xref:System.Windows.Resources.StreamResourceInfo>, který zpřístupňuje soubor obsahu jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="712ed-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="712ed-159">Například následující kód ukazuje, jak použít <xref:System.Windows.Application.GetContentStream%2A> k načtení <xref:System.Windows.Controls.Page> souboru obsahu a jeho nastavení jako obsahu <xref:System.Windows.Controls.Frame> (`pageFrame`).</span><span class="sxs-lookup"><span data-stu-id="712ed-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="712ed-160">Když zavoláte <xref:System.Windows.Application.GetContentStream%2A> máte přístup k <xref:System.IO.Stream>, je nutné provést další práci, která je převedená na typ vlastnosti, se kterou budete nastavovat.</span><span class="sxs-lookup"><span data-stu-id="712ed-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="712ed-161">Místo toho můžete [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postarat o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="712ed-161">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="712ed-162">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="712ed-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="712ed-163">V následujícím příkladu je ekvivalent kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="712ed-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a><span data-ttu-id="712ed-164">Lokalita se zdrojovými soubory</span><span class="sxs-lookup"><span data-stu-id="712ed-164">Site of Origin Files</span></span>  
 <span data-ttu-id="712ed-165">Soubory prostředků mají explicitní vztah se sestaveními, která jsou distribuována společně, jak je definováno <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span><span class="sxs-lookup"><span data-stu-id="712ed-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="712ed-166">Existují však situace, kdy může být vhodné vytvořit implicitní nebo neexistující relaci mezi sestavením a datovým souborem aplikace, včetně:</span><span class="sxs-lookup"><span data-stu-id="712ed-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="712ed-167">Soubor v době kompilace neexistuje.</span><span class="sxs-lookup"><span data-stu-id="712ed-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="712ed-168">Nevíte, které soubory bude vaše sestavení vyžadovat až do doby běhu.</span><span class="sxs-lookup"><span data-stu-id="712ed-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="712ed-169">Chcete být schopni aktualizovat soubory bez opětovné kompilace sestavení, ke kterému jsou přidruženy.</span><span class="sxs-lookup"><span data-stu-id="712ed-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="712ed-170">Vaše aplikace používá velké datové soubory, jako je například zvuk a video, a chcete, aby je uživatelé stáhli, pouze pokud si zvolí.</span><span class="sxs-lookup"><span data-stu-id="712ed-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="712ed-171">Tyto typy souborů je možné načíst pomocí tradičních schémat identifikátorů URI, jako jsou file:///a http://.</span><span class="sxs-lookup"><span data-stu-id="712ed-171">It is possible to load these types of files by using traditional URI schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="712ed-172">Schémata file:///a http://však vyžadují, aby vaše aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="712ed-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="712ed-173">Pokud je vaše aplikace aplikace prohlížeče XAML (XBAP), která byla spuštěna z Internetu nebo intranetu, a žádá o ni pouze sada oprávnění povolených pro aplikace spuštěné z těchto umístění, volné soubory lze načíst pouze z původní lokalita aplikace (umístění pro spuštění).</span><span class="sxs-lookup"><span data-stu-id="712ed-173">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="712ed-174">Takové soubory se označují jako *weby se zdrojovými* soubory.</span><span class="sxs-lookup"><span data-stu-id="712ed-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="712ed-175">Lokalita počátečních souborů je jedinou možností pro aplikace s částečným vztahem důvěryhodnosti, i když nejsou omezeny na aplikace s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="712ed-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="712ed-176">Aplikace s plnou důvěryhodností stále můžou potřebovat načíst datové soubory aplikace, které neznají v době sestavení. zatímco aplikace s plnou důvěryhodností můžou používat file:///, je nejspíš, že se soubory dat aplikace nainstalují do stejné složky jako nebo z podsložky sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="712ed-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="712ed-177">V takovém případě je používání webu s odkazem na počátek snazší než použití file:///, protože použití file:///vyžaduje, abyste si vypracovali celou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="712ed-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="712ed-178">Web se zdrojovými soubory není uložen v mezipaměti aplikace prohlížeče XAML (XBAP) na klientském počítači, zatímco soubory obsahu jsou.</span><span class="sxs-lookup"><span data-stu-id="712ed-178">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="712ed-179">V důsledku toho se stáhnou jenom v případě, že je to výslovně požadováno.</span><span class="sxs-lookup"><span data-stu-id="712ed-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="712ed-180">Pokud aplikace prohlížeče XAML (XBAP) obsahuje velké mediální soubory, nakonfigurujete je jako lokalita původních souborů znamená, že počáteční spuštění aplikace je mnohem rychlejší a soubory se stáhnou jenom na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="712ed-180">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="712ed-181">Probíhá konfigurace serveru počátečních souborů</span><span class="sxs-lookup"><span data-stu-id="712ed-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="712ed-182">Pokud je vaše lokalita se zdrojovými soubory v době kompilace neexistující nebo neznámá, je nutné použít tradiční mechanismy nasazení, aby bylo zajištěno, že požadované soubory budou k dispozici v době běhu, včetně buď `XCopy` programu příkazového řádku nebo programu Microsoft Windows Instalační.</span><span class="sxs-lookup"><span data-stu-id="712ed-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="712ed-183">Pokud v době kompilace znáte soubory, které by měly být umístěny v lokalitě původu, ale přesto chcete se vyhnout explicitní závislosti, můžete tyto soubory přidat do projektu MSBuild jako položku `None`.</span><span class="sxs-lookup"><span data-stu-id="712ed-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="712ed-184">Stejně jako u souborů obsahu je potřeba nastavit atribut MSBuild `CopyToOutputDirectory`, abyste určili, že je lokalita zdrojového souboru zkopírována do umístění, které je relativní k sestavenému sestavení, zadáním hodnoty `Always` nebo `PreserveNewest` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="712ed-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="712ed-185">V aplikaci Visual Studio vytvoříte web se zdrojovým souborem přidáním souboru do projektu a nastavením jeho `Build Action` na `None`.</span><span class="sxs-lookup"><span data-stu-id="712ed-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="712ed-186">Po sestavení projektu nástroj MSBuild zkopíruje zadané soubory do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="712ed-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="712ed-187">Použití serveru původních souborů</span><span class="sxs-lookup"><span data-stu-id="712ed-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="712ed-188">Chcete-li načíst web se zdrojovým souborem, můžete zavolat metodu <xref:System.Windows.Application.GetRemoteStream%2A> třídy <xref:System.Windows.Application> a předat identifikátor URI balíčku, který identifikuje požadovaný web se zdrojovým souborem.</span><span class="sxs-lookup"><span data-stu-id="712ed-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="712ed-189"><xref:System.Windows.Application.GetRemoteStream%2A> vrátí objekt <xref:System.Windows.Resources.StreamResourceInfo>, který zpřístupňuje web zdrojového souboru jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="712ed-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="712ed-190">Například následující kód ukazuje, jak použít <xref:System.Windows.Application.GetRemoteStream%2A> k načtení <xref:System.Windows.Controls.Page> lokality zdrojového kódu a jejich nastavení jako obsahu <xref:System.Windows.Controls.Frame> (`pageFrame`).</span><span class="sxs-lookup"><span data-stu-id="712ed-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="712ed-191">Když zavoláte <xref:System.Windows.Application.GetRemoteStream%2A> máte přístup k <xref:System.IO.Stream>, je nutné provést další práci, která je převedená na typ vlastnosti, se kterou budete nastavovat.</span><span class="sxs-lookup"><span data-stu-id="712ed-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="712ed-192">Místo toho můžete [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postarat o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="712ed-192">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="712ed-193">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="712ed-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="712ed-194">V následujícím příkladu je ekvivalent kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="712ed-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="712ed-195">Opětovné sestavení po změně typu sestavení</span><span class="sxs-lookup"><span data-stu-id="712ed-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="712ed-196">Po změně typu sestavení datového souboru aplikace je nutné znovu sestavit celou aplikaci, abyste zajistili, že tyto změny budou provedeny.</span><span class="sxs-lookup"><span data-stu-id="712ed-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="712ed-197">Pokud sestavíte pouze aplikaci, změny se neprojeví.</span><span class="sxs-lookup"><span data-stu-id="712ed-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712ed-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="712ed-198">See also</span></span>

- [<span data-ttu-id="712ed-199">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="712ed-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
