---
title: "Balení písem s aplikacemi"
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
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3860aff69b0e4e7a3dc624898cc6b1daa0dd092
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="65d6f-102">Balení písem s aplikacemi</span><span class="sxs-lookup"><span data-stu-id="65d6f-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="65d6f-103">Toto téma obsahuje základní informace o na balíček písma s vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65d6f-104">Stejně jako u většiny typů softwaru písma souborů jsou licenci, a nikoli prodávána.</span><span class="sxs-lookup"><span data-stu-id="65d6f-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="65d6f-105">Licence, které budou řídit použití písem lišit od dodavatele dodavatele, ale obecně většina licence, včetně těch, který po sobě zakrývá písma [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] poskytuje s aplikacemi a [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], zakázat písem vložených v aplikacích nebo jinak hodnota znovu distribuovat.</span><span class="sxs-lookup"><span data-stu-id="65d6f-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="65d6f-106">Proto jako vývojář, který je vaší povinností ujistit, že máte požadovanou licenci práva pro libovolného písma, které vložení v rámci aplikace nebo jinak znovu distribuovat.</span><span class="sxs-lookup"><span data-stu-id="65d6f-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="65d6f-107">Úvod do balení písem</span><span class="sxs-lookup"><span data-stu-id="65d6f-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="65d6f-108">Můžete snadno sbalit písem jako prostředky v rámci vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace zobrazíte text v uživatelském rozhraní a dalších typů text na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="65d6f-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="65d6f-109">Písma může být oddělené od nebo vložené v rámci soubory sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="65d6f-110">Můžete také vytvořit pouze písma knihovny, která vaše aplikace, můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="65d6f-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]<span data-ttu-id="65d6f-111">a [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] písem obsahovat typ příznak fsType, určující písma vložení licenční práva pro písmo.</span><span class="sxs-lookup"><span data-stu-id="65d6f-111"> and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="65d6f-112">Tento typ, který příznak se vztahuje pouze na vložená písma, které jsou uložené v dokumentu – it však neodkazuje na písem v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="65d6f-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="65d6f-113">Můžete načíst vložení práva pro písmo vytvořením písma <xref:System.Windows.Media.GlyphTypeface> objekt a odkazování na jeho <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65d6f-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="65d6f-114">Informace naleznete v sekci "OS/2 a Windows metrik" z [OpenType specifikace](http://www.microsoft.com/typography/otspec/os2.htm) Další informace o příznak fsType.</span><span class="sxs-lookup"><span data-stu-id="65d6f-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](http://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="65d6f-115">[Microsoft Typography](http://www.microsoft.com/typography/links/) webový server obsahuje kontaktní informace, které vám může pomoct najít dodavatele zvolené písmo k dispozici nebo najít dodavatele písma pro vlastní pracovní.</span><span class="sxs-lookup"><span data-stu-id="65d6f-115">The [Microsoft Typography](http://www.microsoft.com/typography/links/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="65d6f-116">Přidání písem jako položky obsahu</span><span class="sxs-lookup"><span data-stu-id="65d6f-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="65d6f-117">Písma můžete přidat do vaší aplikace jako obsahu položky projektu, které jsou oddělené od soubory sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="65d6f-118">To znamená, že obsahu položky nejsou vloženy jako prostředky v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="65d6f-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="65d6f-119">Následující příklad souboru projektu ukazuje, jak k definování položek obsahu.</span><span class="sxs-lookup"><span data-stu-id="65d6f-119">The following project file example shows how to define content items.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 <span data-ttu-id="65d6f-120">Aby se zajistilo, že aplikace můžete použít písma v době běhu, písma musí být dostupný v adresáři nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="65d6f-121">`<CopyToOutputDirectory>` Element v souboru projektu aplikace umožňuje automaticky kopírovat písma k adresáři nasazení aplikace během procesu vytváření.</span><span class="sxs-lookup"><span data-stu-id="65d6f-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="65d6f-122">Následující příklad souboru projektu ukazuje, jak zkopírovat do adresáře nasazení písem.</span><span class="sxs-lookup"><span data-stu-id="65d6f-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 <span data-ttu-id="65d6f-123">Následující příklad kódu ukazuje, jak chcete-li písmo aplikace jako položku obsahu – odkazovaná položka obsahu musí být ve stejném adresáři jako soubory sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="65d6f-124">Přidání písem jako položky prostředků</span><span class="sxs-lookup"><span data-stu-id="65d6f-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="65d6f-125">Písma můžete přidat do vaší aplikace jako položky projektu prostředků, které jsou vloženy do souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="65d6f-126">Používání samostatné podadresáři pro prostředky přispívá k uspořádání souborů projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="65d6f-127">Následující příklad souboru projektu ukazuje, jak definovat jako položky prostředků v samostatných podadresáři písem.</span><span class="sxs-lookup"><span data-stu-id="65d6f-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  <span data-ttu-id="65d6f-128">Když přidáte písem jako prostředky do vaší aplikace, ujistěte se, jsou nastavení `<Resource>` elementu a ne `<EmbeddedResource>` element v souboru projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="65d6f-129">`<EmbeddedResource>` Element pro akce sestavení není podporován.</span><span class="sxs-lookup"><span data-stu-id="65d6f-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="65d6f-130">Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="65d6f-131">Odkazy na písma prostředků položky z kódu</span><span class="sxs-lookup"><span data-stu-id="65d6f-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="65d6f-132">Chcete-li odkazovat na položky prostředků písma z kódu, je nutné zadat odkaz na prostředků písma dvě části: základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; a odkaz na umístění písma.</span><span class="sxs-lookup"><span data-stu-id="65d6f-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="65d6f-133">Tyto hodnoty jsou použity jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="65d6f-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="65d6f-134">Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace v podadresáři projektu s názvem `resources`.</span><span class="sxs-lookup"><span data-stu-id="65d6f-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="65d6f-135">Základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] může zahrnovat podadresář aplikace, kde se nachází prostředků písma.</span><span class="sxs-lookup"><span data-stu-id="65d6f-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="65d6f-136">V takovém případě není potřeba zadávat adresář umístění odkaz na písma, ale by měl zahrnovat jako úvodní "`./`", což naznačuje písma prostředek je ve stejném adresáři určeného základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65d6f-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="65d6f-137">Následující příklad kódu ukazuje alternativní způsob odkazující na položce prostředků písma – je ekvivalentní k předchozí příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="65d6f-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="65d6f-138">Odkazy na písma z stejném podadresáři aplikace</span><span class="sxs-lookup"><span data-stu-id="65d6f-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="65d6f-139">Můžete umístit obě aplikace obsahu a zdrojové soubory ve stejném podadresáři uživatelem definované projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="65d6f-140">Následující příklad souboru projektu zobrazuje stránku obsahu a definované ve stejném podadresáři prostředky písma.</span><span class="sxs-lookup"><span data-stu-id="65d6f-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="65d6f-141">Vzhledem k tomu, že obsah aplikace a písma jsou ve stejném podadresáři, odkaz písma je relativní vzhledem k obsahu aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="65d6f-142">Následující příklady ukazují, jak odkazovat prostředků písma, pokud písmo je ve stejném adresáři jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="65d6f-143">Vytváření výčtu písem v aplikaci</span><span class="sxs-lookup"><span data-stu-id="65d6f-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="65d6f-144">Zobrazení výčtu písem jako položky prostředků ve vaší aplikaci, použijte buď <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> nebo <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="65d6f-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="65d6f-145">Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metoda vrátí kolekci <xref:System.Windows.Media.FontFamily> objekty z umístění písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="65d6f-146">V takovém případě aplikace obsahuje podadresáři s názvem "zdroje".</span><span class="sxs-lookup"><span data-stu-id="65d6f-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="65d6f-147">Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metoda vrátí kolekci <xref:System.Windows.Media.Typeface> objekty z umístění písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="65d6f-148">V takovém případě aplikace obsahuje podadresáři s názvem "zdroje".</span><span class="sxs-lookup"><span data-stu-id="65d6f-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="65d6f-149">Vytvoření prostředku knihovny písma</span><span class="sxs-lookup"><span data-stu-id="65d6f-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="65d6f-150">Můžete vytvořit pouze prostředky knihovny, která obsahuje pouze písma – bez kódu je součástí tento typ projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="65d6f-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="65d6f-151">Vytvoření pouze knihovny je běžné technika pro oddělení prostředky z aplikační kód, který používá je.</span><span class="sxs-lookup"><span data-stu-id="65d6f-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="65d6f-152">To také umožňuje sestavení knihovny zahrnuty s více projekty aplikací.</span><span class="sxs-lookup"><span data-stu-id="65d6f-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="65d6f-153">Následující příklad souboru projektu ukazuje části klíče projektu knihovny jen prostředků.</span><span class="sxs-lookup"><span data-stu-id="65d6f-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="65d6f-154">Odkazy na písma v knihovně prostředků</span><span class="sxs-lookup"><span data-stu-id="65d6f-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="65d6f-155">Chcete-li písmo v knihovně prostředků z vaší aplikace, musíte přidat předponu odkaz na písma s názvem sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="65d6f-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="65d6f-156">V takovém případě je sestavení prostředků písma "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="65d6f-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="65d6f-157">Chcete-li samostatné název sestavení z odkazu v rámci sestavení, použijte znak ';'.</span><span class="sxs-lookup"><span data-stu-id="65d6f-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="65d6f-158">Přidání následuje odkaz na název písma – klíčové slovo "Component" dokončení úplné odkaz na prostředek knihovny písma.</span><span class="sxs-lookup"><span data-stu-id="65d6f-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="65d6f-159">Následující příklad kódu ukazuje, jak chcete-li písmo v sestavení prostředků knihovny.</span><span class="sxs-lookup"><span data-stu-id="65d6f-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="65d6f-160">Tato sada SDK obsahuje sadu ukázka [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma, která můžete použít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-160">This SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="65d6f-161">Písma jsou definovány v knihovně jen prostředků.</span><span class="sxs-lookup"><span data-stu-id="65d6f-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="65d6f-162">Další informace najdete v tématu [ukázkové sadě písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="65d6f-162">For more information, see [Sample OpenType Font Pack](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="65d6f-163">Omezení využití písma</span><span class="sxs-lookup"><span data-stu-id="65d6f-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="65d6f-164">Následující seznam popisuje několik omezení na balení a použití písem v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="65d6f-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="65d6f-165">**Vložení bity oprávnění písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací zkontrolujte nebo vynutit jakéhokoli písma vložení bity oprávnění.</span><span class="sxs-lookup"><span data-stu-id="65d6f-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="65d6f-166">Najdete v článku [Introduction_to_Packing písem](#introduction_to_packaging_fonts) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
-   <span data-ttu-id="65d6f-167">**Lokality písem původu:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují písma odkaz na protokolu http nebo ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65d6f-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
-   <span data-ttu-id="65d6f-168">**Absolutní identifikátor URI pomocí balíčku: zápis:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují vytvářet <xref:System.Windows.Media.FontFamily> objektu programově pomocí "pack:" jako součást absolutní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz na písmo.</span><span class="sxs-lookup"><span data-stu-id="65d6f-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="65d6f-169">Například `"pack://application:,,,/resources/#Pericles Light"` je odkaz na neplatný písma.</span><span class="sxs-lookup"><span data-stu-id="65d6f-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
-   <span data-ttu-id="65d6f-170">**Vkládání automatické písem:** během doby návrhu, neexistuje žádná podpora pro vyhledávání aplikace použití písem a automaticky vložení písem v prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6f-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
-   <span data-ttu-id="65d6f-171">**Písmo podmnožin:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepodporují vytvoření podmnožiny písma pro přenosné dokumenty.</span><span class="sxs-lookup"><span data-stu-id="65d6f-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
-   <span data-ttu-id="65d6f-172">V případech, kde je nesprávný referenční, aplikace se vrátí k používání dostupné písmo.</span><span class="sxs-lookup"><span data-stu-id="65d6f-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d6f-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="65d6f-173">See Also</span></span>  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [<span data-ttu-id="65d6f-174">Typografii Microsoft: Odkazy, novinky a kontakty</span><span class="sxs-lookup"><span data-stu-id="65d6f-174">Microsoft Typography: Links, News, and Contacts</span></span>](http://www.microsoft.com/typography/links/)  
 [<span data-ttu-id="65d6f-175">Specifikace OpenType</span><span class="sxs-lookup"><span data-stu-id="65d6f-175">OpenType Specification</span></span>](http://www.microsoft.com/typography/otspec/)  
 [<span data-ttu-id="65d6f-176">Funkce písma OpenType</span><span class="sxs-lookup"><span data-stu-id="65d6f-176">OpenType Font Features</span></span>](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [<span data-ttu-id="65d6f-177">Ukázková sada písem OpenType</span><span class="sxs-lookup"><span data-stu-id="65d6f-177">Sample OpenType Font Pack</span></span>](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
