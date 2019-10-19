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
ms.openlocfilehash: c90d554338da21a55f058fdf1ce27b8ee28e682b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580939"
---
# <a name="packaging-fonts-with-applications"></a>Balení písem s aplikacemi
Toto téma poskytuje přehled o tom, jak pomocí aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zabalit písma.  
  
> [!NOTE]
> Stejně jako u většiny typů softwaru jsou soubory písem licencované a nikoli prodávatelné. Licence, které řídí použití písem, se liší od dodavatele k dodavatelům, ale obecně většinou licencí, včetně těch, které se týkají písem, která Microsoft dodává s aplikacemi a Windows, nedovolují vkládání písem do aplikací ani jiné distribuci. Proto je jako vývojář zodpovědný za to, že máte požadovaná licenční práva pro všechna písma vložená v rámci aplikace nebo jinak znovu distribuovat.  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Úvod do balení písem  
 Můžete snadno zabalit písma jako prostředky v aplikacích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro zobrazení textu uživatelského rozhraní a dalších typů textových obsahu. Písma mohou být oddělena nebo vložena do souborů sestavení aplikace. Můžete také vytvořit knihovnu písem pouze pro prostředky, kterou může vaše aplikace odkazovat.  
  
 Písma OpenType a TrueType® obsahují příznak typu fsType, který označuje licenční práva pro vkládání písem. Tento příznak typu se však vztahuje pouze na vložená písma uložená v dokumentu – neodkazuje se na písma vložená v aplikaci. Můžete načíst práva pro vkládání písma pro písmo vytvořením objektu <xref:System.Windows.Media.GlyphTypeface> a odkazem na jeho vlastnost <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>. Další informace o příznaku fsType najdete v části "OS/2 a metriky Windows" v tématu [specifikace OpenType](https://www.microsoft.com/typography/otspec/os2.htm) .  
  
 Web [Typografie společnosti Microsoft](https://docs.microsoft.com/typography/) obsahuje kontaktní informace, které vám pomůžou najít konkrétního dodavatele písma nebo najít dodavatele písma pro vlastní práci.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>Přidání písem jako položek obsahu  
 Do aplikace můžete přidat písma jako položky obsahu projektu, které jsou oddělené od souborů sestavení aplikace. To znamená, že položky obsahu nejsou vloženy jako prostředky v rámci sestavení. Následující příklad souboru projektu ukazuje, jak definovat položky obsahu.  
  
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
  
 Aby bylo zajištěno, že aplikace bude moci používat písma v době běhu, musí být písma přístupná v adresáři nasazení aplikace. Element `<CopyToOutputDirectory>` v souboru projektu aplikace umožňuje automaticky Kopírovat písma do adresáře nasazení aplikace během procesu sestavení. Následující příklad souboru projektu ukazuje, jak zkopírovat písma do adresáře nasazení.  
  
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
  
 Následující příklad kódu ukazuje, jak odkazovat na písmo aplikace jako položku obsahu – odkazovaná položka obsahu musí být ve stejném adresáři jako soubory sestavení aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Přidávání písem jako položek prostředků  
 Do aplikace můžete přidat písma jako položky prostředků projektu, které jsou vloženy do souborů sestavení aplikace. Použití samostatného podadresáře pro prostředky pomáhá organizovat soubory projektu aplikace. Následující příklad souboru projektu ukazuje, jak definovat písma jako položky prostředků v samostatném podadresáři.  
  
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
> Když přidáte písma jako prostředky do aplikace, ujistěte se, že nastavujete prvek `<Resource>` a ne prvek `<EmbeddedResource>` v souboru projektu vaší aplikace. Element `<EmbeddedResource>` pro akci sestavení není podporován.  
  
 Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odkazování na položky prostředků písma z kódu  
 Chcete-li odkazovat na položky prostředků písma z kódu, je nutné dodat odkaz na prostředek o dvou částech: základní identifikátor URI (Uniform Resource Identifier); a odkaz na umístění písma. Tyto hodnoty se používají jako parametry pro metodu <xref:System.Windows.Media.FontFamily.%23ctor%2A>. Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace v podadresáři projektu s názvem `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Základní identifikátor URI (Uniform Resource Identifier) může zahrnovat podadresář aplikace, ve kterém se nachází prostředek písma. V takovém případě odkaz na umístění písma nepotřebuje zadat adresář, ale musí obsahovat úvodní "`./`", což znamená, že se prostředek písma nachází ve stejném adresáři, který je určen základní identifikátor URI (Uniform Resource Identifier). Následující příklad kódu ukazuje alternativní způsob odkazování na položku prostředku písma – je ekvivalentní k předchozímu příkladu kódu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odkazování na písma ze stejného podadresáře aplikace  
 Můžete umístit obsah aplikace i soubory prostředků do stejného uživatelsky definovaného podadresáře projektu aplikace. Následující příklad souboru projektu ukazuje stránku obsahu a prostředky písem definované ve stejném podadresáři.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Vzhledem k tomu, že je obsah aplikace a písmo ve stejném podadresáři, je odkaz na písmo relativní vzhledem k obsahu aplikace. Následující příklady ukazují, jak odkazovat na prostředek písma aplikace, když je písmo ve stejném adresáři jako aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Vyčíslení písem v aplikaci  
 Chcete-li vytvořit výčet písem jako položek prostředků v aplikaci, použijte metodu <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> nebo <xref:System.Windows.Media.Fonts.GetTypefaces%2A>. Následující příklad ukazuje, jak použít metodu <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> k vrácení kolekce objektů <xref:System.Windows.Media.FontFamily> z umístění písma aplikace. V tomto případě aplikace obsahuje podadresář s názvem "Resources".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Následující příklad ukazuje, jak použít metodu <xref:System.Windows.Media.Fonts.GetTypefaces%2A> k vrácení kolekce objektů <xref:System.Windows.Media.Typeface> z umístění písma aplikace. V tomto případě aplikace obsahuje podadresář s názvem "Resources".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Vytvoření knihovny prostředků písma  
 Můžete vytvořit knihovnu pouze pro prostředky, která obsahuje pouze písma – žádný kód není součástí tohoto typu projektu knihovny. Vytváření knihovny pouze pro prostředky je běžnou technikou pro oddělení prostředků z kódu aplikace, který je používá. To umožňuje také zahrnutí sestavení knihovny do více projektů aplikace. Následující příklad souboru projektu ukazuje klíčové části projektu knihovny pouze s prostředky.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Odkazování na písmo v knihovně prostředků  
 Chcete-li odkazovat na písmo v knihovně prostředků z vaší aplikace, je nutné odkaz na písmo prefixovat názvem sestavení knihovny. V tomto případě je sestavení prostředků písma "FontLibrary". Chcete-li název sestavení oddělit od odkazu v rámci sestavení, použijte znak ";". Přidání klíčového slova Component, za nímž následuje odkaz na název písma, dokončí úplný odkaz na prostředek knihovny písem. Následující příklad kódu ukazuje, jak odkazovat na písmo v sestavení knihovny prostředků.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Tato sada SDK obsahuje sadu ukázkových písem OpenType, která můžete použít s aplikacemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Písma jsou definována v knihovně určené pouze pro prostředky. Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Omezení používání písem  
 Následující seznam popisuje několik omezení pro balení a používání písem v aplikacích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- **Bity oprávnění vkládání písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nekontrolují ani vynutily žádné bity oprávnění vkládání písem. Další informace najdete v části [Fonts Introduction_to_Packing](#introduction_to_packaging_fonts) .  
  
- **Lokalita o neoriginálních písmech:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepovolují odkaz na písmo na identifikátor URI http nebo FTP (Uniform Resource Identifier).  
  
- **Absolutní identifikátor URI pomocí balíčku: Notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují vytvořit objekt <xref:System.Windows.Media.FontFamily> programově pomocí příkazu "Pack:" jako součást absolutního odkazu na identifikátor URI (Uniform Resource Identifier) na písmo. Například `"pack://application:,,,/resources/#Pericles Light"` je neplatný odkaz na písmo.  
  
- **Automatické vkládání písem:** Během návrhu není dostupná žádná podpora pro hledání použití písem aplikace a automatické vkládání písem do prostředků aplikace.  
  
- **Podsady písem:** aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nepodporují vytváření podmnožin písem pro nepevné dokumenty.  
  
- V případech, kdy je k dispozici nesprávný odkaz, se aplikace vrátí k použití dostupného písma.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Typografie Microsoft – odkazy, novinky a kontakty](https://docs.microsoft.com/typography/)
- [Specifikace OpenType](https://www.microsoft.com/typography/otspec/)
- [Funkce písma OpenType](opentype-font-features.md)
- [Ukázková sada písem OpenType](sample-opentype-font-pack.md)
