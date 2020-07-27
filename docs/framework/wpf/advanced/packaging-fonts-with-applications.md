---
title: Balení písem s aplikacemi
description: Naučte se zabalit písma pomocí Windows Presentation Foundation aplikace, včetně přidání písem jako obsahu a položek prostředků a omezení využití písma.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: 725f05c22eda199d86e5ec5dbb6bdd899ee66a5d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166351"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="f1a6b-103">Balení písem s aplikacemi</span><span class="sxs-lookup"><span data-stu-id="f1a6b-103">Packaging Fonts with Applications</span></span>
<span data-ttu-id="f1a6b-104">Toto téma poskytuje přehled o tom, jak zabalit písma s vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-104">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1a6b-105">Stejně jako u většiny typů softwaru jsou soubory písem licencované a nikoli prodávatelné.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-105">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="f1a6b-106">Licence, které řídí použití písem, se liší od dodavatele k dodavatelům, ale obecně většinou licencí, včetně těch, které se týkají písem, která Microsoft dodává s aplikacemi a Windows, nedovolují vkládání písem do aplikací ani jiné distribuci.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-106">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="f1a6b-107">Proto je jako vývojář zodpovědný za to, že máte požadovaná licenční práva pro všechna písma vložená v rámci aplikace nebo jinak znovu distribuovat.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-107">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="f1a6b-108">Úvod do balení písem</span><span class="sxs-lookup"><span data-stu-id="f1a6b-108">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="f1a6b-109">Můžete snadno zabalit písma jako prostředky v rámci svých [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, aby se zobrazil text uživatelského rozhraní a další typy textových obsahu.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-109">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="f1a6b-110">Písma mohou být oddělena nebo vložena do souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-110">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="f1a6b-111">Můžete také vytvořit knihovnu písem pouze pro prostředky, kterou může vaše aplikace odkazovat.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-111">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="f1a6b-112">Písma OpenType a TrueType® obsahují příznak typu fsType, který označuje licenční práva pro vkládání písem.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-112">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="f1a6b-113">Tento příznak typu se však vztahuje pouze na vložená písma uložená v dokumentu – neodkazuje se na písma vložená v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-113">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="f1a6b-114">Můžete načíst práva pro vkládání písma pro písmo vytvořením <xref:System.Windows.Media.GlyphTypeface> objektu a odkazování na jeho <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-114">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="f1a6b-115">Další informace o příznaku fsType najdete v části "OS/2 a metriky Windows" v tématu [specifikace OpenType](https://www.microsoft.com/typography/otspec/os2.htm) .</span><span class="sxs-lookup"><span data-stu-id="f1a6b-115">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="f1a6b-116">Web [Typografie společnosti Microsoft](https://docs.microsoft.com/typography/) obsahuje kontaktní informace, které vám pomůžou najít konkrétního dodavatele písma nebo najít dodavatele písma pro vlastní práci.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-116">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="f1a6b-117">Přidání písem jako položek obsahu</span><span class="sxs-lookup"><span data-stu-id="f1a6b-117">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="f1a6b-118">Do aplikace můžete přidat písma jako položky obsahu projektu, které jsou oddělené od souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-118">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="f1a6b-119">To znamená, že položky obsahu nejsou vloženy jako prostředky v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-119">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="f1a6b-120">Následující příklad souboru projektu ukazuje, jak definovat položky obsahu.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-120">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="f1a6b-121">Aby bylo zajištěno, že aplikace bude moci používat písma v době běhu, musí být písma přístupná v adresáři nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-121">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="f1a6b-122">`<CopyToOutputDirectory>`Element v souboru projektu aplikace umožňuje automaticky Kopírovat písma do adresáře nasazení aplikace během procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-122">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="f1a6b-123">Následující příklad souboru projektu ukazuje, jak zkopírovat písma do adresáře nasazení.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-123">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="f1a6b-124">Následující příklad kódu ukazuje, jak odkazovat na písmo aplikace jako položku obsahu – odkazovaná položka obsahu musí být ve stejném adresáři jako soubory sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-124">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="f1a6b-125">Přidávání písem jako položek prostředků</span><span class="sxs-lookup"><span data-stu-id="f1a6b-125">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="f1a6b-126">Do aplikace můžete přidat písma jako položky prostředků projektu, které jsou vloženy do souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-126">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="f1a6b-127">Použití samostatného podadresáře pro prostředky pomáhá organizovat soubory projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-127">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="f1a6b-128">Následující příklad souboru projektu ukazuje, jak definovat písma jako položky prostředků v samostatném podadresáři.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-128">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
> <span data-ttu-id="f1a6b-129">Když přidáte písma jako prostředky do aplikace, ujistěte se, že nastavujete `<Resource>` prvek a nikoli `<EmbeddedResource>` element v souboru projektu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-129">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="f1a6b-130">`<EmbeddedResource>`Element pro akci sestavení není podporován.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-130">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="f1a6b-131">Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-131">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="f1a6b-132">Odkazování na položky prostředků písma z kódu</span><span class="sxs-lookup"><span data-stu-id="f1a6b-132">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="f1a6b-133">Chcete-li odkazovat na položky prostředků písma z kódu, je nutné dodat odkaz na prostředek o dvou částech: základní identifikátor URI (Uniform Resource Identifier); a odkaz na umístění písma.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-133">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="f1a6b-134">Tyto hodnoty se používají jako parametry pro <xref:System.Windows.Media.FontFamily.%23ctor%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-134">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="f1a6b-135">Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace v podadresáři projektu s názvem `resources` .</span><span class="sxs-lookup"><span data-stu-id="f1a6b-135">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="f1a6b-136">Základní identifikátor URI (Uniform Resource Identifier) může zahrnovat podadresář aplikace, ve kterém se nachází prostředek písma.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-136">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="f1a6b-137">V takovém případě by odkaz na umístění písma nemusel zadat adresář, ale musel by obsahovat úvodní znak " `./` ", což znamená, že se prostředek písma nachází ve stejném adresáři určeném základním identifikátorem URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="f1a6b-137">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="f1a6b-138">Následující příklad kódu ukazuje alternativní způsob odkazování na položku prostředku písma – je ekvivalentní k předchozímu příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-138">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="f1a6b-139">Odkazování na písma ze stejného podadresáře aplikace</span><span class="sxs-lookup"><span data-stu-id="f1a6b-139">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="f1a6b-140">Můžete umístit obsah aplikace i soubory prostředků do stejného uživatelsky definovaného podadresáře projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-140">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="f1a6b-141">Následující příklad souboru projektu ukazuje stránku obsahu a prostředky písem definované ve stejném podadresáři.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-141">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="f1a6b-142">Vzhledem k tomu, že je obsah aplikace a písmo ve stejném podadresáři, je odkaz na písmo relativní vzhledem k obsahu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-142">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="f1a6b-143">Následující příklady ukazují, jak odkazovat na prostředek písma aplikace, když je písmo ve stejném adresáři jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-143">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="f1a6b-144">Vyčíslení písem v aplikaci</span><span class="sxs-lookup"><span data-stu-id="f1a6b-144">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="f1a6b-145">Chcete-li vytvořit výčet písem jako položek prostředků v aplikaci, použijte <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> buď <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metodu, nebo.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-145">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="f1a6b-146">Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metodu pro vrácení kolekce <xref:System.Windows.Media.FontFamily> objektů z umístění písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-146">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="f1a6b-147">V tomto případě aplikace obsahuje podadresář s názvem "Resources".</span><span class="sxs-lookup"><span data-stu-id="f1a6b-147">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="f1a6b-148">Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metodu pro vrácení kolekce <xref:System.Windows.Media.Typeface> objektů z umístění písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-148">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="f1a6b-149">V tomto případě aplikace obsahuje podadresář s názvem "Resources".</span><span class="sxs-lookup"><span data-stu-id="f1a6b-149">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="f1a6b-150">Vytvoření knihovny prostředků písma</span><span class="sxs-lookup"><span data-stu-id="f1a6b-150">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="f1a6b-151">Můžete vytvořit knihovnu pouze pro prostředky, která obsahuje pouze písma – žádný kód není součástí tohoto typu projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-151">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="f1a6b-152">Vytváření knihovny pouze pro prostředky je běžnou technikou pro oddělení prostředků z kódu aplikace, který je používá.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-152">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="f1a6b-153">To umožňuje také zahrnutí sestavení knihovny do více projektů aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-153">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="f1a6b-154">Následující příklad souboru projektu ukazuje klíčové části projektu knihovny pouze s prostředky.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-154">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="f1a6b-155">Odkazování na písmo v knihovně prostředků</span><span class="sxs-lookup"><span data-stu-id="f1a6b-155">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="f1a6b-156">Chcete-li odkazovat na písmo v knihovně prostředků z vaší aplikace, je nutné odkaz na písmo prefixovat názvem sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-156">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="f1a6b-157">V tomto případě je sestavení prostředků písma "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="f1a6b-157">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="f1a6b-158">Chcete-li název sestavení oddělit od odkazu v rámci sestavení, použijte znak ";".</span><span class="sxs-lookup"><span data-stu-id="f1a6b-158">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="f1a6b-159">Přidání klíčového slova Component, za nímž následuje odkaz na název písma, dokončí úplný odkaz na prostředek knihovny písem.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-159">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="f1a6b-160">Následující příklad kódu ukazuje, jak odkazovat na písmo v sestavení knihovny prostředků.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-160">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="f1a6b-161">Tato sada SDK obsahuje sadu ukázkových písem OpenType, která můžete používat s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-161">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="f1a6b-162">Písma jsou definována v knihovně určené pouze pro prostředky.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-162">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="f1a6b-163">Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f1a6b-163">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="f1a6b-164">Omezení používání písem</span><span class="sxs-lookup"><span data-stu-id="f1a6b-164">Limitations on Font Usage</span></span>  
 <span data-ttu-id="f1a6b-165">Následující seznam popisuje několik omezení pro balení a používání písem v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacích:</span><span class="sxs-lookup"><span data-stu-id="f1a6b-165">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="f1a6b-166">**Bity oprávnění k vkládání písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nekontrolují ani vynutily žádné bity oprávnění vkládání písem.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-166">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="f1a6b-167">Další informace najdete v části [Introduction_to_Packing písma](#introduction_to_packaging_fonts) .</span><span class="sxs-lookup"><span data-stu-id="f1a6b-167">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="f1a6b-168">**Umístění původních písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepovolují odkaz na písmo na identifikátor URI http nebo FTP (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="f1a6b-168">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="f1a6b-169">**Absolutní identifikátor URI pomocí balíčku: Notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují vytvořit <xref:System.Windows.Media.FontFamily> objekt programově pomocí příkazu Pack: jako součást absolutního odkazu na identifikátor URI (Uniform Resource Identifier) na písmo.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-169">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="f1a6b-170">Například `"pack://application:,,,/resources/#Pericles Light"` je neplatný odkaz na písmo.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-170">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="f1a6b-171">**Automatické vkládání písem:** Během návrhu není dostupná žádná podpora pro hledání použití písem aplikace a automatické vkládání písem do prostředků aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-171">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="f1a6b-172">**Podsady písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepodporují vytváření podmnožin písem pro nepevné dokumenty.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-172">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="f1a6b-173">V případech, kdy je k dispozici nesprávný odkaz, se aplikace vrátí k použití dostupného písma.</span><span class="sxs-lookup"><span data-stu-id="f1a6b-173">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a6b-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1a6b-174">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="f1a6b-175">Typografie Microsoft – odkazy, novinky a kontakty</span><span class="sxs-lookup"><span data-stu-id="f1a6b-175">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="f1a6b-176">Specifikace OpenType</span><span class="sxs-lookup"><span data-stu-id="f1a6b-176">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="f1a6b-177">Funkce písma OpenType</span><span class="sxs-lookup"><span data-stu-id="f1a6b-177">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="f1a6b-178">Ukázková sada písem OpenType</span><span class="sxs-lookup"><span data-stu-id="f1a6b-178">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
