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
ms.openlocfilehash: d5101d19cd250d96ba183fa14bd9db6692f05484
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611862"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="6dff2-102">Balení písem s aplikacemi</span><span class="sxs-lookup"><span data-stu-id="6dff2-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="6dff2-103">Toto téma poskytuje přehled o tom balení písem za použití vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6dff2-104">Stejně jako u většiny typů softwaru, soubory písma jsou licencované, spíše než prodává.</span><span class="sxs-lookup"><span data-stu-id="6dff2-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="6dff2-105">Licence, které se vztahují na používání služeb písma se liší od dodavatele dodavatele, ale obecně většina licence, včetně těch, které pokrývají písma [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] dodává s aplikacemi a [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], nejsou povoleny jako vložený v rámci aplikace nebo jinak písma znovu distribuovat.</span><span class="sxs-lookup"><span data-stu-id="6dff2-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="6dff2-106">Proto se jako vývojář, který je na vás, abyste měli jistotu, že máte potřebná licenční oprávnění pro všechny písmo, které můžete vložit do aplikace nebo jinak redistribute.</span><span class="sxs-lookup"><span data-stu-id="6dff2-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="6dff2-107">Úvod k balení písem</span><span class="sxs-lookup"><span data-stu-id="6dff2-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="6dff2-108">Můžete jednoduše zabalit písma jako prostředky v rámci vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, chcete-li zobrazit text uživatelského rozhraní a dalších typů text na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="6dff2-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="6dff2-109">Písma může být oddělené od nebo vložené v souborech sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="6dff2-110">Můžete také vytvořit písmo pouze prostředky knihovny, která vaše aplikace může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="6dff2-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="6dff2-111">a [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] písma obsahovat příznak typ fsType, určující písma vkládání licenční práva pro písmo.</span><span class="sxs-lookup"><span data-stu-id="6dff2-111">and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="6dff2-112">Tento typ, který příznak se vztahuje pouze na vložených písem, uložených v dokumentu – it, ale neodkazuje na písma, které jsou součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="6dff2-113">Můžete načíst vkládání práva pro písma tak, že vytvoříte písem <xref:System.Windows.Media.GlyphTypeface> objektu a odkazování na ně jeho <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6dff2-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="6dff2-114">Přečtěte si část "operačního systému a 2 a Windows metrik" [OpenType specifikace](https://www.microsoft.com/typography/otspec/os2.htm) Další informace o fsType příznak.</span><span class="sxs-lookup"><span data-stu-id="6dff2-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="6dff2-115">[Microsoft Typography](https://docs.microsoft.com/typography/) webu obsahuje kontaktní informace, které pomáhají najít konkrétní písmo dodavatele nebo najít dodavatele písma pro vlastní práci.</span><span class="sxs-lookup"><span data-stu-id="6dff2-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="6dff2-116">Přidávání písem jako položky obsahu</span><span class="sxs-lookup"><span data-stu-id="6dff2-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="6dff2-117">Přidat písma pro vaši aplikaci ve formě obsahu položky projektu, které jsou oddělené od soubory sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="6dff2-118">To znamená, že nejsou obsahu položky vloženy jako prostředky v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="6dff2-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="6dff2-119">Následující příklad souboru projektu ukazuje, jak definovat položky obsahu.</span><span class="sxs-lookup"><span data-stu-id="6dff2-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="6dff2-120">Aby se zajistilo, že aplikace může používat písma v době běhu, písma musí být přístupné v adresáři nasazení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="6dff2-121">`<CopyToOutputDirectory>` Prvku v souboru projektu aplikace umožňuje automaticky kopírovat písem do adresáře nasazení aplikace během procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6dff2-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="6dff2-122">Následující příklad souboru projektu ukazuje, jak kopírovat písma do adresáře nasazení.</span><span class="sxs-lookup"><span data-stu-id="6dff2-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="6dff2-123">Následující příklad kódu ukazuje, jak odkazovat na aplikace písmo jako položka obsahu – odkazovaná položka obsahu musí být ve stejném adresáři jako soubory sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="6dff2-124">Přidávání písem jako položky prostředků</span><span class="sxs-lookup"><span data-stu-id="6dff2-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="6dff2-125">Přidat písma do aplikace jako zdroj položek projektu, které jsou vloženy do souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="6dff2-126">Pomocí samostatných podadresář zdrojů pomáhá uspořádat soubory projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="6dff2-127">Následující příklad souboru projektu ukazuje, jak definovat písma jako položky prostředků v samostatném podadresáři.</span><span class="sxs-lookup"><span data-stu-id="6dff2-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
>  <span data-ttu-id="6dff2-128">Když přidáte písma jako prostředky pro vaši aplikaci, ujistěte se, že nastavujete `<Resource>` elementu a ne `<EmbeddedResource>` element v souboru projektu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="6dff2-129">`<EmbeddedResource>` Není podporován – element pro akci sestavení.</span><span class="sxs-lookup"><span data-stu-id="6dff2-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="6dff2-130">Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="6dff2-131">Odkazování na písma položky prostředků z kódu</span><span class="sxs-lookup"><span data-stu-id="6dff2-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="6dff2-132">Aby bylo možné odkazovat písma položky prostředků z kódu, je nutné zadat odkaz na prostředek písma dvou částí: základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; a odkaz na umístění písma.</span><span class="sxs-lookup"><span data-stu-id="6dff2-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="6dff2-133">Tyto hodnoty se použijí jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6dff2-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="6dff2-134">Následující příklad kódu ukazuje, jak odkazovat na písmo prostředků v projektu podadresář s názvem `resources`.</span><span class="sxs-lookup"><span data-stu-id="6dff2-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="6dff2-135">Základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mohou zahrnovat podadresář aplikace, ve které se nachází zdroj písma.</span><span class="sxs-lookup"><span data-stu-id="6dff2-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="6dff2-136">V takovém případě není potřeba zadávat adresář odkaz na umístění písma, ale by měl zahrnovat jeden z předních "`./`", označující písma prostředků je ve stejném adresáři určeném základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6dff2-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="6dff2-137">Následující příklad kódu ukazuje alternativní způsob odkazuje na položku prostředků písma – je ekvivalentní předchozí příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="6dff2-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="6dff2-138">Odkazování na písma z podadresáře stejné aplikace</span><span class="sxs-lookup"><span data-stu-id="6dff2-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="6dff2-139">Můžete umístit obě aplikace obsahu a zdrojové soubory v rámci stejné uživatelské podadresáře projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="6dff2-140">Následující příklad souboru projektu zobrazí stránku obsahu a zdroje písma, které jsou definovány ve stejném podadresáři.</span><span class="sxs-lookup"><span data-stu-id="6dff2-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="6dff2-141">Protože obsah aplikace a písma jsou ve stejném podadresáři, písmo odkaz je relativní vzhledem k obsahu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="6dff2-142">Následující příklady ukazují způsob vytvoření odkazu prostředku písem aplikace, když je písmo ve stejném adresáři jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="6dff2-143">Vytváření výčtu písem v aplikaci</span><span class="sxs-lookup"><span data-stu-id="6dff2-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="6dff2-144">Výčet písma jako položky prostředků ve vaší aplikaci, použijte buď <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> nebo <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6dff2-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="6dff2-145">Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metoda vrátí kolekci <xref:System.Windows.Media.FontFamily> objekty z písma umístění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="6dff2-146">V tomto případě aplikace obsahuje podadresář s názvem "resources".</span><span class="sxs-lookup"><span data-stu-id="6dff2-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="6dff2-147">Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metoda vrátí kolekci <xref:System.Windows.Media.Typeface> objekty z písma umístění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="6dff2-148">V tomto případě aplikace obsahuje podadresář s názvem "resources".</span><span class="sxs-lookup"><span data-stu-id="6dff2-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="6dff2-149">Vytvoření prostředků knihovny písma</span><span class="sxs-lookup"><span data-stu-id="6dff2-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="6dff2-150">Můžete vytvořit pouze prostředky knihovny, který obsahuje pouze písma – není součástí tohoto typu projektu knihovny žádný kód.</span><span class="sxs-lookup"><span data-stu-id="6dff2-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="6dff2-151">Vytvoření knihovny jen pro prostředek je běžná technika pro oddělení prostředků od kódu aplikace, která je používá.</span><span class="sxs-lookup"><span data-stu-id="6dff2-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="6dff2-152">Také to umožňuje sestavení knihovny, které mají být zahrnuty s více projekty aplikací.</span><span class="sxs-lookup"><span data-stu-id="6dff2-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="6dff2-153">Následující příklad souboru projektu ukazuje nejdůležitějších částí projektu pouze prostředky knihovny.</span><span class="sxs-lookup"><span data-stu-id="6dff2-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="6dff2-154">Odkazování na písmo v knihovně prostředků</span><span class="sxs-lookup"><span data-stu-id="6dff2-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="6dff2-155">K odkazování písma v knihovně prostředků z vaší aplikace, musíte přidat předponu písma odkaz s názvem sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="6dff2-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="6dff2-156">V takovém případě je sestavení prostředků písmo "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="6dff2-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="6dff2-157">K oddělení názvu sestavení z odkazu v rámci sestavení, použijte znak ";".</span><span class="sxs-lookup"><span data-stu-id="6dff2-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="6dff2-158">Přidání klíčového slova "Součást", za nímž následuje odkaz na název písma dokončí úplný odkaz na prostředek knihovny písma.</span><span class="sxs-lookup"><span data-stu-id="6dff2-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="6dff2-159">Následující příklad kódu ukazuje, jak odkazovat na písmo v sestavení knihovny prostředků.</span><span class="sxs-lookup"><span data-stu-id="6dff2-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="6dff2-160">Tato sada SDK obsahuje sadu ukázkových [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem, které můžete použít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="6dff2-160">This SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="6dff2-161">Písma jsou definovány v knihovně pouze prostředky.</span><span class="sxs-lookup"><span data-stu-id="6dff2-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="6dff2-162">Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6dff2-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="6dff2-163">Omezení týkající se použití písem</span><span class="sxs-lookup"><span data-stu-id="6dff2-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="6dff2-164">Následující seznam popisuje několik omezení na balení a použití písem v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="6dff2-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="6dff2-165">**Písmo vkládání bity oprávnění:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace zkontrolovat nebo jakékoli písmo vkládání bity oprávnění vynutit.</span><span class="sxs-lookup"><span data-stu-id="6dff2-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="6dff2-166">Zobrazit [Introduction_to_Packing písma](#introduction_to_packaging_fonts) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="6dff2-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="6dff2-167">**Lokality původu písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují písma odkaz na http nebo ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6dff2-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
- <span data-ttu-id="6dff2-168">**Absolutní identifikátor URI pomocí balíčku: zápis:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace vytvářet neumožňují <xref:System.Windows.Media.FontFamily> prostřednictvím kódu programu pomocí "aktualizací Service pack:" jako součást absolutní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz na písmo.</span><span class="sxs-lookup"><span data-stu-id="6dff2-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="6dff2-169">Například `"pack://application:,,,/resources/#Pericles Light"` je odkaz na neplatné písmo.</span><span class="sxs-lookup"><span data-stu-id="6dff2-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="6dff2-170">**Vkládání automatické písma:** V době návrhu není dostupná podpora pro vyhledávání aplikace použití písem a automaticky vložení písma do aplikace prostředků.</span><span class="sxs-lookup"><span data-stu-id="6dff2-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="6dff2-171">**Podsady písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepodporují vytváření podsady písma pro nepevnou dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6dff2-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="6dff2-172">V případech, kde je nesprávný odkaz, aplikace přejde k použití dostupné písmo.</span><span class="sxs-lookup"><span data-stu-id="6dff2-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dff2-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6dff2-173">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="6dff2-174">Typografie společnosti Microsoft: Odkazy, zprávy a kontaktů</span><span class="sxs-lookup"><span data-stu-id="6dff2-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="6dff2-175">Specifikace OpenType</span><span class="sxs-lookup"><span data-stu-id="6dff2-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="6dff2-176">Funkce písma OpenType</span><span class="sxs-lookup"><span data-stu-id="6dff2-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="6dff2-177">Ukázková sada písem OpenType</span><span class="sxs-lookup"><span data-stu-id="6dff2-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
