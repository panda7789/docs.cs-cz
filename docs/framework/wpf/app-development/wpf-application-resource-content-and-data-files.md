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
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="0188e-102">Zdroj, obsah a datové soubory zdroje aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="0188e-102">WPF Application Resource, Content, and Data Files</span></span>
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]<span data-ttu-id="0188e-103">aplikace často závisí na soubory, které obsahují data spustitelný soubor, jako například [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrázky, videa a zvuku.</span><span class="sxs-lookup"><span data-stu-id="0188e-103"> applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]<span data-ttu-id="0188e-104">nabízí zvláštní podporu pro konfiguraci, identifikace a použití těchto typů datových souborů, které se nazývají datové soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="0188e-104"> offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="0188e-105">Tato podpora se pohybuje kolem konkrétní sadu typy souborů dat aplikace, včetně:</span><span class="sxs-lookup"><span data-stu-id="0188e-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
-   <span data-ttu-id="0188e-106">**Soubory prostředků**: datové soubory, které jsou zkompilovány do buď spustitelný soubor nebo knihovna [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-106">**Resource Files**: Data files that are compiled into either an executable or library [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
-   <span data-ttu-id="0188e-107">**Soubory obsahu**: samostatné datové soubory, které mají explicitní přidružení se spustitelný soubor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-107">**Content Files**: Standalone data files that have an explicit association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
-   <span data-ttu-id="0188e-108">**Lokality počátek souborů**: samostatné datové soubory, které mají souvislost se spustitelný soubor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-108">**Site of Origin Files**: Standalone data files that have no association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
 <span data-ttu-id="0188e-109">Jeden rozlišení, aby mezi tyto tři typy souborů je, že zdrojových souborů a soubory obsahu se ví, že v čase vytvoření buildu; sestavení má explicitní znalosti z nich.</span><span class="sxs-lookup"><span data-stu-id="0188e-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="0188e-110">Pro lokalitu zdroji souborů, ale sestavení může mít žádné znalosti z nich, nebo implicitní znalosti prostřednictvím sadu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz; v případě, není zaručeno, že odkazovaného webu zdrojový soubor skutečně existuje.</span><span class="sxs-lookup"><span data-stu-id="0188e-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="0188e-111">Chcete-li datové soubory aplikace [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] používá sada [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] schéma, které je podrobně popsaná v [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="0188e-111">To reference application data files, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uses the Pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Scheme, which is described in detail in [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="0188e-112">Toto téma popisuje, jak konfigurovat a používat soubory dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="0188e-112">This topic describes how to configure and use application data files.</span></span>  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a><span data-ttu-id="0188e-113">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="0188e-113">Resource Files</span></span>  
 <span data-ttu-id="0188e-114">Pokud datového souboru aplikace musí být vždy k dispozici pro aplikace, je jediným způsobem, jak zajistit dostupnost kompilována hlavní spustitelný soubor sestavení aplikace nebo jednoho z jeho odkazovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="0188e-115">Tento typ datového souboru aplikace se označuje jako *souboru prostředků*.</span><span class="sxs-lookup"><span data-stu-id="0188e-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="0188e-116">Měli byste použít prostředků soubory, když:</span><span class="sxs-lookup"><span data-stu-id="0188e-116">You should use resource files when:</span></span>  
  
-   <span data-ttu-id="0188e-117">Nemusíte aktualizovat obsah souboru prostředků poté, co se zkompiluje do sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
-   <span data-ttu-id="0188e-118">Chcete zjednodušit složitost distribuce aplikací snížením počtu závislostech souborů.</span><span class="sxs-lookup"><span data-stu-id="0188e-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
-   <span data-ttu-id="0188e-119">Vašeho datového souboru aplikace, je potřeba lokalizovatelný (viz [WPF globalizace a lokalizace přehled](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="0188e-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0188e-120">Soubory prostředků, které jsou popsané v této části jsou jiné než soubory prostředků popsaných v [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md) a jiné než vložené nebo propojené prostředky, které jsou popsané v [Správa prostředků aplikace (.NET) ](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).</span><span class="sxs-lookup"><span data-stu-id="0188e-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) and different than the embedded or linked resources described in [Managing Application Resources (.NET)](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="0188e-121">Konfigurace soubory prostředků</span><span class="sxs-lookup"><span data-stu-id="0188e-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="0188e-122">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], soubor prostředků je soubor, který je součástí [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Resource` položky.</span><span class="sxs-lookup"><span data-stu-id="0188e-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a resource file is a file that is included in an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as a `Resource` item.</span></span>  
  
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
>  <span data-ttu-id="0188e-123">V [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vytvořte soubor prostředků přidáním souboru do projektu a nastavení jeho `Build Action` k `Resource`.</span><span class="sxs-lookup"><span data-stu-id="0188e-123">In [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="0188e-124">Při sestavení projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kompilovaný prostředku do sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-124">When the project is built, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="0188e-125">Pomocí soubory prostředků</span><span class="sxs-lookup"><span data-stu-id="0188e-125">Using Resource Files</span></span>  
 <span data-ttu-id="0188e-126">Chcete-li načíst soubor prostředků, můžete zavolat <xref:System.Windows.Application.GetResourceStream%2A> metodu <xref:System.Windows.Application> třídy a předejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující souboru požadovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="0188e-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired resource file.</span></span> <span data-ttu-id="0188e-127"><xref:System.Windows.Application.GetResourceStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zveřejňuje soubor prostředků jako <xref:System.IO.Stream> a popisuje typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="0188e-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="0188e-128">Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetResourceStream%2A> načíst <xref:System.Windows.Controls.Page> prostředků souborů a nastavte jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`):</span><span class="sxs-lookup"><span data-stu-id="0188e-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="0188e-129">Při volání <xref:System.Windows.Application.GetResourceStream%2A> dává vám přístup k <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, který jste budete nastavení, je další práci.</span><span class="sxs-lookup"><span data-stu-id="0188e-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="0188e-130">Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnost typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0188e-130">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="0188e-131">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0188e-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="0188e-132">Následující příklad je kód ekvivalentní v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0188e-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="0188e-133">Soubory aplikace kódu jako soubory prostředků</span><span class="sxs-lookup"><span data-stu-id="0188e-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="0188e-134">Speciální sadu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] soubory kódu aplikace můžete odkazovat pomocí pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně systému windows, stránky, tok dokumenty a slovnících prostředků.</span><span class="sxs-lookup"><span data-stu-id="0188e-134">A special set of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application code files can be referenced using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="0188e-135">Například můžete nastavit <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> vlastnost s sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] okno nebo stránka, která se má načíst při spuštění aplikace, který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="0188e-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="0188e-136">Můžete provést při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je součástí [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Page` položky.</span><span class="sxs-lookup"><span data-stu-id="0188e-136">You can do this when a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is included in an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as a `Page` item.</span></span>  
  
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
>  <span data-ttu-id="0188e-137">V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], můžete přidat novou <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, nebo <xref:System.Windows.ResourceDictionary> do projektu, `Build Action` pro značku použije výchozí soubor `Page`.</span><span class="sxs-lookup"><span data-stu-id="0188e-137">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="0188e-138">Když na projekt s `Page` kompiluje položky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] položky jsou převedeny na binární formát a zkompilovat do přidružené sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="0188e-139">V důsledku toho tyto soubory můžete použít stejným způsobem jako soubory typické prostředků.</span><span class="sxs-lookup"><span data-stu-id="0188e-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0188e-140">Pokud [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru je nakonfigurovaný jako `Resource` položky a nemá souboru kódu na pozadí, nezpracovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zkompilován sestavení spíše než binární verzi nezpracovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0188e-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a><span data-ttu-id="0188e-141">Soubory obsahu</span><span class="sxs-lookup"><span data-stu-id="0188e-141">Content Files</span></span>  
 <span data-ttu-id="0188e-142">A *obsahu souboru* je distribuován jako soubor přijít společně se spustitelný soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="0188e-143">I když nejsou se zkompiluje do sestavení, sestavení jsou kompilovat s metadata, která vytvoří přidružení se jednotlivé soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="0188e-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="0188e-144">Měli byste použít soubory obsahu, když vaše aplikace vyžaduje konkrétní sadu datové soubory aplikace, které chcete mít možnost aktualizovat bez nutnosti rekompilace sestavení, které využívá je.</span><span class="sxs-lookup"><span data-stu-id="0188e-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="0188e-145">Konfigurace souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="0188e-145">Configuring Content Files</span></span>  
 <span data-ttu-id="0188e-146">Pokud chcete přidat do projektu soubor obsahu, musí být zahrnut jako datového souboru aplikace `Content` položky.</span><span class="sxs-lookup"><span data-stu-id="0188e-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="0188e-147">Kromě toho, protože soubor obsahu není zkompilovat přímo do sestavení, je nutné nastavit [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` element metadat k určení, zda soubor obsahu zkopírován do umístění, která je relativní k integrovaný sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="0188e-148">Pokud chcete prostředek zkopírovány do výstupní složky sestavení pokaždé, když je založený na projekt, nastavíte `CopyToOutputDirectory` element metadat s `Always` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0188e-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="0188e-149">Jinak, můžete zajistit, že je pouze nejnovější verzi prostředku zkopírovány do výstupní složky sestavení pomocí `PreserveNewest` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0188e-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="0188e-150">Na obrázku je soubor, který je konfigurován jako soubor obsahu, který se zkopíruje do sestavení výstupu složky pouze v případě, že nová verze prostředku se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="0188e-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
>  <span data-ttu-id="0188e-151">V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vytvořte soubor obsahu přidáním souboru do projektu a nastavení jeho `Build Action` k `Content`a nastavit jeho `Copy to Output Directory` k `Copy always` (stejné jako `Always`) a `Copy if newer` (stejné jako `PreserveNewest`).</span><span class="sxs-lookup"><span data-stu-id="0188e-151">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="0188e-152">Při sestavení projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut kompiluje na metadata sestavení pro jednotlivé soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="0188e-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="0188e-153">Hodnota <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> znamená cestu k souboru obsahu vzhledem ke své pozici v projektu.</span><span class="sxs-lookup"><span data-stu-id="0188e-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="0188e-154">Například pokud byl soubor obsahu umístěné v podsložce projektu, další informace o cestě by být součástí <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0188e-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="0188e-155"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Hodnota je také s hodnotou obsahující cestu k souboru obsahu do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="0188e-156">Pomocí souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="0188e-156">Using Content Files</span></span>  
 <span data-ttu-id="0188e-157">Chcete-li načíst soubor obsahu, můžete zavolat <xref:System.Windows.Application.GetContentStream%2A> metodu <xref:System.Windows.Application> třídy a předejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující soubor požadovaného obsahu.</span><span class="sxs-lookup"><span data-stu-id="0188e-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired content file.</span></span> <span data-ttu-id="0188e-158"><xref:System.Windows.Application.GetContentStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zveřejňuje soubor obsahu jako <xref:System.IO.Stream> a popisuje typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="0188e-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="0188e-159">Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetContentStream%2A> načíst <xref:System.Windows.Controls.Page> obsahu souboru a nastavte jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`).</span><span class="sxs-lookup"><span data-stu-id="0188e-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="0188e-160">Při volání <xref:System.Windows.Application.GetContentStream%2A> dává vám přístup k <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, který jste budete nastavení, je další práci.</span><span class="sxs-lookup"><span data-stu-id="0188e-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="0188e-161">Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnost typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0188e-161">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="0188e-162">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0188e-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="0188e-163">Následující příklad je kód ekvivalentní v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0188e-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a><span data-ttu-id="0188e-164">Lokality počátek souborů</span><span class="sxs-lookup"><span data-stu-id="0188e-164">Site of Origin Files</span></span>  
 <span data-ttu-id="0188e-165">Soubory prostředků mít relaci explicitní s sestavení, které jsou distribuovány společně, podle definice <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0188e-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="0188e-166">Ale existují časy, kdy můžete chtít vytvořit buď neexistující nebo implicitní vztah mezi sestavení a souboru dat aplikace, včetně při:</span><span class="sxs-lookup"><span data-stu-id="0188e-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
-   <span data-ttu-id="0188e-167">Soubor neexistuje, když v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0188e-167">A file doesn't exist when at compile time.</span></span>  
  
-   <span data-ttu-id="0188e-168">Nevíte, jaké soubory vaše sestavení bude vyžadovat až při spuštění.</span><span class="sxs-lookup"><span data-stu-id="0188e-168">You don't know what files your assembly will require until run time.</span></span>  
  
-   <span data-ttu-id="0188e-169">Chcete mít možnost aktualizovat soubory bez nutnosti rekompilace sestavení, které jsou přidruženy.</span><span class="sxs-lookup"><span data-stu-id="0188e-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
-   <span data-ttu-id="0188e-170">Vaše aplikace používá velké datové soubory, jako je například audio a video, a chcete pouze uživatelům, pokud se rozhodnete je stáhnout.</span><span class="sxs-lookup"><span data-stu-id="0188e-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="0188e-171">Je možné načíst tyto typy souborů pomocí tradiční [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schémata, jako je například schémata file:/// a http://.</span><span class="sxs-lookup"><span data-stu-id="0188e-171">It is possible to load these types of files by using traditional [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="0188e-172">Schémata file:/// a http:// ale vyžadují vaše aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="0188e-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="0188e-173">Pokud je vaše aplikace [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] který byl spuštěn z Internetu nebo intranetu, a požaduje jenom na sadu oprávnění, která jsou povoleny pro spuštění z těchto umístění aplikace volné soubory mohou být načteny pouze ze serveru aplikace z původu ( Spusťte umístění).</span><span class="sxs-lookup"><span data-stu-id="0188e-173">If your application is a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="0188e-174">Tyto soubory se označují jako *lokality původu* soubory.</span><span class="sxs-lookup"><span data-stu-id="0188e-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="0188e-175">Lokality počátek soubory jsou jenom možnosti pro aplikace s částečnou důvěryhodností, i když jsou mimo jiné aplikace s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="0188e-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="0188e-176">Aplikace úplný vztah důvěryhodnosti je stále nutné načíst soubory dat aplikace, které budou neznáte o v čase vytvoření buildu; Při úplný vztah důvěryhodnosti aplikace může používat file:///, je pravděpodobné, že datové soubory aplikace se nainstaluje ve stejné složce jako, nebo na podsložku ve sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="0188e-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="0188e-177">V takovém případě pomocí lokality odkazující na počátku je jednodušší než použití file:///, protože pomocí file:/// vyžaduje, abyste vycházejí úplnou cestu souboru.</span><span class="sxs-lookup"><span data-stu-id="0188e-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0188e-178">Lokality původu soubory se neukládají do mezipaměti s [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] na klientský počítač, když jsou soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="0188e-178">Site of origin files are not cached with an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] on a client machine, while content files are.</span></span> <span data-ttu-id="0188e-179">V důsledku toho pouze stáhnou se konkrétně vyžádání.</span><span class="sxs-lookup"><span data-stu-id="0188e-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="0188e-180">Pokud [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] aplikace má velké soubory médií, je konfigurace, protože lokality počátek souborů znamená spuštění počáteční aplikace je mnohem rychlejší a soubory staženy pouze na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="0188e-180">If an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="0188e-181">Konfigurace lokality počátek souborů</span><span class="sxs-lookup"><span data-stu-id="0188e-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="0188e-182">Pokud váš web počátek soubory jsou neexistující nebo neznámé v době kompilace, budete muset použít tradiční nasazení mechanismy pro zajištění požadované soubory jsou k dispozici v době běhu, včetně použití buď `XCopy` příkazového řádku programu nebo [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0188e-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].</span></span>  
  
 <span data-ttu-id="0188e-183">Pokud znáte v době kompilace soubory, které byste chtěli být umístěny v lokalitě původu, ale stále se chcete vyhnout explicitní závislosti, můžete přidat těchto souborů do [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="0188e-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as `None` item.</span></span> <span data-ttu-id="0188e-184">Jak se soubory obsahu, musíte nastavit [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` atribut k určení, zda webu zdrojový soubor zkopírován do umístění, která je relativní k integrovaný sestavení zadáním buď `Always` hodnotu nebo `PreserveNewest` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0188e-184">As with content files, you need to set the [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
>  <span data-ttu-id="0188e-185">V [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vytvoření webu zdrojový soubor přidáním souboru do projektu a nastavení jeho `Build Action` k `None`.</span><span class="sxs-lookup"><span data-stu-id="0188e-185">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="0188e-186">Při sestavení projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] zkopíruje zadané soubory do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="0188e-186">When the project is built, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="0188e-187">Pomocí lokality počátek souborů</span><span class="sxs-lookup"><span data-stu-id="0188e-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="0188e-188">Chcete-li načíst lokality zdrojový soubor, můžete zavolat <xref:System.Windows.Application.GetRemoteStream%2A> metodu <xref:System.Windows.Application> třídy a předejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující požadovaného webu zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="0188e-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired site of origin file.</span></span> <span data-ttu-id="0188e-189"><xref:System.Windows.Application.GetRemoteStream%2A>Vrátí <xref:System.Windows.Resources.StreamResourceInfo> objekt, který zveřejňuje lokalitě jako zdrojový soubor <xref:System.IO.Stream> a popisuje typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="0188e-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="0188e-190">Například následující kód ukazuje, jak používat <xref:System.Windows.Application.GetRemoteStream%2A> načíst <xref:System.Windows.Controls.Page> lokality původu souboru a nastavte jej jako obsah <xref:System.Windows.Controls.Frame> (`pageFrame`).</span><span class="sxs-lookup"><span data-stu-id="0188e-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="0188e-191">Při volání <xref:System.Windows.Application.GetRemoteStream%2A> dává vám přístup k <xref:System.IO.Stream>, je třeba provést převod na typ vlastnosti, který jste budete nastavení, je další práci.</span><span class="sxs-lookup"><span data-stu-id="0188e-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="0188e-192">Místo toho můžete nechat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] postará o otevření a převod <xref:System.IO.Stream> načtením souboru prostředků přímo do vlastnost typu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0188e-192">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="0188e-193">Následující příklad ukazuje, jak načíst <xref:System.Windows.Controls.Page> přímo do <xref:System.Windows.Controls.Frame> (`pageFrame`) pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0188e-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="0188e-194">Následující příklad je kód ekvivalentní v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0188e-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="0188e-195">Opětovné sestavení po změně typu sestavení</span><span class="sxs-lookup"><span data-stu-id="0188e-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="0188e-196">Po provedení změny sestavení typ datového souboru aplikace, budete muset znovu sestavte celé aplikace k zajištění, že tyto změny se použijí.</span><span class="sxs-lookup"><span data-stu-id="0188e-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="0188e-197">Pokud vytvoříte pouze aplikace, nejsou použity změny.</span><span class="sxs-lookup"><span data-stu-id="0188e-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0188e-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="0188e-198">See Also</span></span>  
 [<span data-ttu-id="0188e-199">Identifikátory URI Pack v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="0188e-199">Pack URIs in WPF</span></span>](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
