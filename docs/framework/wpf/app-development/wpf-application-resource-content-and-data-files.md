---
title: Prostředky aplikace, obsah a datové soubory
description: Přečtěte si o speciální podpoře pro konfiguraci, identifikaci a používání datových souborů aplikace v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 324b3eb922f0fd1d1d9ad00105a06a7fbdb8effd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622858"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="ee9ee-103">Zdroj, obsah a datové soubory zdroje aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="ee9ee-103">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="ee9ee-104">Aplikace Microsoft Windows jsou často závislé na souborech, které obsahují data, která nejsou spustitelná, například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] obrázky, videa a zvuky.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-104">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="ee9ee-105">Windows Presentation Foundation (WPF) nabízí speciální podporu pro konfiguraci, identifikaci a používání těchto typů datových souborů, které se nazývají datové soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-105">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="ee9ee-106">Tato podpora se otáčí kolem konkrétní sady typů datových souborů aplikace, včetně:</span><span class="sxs-lookup"><span data-stu-id="ee9ee-106">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="ee9ee-107">**Soubory prostředků**: datové soubory, které jsou kompilovány buď do spustitelného souboru, nebo do knihovny WPF sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-107">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="ee9ee-108">**Soubory obsahu**: samostatné datové soubory, které mají explicitní přidružení se spustitelným sestavením WPF.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-108">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="ee9ee-109">**Lokalita se zdrojovými soubory**: samostatné datové soubory, které nemají žádné spojení se spustitelným sestavením WPF.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-109">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="ee9ee-110">Jedním z důležitých rozdílů mezi těmito třemi typy souborů je, že soubory prostředků a soubory obsahu jsou známy v době sestavování. sestavení má explicitní znalosti.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-110">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="ee9ee-111">Pro weby, které mají zdrojové soubory, ale sestavení nemusí mít žádná vědomí vůbec nebo implicitně znát odkaz na identifikátor URI (Uniform Resource Identifier). v opačném případě není nijak zaručeno, že již existuje odkazovaná lokalita zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-111">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="ee9ee-112">Chcete-li odkazovat na datové soubory aplikace Windows Presentation Foundation (WPF), používá schéma identifikátoru URI (Uniform Resource Identifier), které je podrobněji popsáno v [balíčku identifikátory URI v](pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-112">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="ee9ee-113">Toto téma popisuje, jak nakonfigurovat a používat datové soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-113">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="ee9ee-114">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="ee9ee-114">Resource Files</span></span>  
 <span data-ttu-id="ee9ee-115">Pokud datový soubor aplikace musí být vždy k dispozici aplikaci, jediným způsobem, jak zaručit dostupnost, je jeho kompilace do hlavního spustitelného sestavení aplikace nebo do jednoho z jeho odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-115">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="ee9ee-116">Tento typ datového souboru aplikace je známý jako *soubor prostředků*.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-116">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="ee9ee-117">Soubory prostředků byste měli používat v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="ee9ee-117">You should use resource files when:</span></span>  
  
- <span data-ttu-id="ee9ee-118">Po zkompilování do sestavení nemusíte aktualizovat obsah zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-118">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="ee9ee-119">Chcete zjednodušit distribuci aplikací tím, že snížíte počet závislostí souborů.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-119">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="ee9ee-120">Váš datový soubor aplikace musí být Lokalizovatelný (viz [Přehled globalizace a lokalizace WPF](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-120">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee9ee-121">Soubory prostředků popsané v této části se liší od souborů prostředků popsaných v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) a liší se od vložených nebo propojených prostředků popsaných v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-121">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="ee9ee-122">Konfigurace souborů prostředků</span><span class="sxs-lookup"><span data-stu-id="ee9ee-122">Configuring Resource Files</span></span>  
 <span data-ttu-id="ee9ee-123">V WPF je soubor prostředků soubor, který je součástí projektu nástroje Microsoft Build Engine (MSBuild) jako `Resource` položka.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-123">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="ee9ee-124">V aplikaci Visual Studio vytvoříte soubor prostředků přidáním souboru do projektu a jeho nastavením `Build Action` na `Resource` .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-124">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="ee9ee-125">Když je projekt sestaven, MSBuild zkompiluje prostředek do sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-125">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="ee9ee-126">Použití souborů prostředků</span><span class="sxs-lookup"><span data-stu-id="ee9ee-126">Using Resource Files</span></span>  
 <span data-ttu-id="ee9ee-127">Chcete-li načíst soubor prostředků, můžete zavolat <xref:System.Windows.Application.GetResourceStream%2A> metodu <xref:System.Windows.Application> třídy a předat identifikátor URI balíčku, který identifikuje požadovaný soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-127">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="ee9ee-128"><xref:System.Windows.Application.GetResourceStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor prostředků jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-128"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="ee9ee-129">Například následující kód ukazuje, jak použít <xref:System.Windows.Application.GetResourceStream%2A> k načtení <xref:System.Windows.Controls.Page> souboru prostředků a jeho nastavení jako obsahu a <xref:System.Windows.Controls.Frame> ( `pageFrame` ):</span><span class="sxs-lookup"><span data-stu-id="ee9ee-129">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="ee9ee-130">Při volání <xref:System.Windows.Application.GetResourceStream%2A> poskytuje přístup k <xref:System.IO.Stream> , je nutné provést další práci, která je převedena na typ vlastnosti, se kterou budete nastavovat.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-130">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="ee9ee-131">Místo toho je možné nechat, aby se WPF postaral o otevření a převod <xref:System.IO.Stream> pomocí načtení souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-131">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="ee9ee-132">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do a <xref:System.Windows.Controls.Frame> ( `pageFrame` ) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-132">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="ee9ee-133">V následujícím příkladu je ekvivalent kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-133">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="ee9ee-134">Soubory s kódem aplikace jako soubory prostředků</span><span class="sxs-lookup"><span data-stu-id="ee9ee-134">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="ee9ee-135">Pomocí identifikátorů URI balíčků, včetně oken, stránek, toků dokumentů a slovníků prostředků, se dá odkazovat speciální sada souborů s kódem aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-135">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="ee9ee-136">Můžete například nastavit <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> vlastnost s identifikátorem URI balíčku, který odkazuje na okno nebo stránku, které chcete načíst při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-136">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="ee9ee-137">To lze provést, pokud je soubor XAML obsažen v projektu MSBuild jako `Page` položka.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-137">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="ee9ee-138">V aplikaci Visual Studio přidáte nový <xref:System.Windows.Window> ,,, <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument> nebo <xref:System.Windows.ResourceDictionary> do projektu, `Build Action` pro soubor označení bude použita výchozí hodnota `Page` .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-138">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="ee9ee-139">Když `Page` je zkompilován projekt s položkami, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] položky jsou převedeny do binárního formátu a zkompilovány do přidruženého sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-139">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="ee9ee-140">V důsledku toho lze tyto soubory použít stejným způsobem jako typické soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-140">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee9ee-141">Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor nakonfigurovaný jako `Resource` položka a nemá soubor s kódem na pozadí, nezpracovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] instance je zkompilována do sestavení namísto binární verze nezpracovaného [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-141">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="ee9ee-142">Soubory obsahu</span><span class="sxs-lookup"><span data-stu-id="ee9ee-142">Content Files</span></span>  
 <span data-ttu-id="ee9ee-143">*Soubor obsahu* je distribuován jako volný soubor společně se spustitelným sestavením.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-143">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="ee9ee-144">I když nejsou zkompilovány do sestavení, sestavení jsou kompilována s metadaty, která vytváří přidružení ke každému souboru obsahu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-144">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="ee9ee-145">Soubory obsahu byste měli použít, pokud vaše aplikace vyžaduje konkrétní sadu datových souborů aplikace, které chcete aktualizovat, aniž by bylo nutné znovu kompilovat sestavení, které je využívá.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-145">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="ee9ee-146">Konfigurace souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="ee9ee-146">Configuring Content Files</span></span>  
 <span data-ttu-id="ee9ee-147">Chcete-li přidat soubor obsahu do projektu, je třeba zahrnout datový soubor aplikace jako `Content` položku.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-147">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="ee9ee-148">Vzhledem k tomu, že soubor obsahu není zkompilován přímo do sestavení, je nutné nastavit `CopyToOutputDirectory` element metadata MSBuild pro určení, že soubor obsahu je zkopírován do umístění, které je relativní k sestavenému sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-148">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="ee9ee-149">Chcete-li, aby byl prostředek zkopírován do výstupní složky sestavení při každém sestavení projektu, nastavte `CopyToOutputDirectory` element metadata na `Always` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-149">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="ee9ee-150">V opačném případě můžete zajistit, aby byla do výstupní složky sestavení zkopírována pouze nejnovější verze prostředku pomocí `PreserveNewest` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-150">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="ee9ee-151">Následující příklad ukazuje soubor, který je nakonfigurován jako soubor obsahu, který je zkopírován do výstupní složky sestavení pouze v případě, že je do projektu přidána nová verze prostředku.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-151">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="ee9ee-152">V sadě Visual Studio vytvoříte soubor obsahu přidáním souboru do projektu a jeho nastavením `Build Action` na `Content` a nastavíte `Copy to Output Directory` na hodnotu `Copy always` (stejné jako `Always` ) a `Copy if newer` (stejné jako `PreserveNewest` ).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-152">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="ee9ee-153">Při sestavení projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je atribut zkompilován do metadat sestavení pro každý soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-153">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="ee9ee-154">Hodnota z hodnoty <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implikuje cestu k souboru obsahu relativně k jeho umístění v projektu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-154">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="ee9ee-155">Například pokud se soubor obsahu nachází v podsložce projektu, další informace o cestě budou začleněny do <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-155">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="ee9ee-156"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>Hodnota je také hodnota cesty k souboru obsahu ve výstupní složce sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-156">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="ee9ee-157">Používání souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="ee9ee-157">Using Content Files</span></span>  
 <span data-ttu-id="ee9ee-158">Chcete-li načíst soubor obsahu, můžete zavolat <xref:System.Windows.Application.GetContentStream%2A> metodu <xref:System.Windows.Application> třídy, PŘEDÁNÍm identifikátoru URI balíčku, který identifikuje požadovaný soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-158">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="ee9ee-159"><xref:System.Windows.Application.GetContentStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje soubor obsahu jako <xref:System.IO.Stream> a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-159"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="ee9ee-160">Například následující kód ukazuje, jak použít <xref:System.Windows.Application.GetContentStream%2A> k načtení <xref:System.Windows.Controls.Page> souboru obsahu a jeho nastavení jako obsahu a <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-160">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="ee9ee-161">Při volání <xref:System.Windows.Application.GetContentStream%2A> poskytuje přístup k <xref:System.IO.Stream> , je nutné provést další práci, která je převedena na typ vlastnosti, se kterou budete nastavovat.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-161">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="ee9ee-162">Místo toho je možné nechat, aby se WPF postaral o otevření a převod <xref:System.IO.Stream> pomocí načtení souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-162">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="ee9ee-163">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do a <xref:System.Windows.Controls.Frame> ( `pageFrame` ) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-163">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="ee9ee-164">V následujícím příkladu je ekvivalent kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-164">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="ee9ee-165">Lokalita se zdrojovými soubory</span><span class="sxs-lookup"><span data-stu-id="ee9ee-165">Site of Origin Files</span></span>  
 <span data-ttu-id="ee9ee-166">Soubory prostředků mají explicitní vztah se sestaveními, která jsou distribuována společně, jak je definováno v <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-166">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="ee9ee-167">Existují však situace, kdy může být vhodné vytvořit implicitní nebo neexistující relaci mezi sestavením a datovým souborem aplikace, včetně:</span><span class="sxs-lookup"><span data-stu-id="ee9ee-167">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="ee9ee-168">Soubor v době kompilace neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-168">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="ee9ee-169">Nevíte, které soubory bude vaše sestavení vyžadovat až do doby běhu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-169">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="ee9ee-170">Chcete být schopni aktualizovat soubory bez opětovné kompilace sestavení, ke kterému jsou přidruženy.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-170">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="ee9ee-171">Vaše aplikace používá velké datové soubory, jako je například zvuk a video, a chcete, aby je uživatelé stáhli, pouze pokud si zvolí.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-171">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="ee9ee-172">Tyto typy souborů lze načíst pomocí tradičních schémat identifikátorů URI, například `file:///` `http://` schémat a.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-172">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="ee9ee-173">Nicméně `file:///` `http://` schémata a vyžadují, aby vaše aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-173">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="ee9ee-174">Pokud se jedná o aplikaci prohlížeče XAML (XBAP), která byla spuštěna z Internetu nebo intranetu, a požaduje pouze sadu oprávnění, která jsou povolena pro aplikace spuštěné z těchto umístění, volné soubory lze načíst pouze z lokality původu aplikace (umístění pro spuštění).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-174">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="ee9ee-175">Takové soubory se označují jako *weby se zdrojovými* soubory.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-175">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="ee9ee-176">Lokalita počátečních souborů je jedinou možností pro aplikace s částečným vztahem důvěryhodnosti, i když nejsou omezeny na aplikace s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-176">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="ee9ee-177">Aplikace s plnou důvěryhodností stále můžou potřebovat načíst datové soubory aplikace, které neznají v době sestavení. zatímco aplikace s plnou důvěryhodností můžou používat file:///, je nejspíš, že se soubory dat aplikace nainstalují do stejné složky jako nebo z podsložky sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-177">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="ee9ee-178">V takovém případě je používání webu s odkazem na počátek snazší než použití file:///, protože použití file:///vyžaduje, abyste si vypracovali celou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-178">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee9ee-179">Web se zdrojovými soubory není uložen v mezipaměti aplikace prohlížeče XAML (XBAP) na klientském počítači, zatímco soubory obsahu jsou.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-179">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="ee9ee-180">V důsledku toho se stáhnou jenom v případě, že je to výslovně požadováno.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-180">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="ee9ee-181">Pokud aplikace prohlížeče XAML (XBAP) obsahuje velké mediální soubory, nakonfigurujete je jako lokalita původních souborů znamená, že počáteční spuštění aplikace je mnohem rychlejší a soubory se stáhnou jenom na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-181">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="ee9ee-182">Probíhá konfigurace serveru počátečních souborů</span><span class="sxs-lookup"><span data-stu-id="ee9ee-182">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="ee9ee-183">Pokud je vaše lokalita se zdrojovými soubory v době kompilace neexistující nebo neznámá, je nutné použít tradiční mechanismy nasazení, aby bylo zajištěno, že požadované soubory jsou k dispozici v době běhu, včetně buď `XCopy` programu příkazového řádku nebo programu Microsoft instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-183">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="ee9ee-184">Pokud v době kompilace znáte soubory, které by měly být umístěny v lokalitě původu, ale přesto chcete se vyhnout explicitní závislosti, můžete tyto soubory přidat do projektu MSBuild jako `None` položku.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-184">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="ee9ee-185">Stejně jako u souborů obsahu je potřeba nastavit `CopyToOutputDirectory` atribut MSBuild tak, aby určoval, že je lokalita zdrojového souboru zkopírována do umístění, které je relativní k sestavenému sestavení, zadáním `Always` hodnoty nebo `PreserveNewest` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-185">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="ee9ee-186">V aplikaci Visual Studio vytvoříte web se zdrojovým souborem přidáním souboru do projektu a jeho nastavením `Build Action` na `None` .</span><span class="sxs-lookup"><span data-stu-id="ee9ee-186">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="ee9ee-187">Po sestavení projektu nástroj MSBuild zkopíruje zadané soubory do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-187">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="ee9ee-188">Použití serveru původních souborů</span><span class="sxs-lookup"><span data-stu-id="ee9ee-188">Using Site of Origin Files</span></span>  
 <span data-ttu-id="ee9ee-189">Chcete-li načíst web se zdrojovým souborem, můžete zavolat <xref:System.Windows.Application.GetRemoteStream%2A> metodu <xref:System.Windows.Application> třídy, PŘEDÁNÍm identifikátoru URI balíčku, který identifikuje požadovaný web zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-189">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="ee9ee-190"><xref:System.Windows.Application.GetRemoteStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zpřístupňuje web zdrojového souboru jako <xref:System.IO.Stream> a a popisuje jeho typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-190"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="ee9ee-191">Například následující kód ukazuje, jak použít <xref:System.Windows.Application.GetRemoteStream%2A> k načtení <xref:System.Windows.Controls.Page> lokality zdrojového souboru a nastavit ji jako obsah a <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="ee9ee-191">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="ee9ee-192">Při volání <xref:System.Windows.Application.GetRemoteStream%2A> poskytuje přístup k <xref:System.IO.Stream> , je nutné provést další práci, která je převedena na typ vlastnosti, se kterou budete nastavovat.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-192">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="ee9ee-193">Místo toho je možné nechat, aby se WPF postaral o otevření a převod <xref:System.IO.Stream> pomocí načtení souboru prostředků přímo do vlastnosti typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-193">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="ee9ee-194">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do a <xref:System.Windows.Controls.Frame> ( `pageFrame` ) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-194">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="ee9ee-195">V následujícím příkladu je ekvivalent kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-195">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="ee9ee-196">Opětovné sestavení po změně typu sestavení</span><span class="sxs-lookup"><span data-stu-id="ee9ee-196">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="ee9ee-197">Po změně typu sestavení datového souboru aplikace je nutné znovu sestavit celou aplikaci, abyste zajistili, že tyto změny budou provedeny.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-197">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="ee9ee-198">Pokud sestavíte pouze aplikaci, změny se neprojeví.</span><span class="sxs-lookup"><span data-stu-id="ee9ee-198">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee9ee-199">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee9ee-199">See also</span></span>

- [<span data-ttu-id="ee9ee-200">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="ee9ee-200">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
