---
title: Balení písem s aplikacemi
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
ms.openlocfilehash: cef2ae26ec4fccd25ca193ba7d441969f36b25a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187094"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="952aa-102">Balení písem s aplikacemi</span><span class="sxs-lookup"><span data-stu-id="952aa-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="952aa-103">Toto téma obsahuje přehled o tom, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jak zabalit písma s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="952aa-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="952aa-104">Stejně jako u většiny typů softwaru jsou soubory písem licencovány, nikoli prodávány.</span><span class="sxs-lookup"><span data-stu-id="952aa-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="952aa-105">Licence, které řídí používání písem, se u jednotlivých dodavatelů liší, ale obecně většina licencí, včetně licencí, které se týkají písem, které společnost Microsoft dodává s aplikacemi a systémem Windows, neumožňují, aby byla písma vložena do aplikací nebo jinak distribuována.</span><span class="sxs-lookup"><span data-stu-id="952aa-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="952aa-106">Proto jako vývojář je vaší odpovědností zajistit, že máte požadovaná licenční práva pro jakékoli písmo, které vložíte do aplikace nebo jinak redistribuujete.</span><span class="sxs-lookup"><span data-stu-id="952aa-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="952aa-107">Úvod do obalových písem</span><span class="sxs-lookup"><span data-stu-id="952aa-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="952aa-108">Písma můžete snadno zabalit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako prostředky v rámci aplikací a zobrazit text uživatelského rozhraní a další typy textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="952aa-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="952aa-109">Písma mohou být oddělena nebo vložena do souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="952aa-110">Můžete také vytvořit knihovnu písem pouze pro prostředky, na kterou může aplikace odkazovat.</span><span class="sxs-lookup"><span data-stu-id="952aa-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="952aa-111">Písma OpenType a TrueType® obsahují příznak typu fsType, který označuje licenční práva pro vkládání písem pro písmo.</span><span class="sxs-lookup"><span data-stu-id="952aa-111">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="952aa-112">Tento příznak typu se však vztahuje pouze na vložená písma uložená v dokumentu – neodkazuje na písma vložená do aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="952aa-113">Práva pro vkládání písma pro písmo <xref:System.Windows.Media.GlyphTypeface> můžete načíst <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> vytvořením objektu a odkazováním na jeho vlastnost.</span><span class="sxs-lookup"><span data-stu-id="952aa-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="952aa-114">Další informace o příznaku fsType naleznete v části Metriky operačního systému 2 a Windows [ve specifikaci OpenType.](https://www.microsoft.com/typography/otspec/os2.htm)</span><span class="sxs-lookup"><span data-stu-id="952aa-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="952aa-115">Web [Typografie společnosti Microsoft](https://docs.microsoft.com/typography/) obsahuje kontaktní informace, které vám mohou pomoci najít konkrétního dodavatele písma nebo najít dodavatele písma pro vlastní práci.</span><span class="sxs-lookup"><span data-stu-id="952aa-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="952aa-116">Přidání písem jako položek obsahu</span><span class="sxs-lookup"><span data-stu-id="952aa-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="952aa-117">Písma můžete přidat do aplikace jako položky obsahu projektu, které jsou oddělené od souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="952aa-118">To znamená, že položky obsahu nejsou vloženy jako prostředky v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="952aa-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="952aa-119">Následující příklad souboru projektu ukazuje, jak definovat položky obsahu.</span><span class="sxs-lookup"><span data-stu-id="952aa-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="952aa-120">Aby bylo zajištěno, že aplikace můžete používat písma za běhu, písma musí být přístupné v adresáři nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="952aa-121">Prvek `<CopyToOutputDirectory>` v souboru projektu aplikace umožňuje automaticky zkopírovat písma do adresáře nasazení aplikace během procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="952aa-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="952aa-122">Následující příklad souboru projektu ukazuje, jak zkopírovat písma do adresáře nasazení.</span><span class="sxs-lookup"><span data-stu-id="952aa-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="952aa-123">Následující příklad kódu ukazuje, jak odkazovat na písmo aplikace jako položku obsahu – odkazovaná položka obsahu musí být ve stejném adresáři jako soubory sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="952aa-124">Přidání písem jako položek zdrojů</span><span class="sxs-lookup"><span data-stu-id="952aa-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="952aa-125">Písma můžete přidat do aplikace jako položky prostředků projektu, které jsou vloženy do souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="952aa-126">Použití samostatného podadresáře pro zdroje pomáhá uspořádat soubory projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="952aa-127">Následující příklad souboru projektu ukazuje, jak definovat písma jako položky prostředků v samostatném podadresáři.</span><span class="sxs-lookup"><span data-stu-id="952aa-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
> <span data-ttu-id="952aa-128">Při přidávání písem jako prostředky do aplikace, ujistěte se, že nastavujete `<Resource>` prvek a nikoli `<EmbeddedResource>` prvek v souboru projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="952aa-129">`<EmbeddedResource>` Prvek pro akci sestavení není podporován.</span><span class="sxs-lookup"><span data-stu-id="952aa-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="952aa-130">Následující příklad značek ukazuje, jak odkazovat na prostředky písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="952aa-131">Odkazování na položky prostředků písma z kódu</span><span class="sxs-lookup"><span data-stu-id="952aa-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="952aa-132">Chcete-li odkazovat na položky prostředků písma z kódu, musíte zadat dvoudílný odkaz na prostředek písma: základní identifikátor jednotného prostředku (URI); a odkaz na umístění písma.</span><span class="sxs-lookup"><span data-stu-id="952aa-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="952aa-133">Tyto hodnoty se používají jako <xref:System.Windows.Media.FontFamily.%23ctor%2A> parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="952aa-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="952aa-134">Následující příklad kódu ukazuje, jak odkazovat na prostředky písem `resources`aplikace v podadresáři projektu s názvem .</span><span class="sxs-lookup"><span data-stu-id="952aa-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="952aa-135">Identifikátor uri základního jednotného prostředku může zahrnovat podadresář aplikace, ve kterém je umístěn prostředek písma.</span><span class="sxs-lookup"><span data-stu-id="952aa-135">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="952aa-136">V takovém případě by odkaz na umístění písma nemusel zadávat adresář,`./`ale musel by obsahovat úvodní " ", což znamená, že prostředek písma je ve stejném adresáři určeném identifikátorem identifikátoru URI (base uniform resource).</span><span class="sxs-lookup"><span data-stu-id="952aa-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="952aa-137">Následující příklad kódu ukazuje alternativní způsob odkazování na položku prostředku písma – je ekvivalentní předchozímu příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="952aa-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="952aa-138">Odkazování na písma ze stejného podadresáře aplikace</span><span class="sxs-lookup"><span data-stu-id="952aa-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="952aa-139">Obsah aplikace i soubory prostředků můžete umístit do stejného uživatelem definovaného podadresáře aplikačního projektu.</span><span class="sxs-lookup"><span data-stu-id="952aa-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="952aa-140">Následující příklad souboru projektu zobrazuje stránku obsahu a prostředky písma definované ve stejném podadresáři.</span><span class="sxs-lookup"><span data-stu-id="952aa-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="952aa-141">Vzhledem k tomu, že obsah aplikace a písmo jsou ve stejném podadresáři, odkaz na písmo je relativní k obsahu aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="952aa-142">Následující příklady ukazují, jak odkazovat na prostředek písma aplikace, pokud je písmo ve stejném adresáři jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="952aa-143">Výčet písem v aplikaci</span><span class="sxs-lookup"><span data-stu-id="952aa-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="952aa-144">Chcete-li vytvořit výčet písem jako položek prostředků <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> v <xref:System.Windows.Media.Fonts.GetTypefaces%2A> aplikaci, použijte metodu or.</span><span class="sxs-lookup"><span data-stu-id="952aa-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="952aa-145">Následující příklad ukazuje, jak <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> použít metodu <xref:System.Windows.Media.FontFamily> k vrácení kolekce objektů z umístění písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="952aa-146">V tomto případě aplikace obsahuje podadresář s názvem "prostředky".</span><span class="sxs-lookup"><span data-stu-id="952aa-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="952aa-147">Následující příklad ukazuje, jak <xref:System.Windows.Media.Fonts.GetTypefaces%2A> použít metodu <xref:System.Windows.Media.Typeface> k vrácení kolekce objektů z umístění písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="952aa-148">V tomto případě aplikace obsahuje podadresář s názvem "prostředky".</span><span class="sxs-lookup"><span data-stu-id="952aa-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="952aa-149">Vytvoření knihovny prostředků písem</span><span class="sxs-lookup"><span data-stu-id="952aa-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="952aa-150">Můžete vytvořit knihovnu pouze pro zdroje, která obsahuje pouze písma – žádný kód není součástí tohoto typu projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="952aa-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="952aa-151">Vytvoření knihovny pouze pro prostředky je běžná technika pro oddělení prostředků od kódu aplikace, který je používá.</span><span class="sxs-lookup"><span data-stu-id="952aa-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="952aa-152">To také umožňuje sestavení knihovny, které mají být zahrnuty do více projektů aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="952aa-153">Následující příklad souboru projektu ukazuje klíčové části projektu knihovny pouze pro zdroje.</span><span class="sxs-lookup"><span data-stu-id="952aa-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="952aa-154">Odkazování na písmo v knihovně zdrojů</span><span class="sxs-lookup"><span data-stu-id="952aa-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="952aa-155">Chcete-li odkazovat na písmo v knihovně prostředků z aplikace, musíte odkaz na písmo předponu s názvem sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="952aa-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="952aa-156">V tomto případě je sestavení prostředku písma "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="952aa-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="952aa-157">Chcete-li oddělit název sestavení od odkazu v rámci sestavení, použijte znak ';'.</span><span class="sxs-lookup"><span data-stu-id="952aa-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="952aa-158">Přidáním klíčového slova Komponenta následovaném odkazem na název písma se doplní úplný odkaz na prostředek knihovny písem.</span><span class="sxs-lookup"><span data-stu-id="952aa-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="952aa-159">Následující příklad kódu ukazuje, jak odkazovat na písmo v sestavení knihovny prostředků.</span><span class="sxs-lookup"><span data-stu-id="952aa-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="952aa-160">Tato sada SDK obsahuje sadu ukázkových písem OpenType, které lze použít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="952aa-160">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="952aa-161">Písma jsou definována v knihovně pouze pro prostředky.</span><span class="sxs-lookup"><span data-stu-id="952aa-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="952aa-162">Další informace naleznete [v tématu Ukázka sady OpenType Font Pack](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="952aa-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="952aa-163">Omezení používání písma</span><span class="sxs-lookup"><span data-stu-id="952aa-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="952aa-164">Následující seznam popisuje několik omezení balení a používání písem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v aplikacích:</span><span class="sxs-lookup"><span data-stu-id="952aa-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="952aa-165">**Bity oprávnění pro vkládání písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nekontrolují ani nevynucují žádné bity oprávnění pro vkládání písem.</span><span class="sxs-lookup"><span data-stu-id="952aa-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="952aa-166">Další informace naleznete v části [písma Introduction_to_Packing.](#introduction_to_packaging_fonts)</span><span class="sxs-lookup"><span data-stu-id="952aa-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="952aa-167">**Místo původu písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují odkaz písma na http nebo ftp identifikátor prostředku (URI).</span><span class="sxs-lookup"><span data-stu-id="952aa-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="952aa-168">**Absolutní identifikátor URI pomocí balíčku: zápis:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují programově vytvořit <xref:System.Windows.Media.FontFamily> objekt pomocí "pack:" jako součást absolutního jednotného identifikátoru prostředku (URI) odkaz na písmo.</span><span class="sxs-lookup"><span data-stu-id="952aa-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="952aa-169">Například `"pack://application:,,,/resources/#Pericles Light"` je neplatný odkaz na písmo.</span><span class="sxs-lookup"><span data-stu-id="952aa-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="952aa-170">**Automatické vkládání písem:** Během návrhu neexistuje žádná podpora pro vyhledávání aplikace použití písem a automatické vkládání písem do prostředků aplikace.</span><span class="sxs-lookup"><span data-stu-id="952aa-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="952aa-171">**Podmnožiny písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepodporují vytváření podmnožin písem pro nepevné dokumenty.</span><span class="sxs-lookup"><span data-stu-id="952aa-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="952aa-172">V případech, kdy je nesprávný odkaz, aplikace přejde zpět k použití dostupné písmo.</span><span class="sxs-lookup"><span data-stu-id="952aa-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952aa-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="952aa-173">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="952aa-174">Microsoft Typography: Odkazy, novinky a kontakty</span><span class="sxs-lookup"><span data-stu-id="952aa-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="952aa-175">Specifikace OpenType</span><span class="sxs-lookup"><span data-stu-id="952aa-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="952aa-176">Funkce písma OpenType</span><span class="sxs-lookup"><span data-stu-id="952aa-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="952aa-177">Ukázková sada písem OpenType</span><span class="sxs-lookup"><span data-stu-id="952aa-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
