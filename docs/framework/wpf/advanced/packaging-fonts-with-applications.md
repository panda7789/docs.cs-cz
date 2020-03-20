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
# <a name="packaging-fonts-with-applications"></a>Balení písem s aplikacemi
Toto téma obsahuje přehled o tom, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jak zabalit písma s vaší aplikací.  
  
> [!NOTE]
> Stejně jako u většiny typů softwaru jsou soubory písem licencovány, nikoli prodávány. Licence, které řídí používání písem, se u jednotlivých dodavatelů liší, ale obecně většina licencí, včetně licencí, které se týkají písem, které společnost Microsoft dodává s aplikacemi a systémem Windows, neumožňují, aby byla písma vložena do aplikací nebo jinak distribuována. Proto jako vývojář je vaší odpovědností zajistit, že máte požadovaná licenční práva pro jakékoli písmo, které vložíte do aplikace nebo jinak redistribuujete.  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>Úvod do obalových písem  
 Písma můžete snadno zabalit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako prostředky v rámci aplikací a zobrazit text uživatelského rozhraní a další typy textového obsahu. Písma mohou být oddělena nebo vložena do souborů sestavení aplikace. Můžete také vytvořit knihovnu písem pouze pro prostředky, na kterou může aplikace odkazovat.  
  
 Písma OpenType a TrueType® obsahují příznak typu fsType, který označuje licenční práva pro vkládání písem pro písmo. Tento příznak typu se však vztahuje pouze na vložená písma uložená v dokumentu – neodkazuje na písma vložená do aplikace. Práva pro vkládání písma pro písmo <xref:System.Windows.Media.GlyphTypeface> můžete načíst <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> vytvořením objektu a odkazováním na jeho vlastnost. Další informace o příznaku fsType naleznete v části Metriky operačního systému 2 a Windows [ve specifikaci OpenType.](https://www.microsoft.com/typography/otspec/os2.htm)  
  
 Web [Typografie společnosti Microsoft](https://docs.microsoft.com/typography/) obsahuje kontaktní informace, které vám mohou pomoci najít konkrétního dodavatele písma nebo najít dodavatele písma pro vlastní práci.  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>Přidání písem jako položek obsahu  
 Písma můžete přidat do aplikace jako položky obsahu projektu, které jsou oddělené od souborů sestavení aplikace. To znamená, že položky obsahu nejsou vloženy jako prostředky v rámci sestavení. Následující příklad souboru projektu ukazuje, jak definovat položky obsahu.  
  
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
  
 Aby bylo zajištěno, že aplikace můžete používat písma za běhu, písma musí být přístupné v adresáři nasazení aplikace. Prvek `<CopyToOutputDirectory>` v souboru projektu aplikace umožňuje automaticky zkopírovat písma do adresáře nasazení aplikace během procesu sestavení. Následující příklad souboru projektu ukazuje, jak zkopírovat písma do adresáře nasazení.  
  
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
## <a name="adding-fonts-as-resource-items"></a>Přidání písem jako položek zdrojů  
 Písma můžete přidat do aplikace jako položky prostředků projektu, které jsou vloženy do souborů sestavení aplikace. Použití samostatného podadresáře pro zdroje pomáhá uspořádat soubory projektu aplikace. Následující příklad souboru projektu ukazuje, jak definovat písma jako položky prostředků v samostatném podadresáři.  
  
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
> Při přidávání písem jako prostředky do aplikace, ujistěte se, že nastavujete `<Resource>` prvek a nikoli `<EmbeddedResource>` prvek v souboru projektu aplikace. `<EmbeddedResource>` Prvek pro akci sestavení není podporován.  
  
 Následující příklad značek ukazuje, jak odkazovat na prostředky písma aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odkazování na položky prostředků písma z kódu  
 Chcete-li odkazovat na položky prostředků písma z kódu, musíte zadat dvoudílný odkaz na prostředek písma: základní identifikátor jednotného prostředku (URI); a odkaz na umístění písma. Tyto hodnoty se používají jako <xref:System.Windows.Media.FontFamily.%23ctor%2A> parametry pro metodu. Následující příklad kódu ukazuje, jak odkazovat na prostředky písem `resources`aplikace v podadresáři projektu s názvem .  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Identifikátor uri základního jednotného prostředku může zahrnovat podadresář aplikace, ve kterém je umístěn prostředek písma. V takovém případě by odkaz na umístění písma nemusel zadávat adresář,`./`ale musel by obsahovat úvodní " ", což znamená, že prostředek písma je ve stejném adresáři určeném identifikátorem identifikátoru URI (base uniform resource). Následující příklad kódu ukazuje alternativní způsob odkazování na položku prostředku písma – je ekvivalentní předchozímu příkladu kódu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odkazování na písma ze stejného podadresáře aplikace  
 Obsah aplikace i soubory prostředků můžete umístit do stejného uživatelem definovaného podadresáře aplikačního projektu. Následující příklad souboru projektu zobrazuje stránku obsahu a prostředky písma definované ve stejném podadresáři.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Vzhledem k tomu, že obsah aplikace a písmo jsou ve stejném podadresáři, odkaz na písmo je relativní k obsahu aplikace. Následující příklady ukazují, jak odkazovat na prostředek písma aplikace, pokud je písmo ve stejném adresáři jako aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Výčet písem v aplikaci  
 Chcete-li vytvořit výčet písem jako položek prostředků <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> v <xref:System.Windows.Media.Fonts.GetTypefaces%2A> aplikaci, použijte metodu or. Následující příklad ukazuje, jak <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> použít metodu <xref:System.Windows.Media.FontFamily> k vrácení kolekce objektů z umístění písma aplikace. V tomto případě aplikace obsahuje podadresář s názvem "prostředky".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Fonts.GetTypefaces%2A> použít metodu <xref:System.Windows.Media.Typeface> k vrácení kolekce objektů z umístění písma aplikace. V tomto případě aplikace obsahuje podadresář s názvem "prostředky".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>Vytvoření knihovny prostředků písem  
 Můžete vytvořit knihovnu pouze pro zdroje, která obsahuje pouze písma – žádný kód není součástí tohoto typu projektu knihovny. Vytvoření knihovny pouze pro prostředky je běžná technika pro oddělení prostředků od kódu aplikace, který je používá. To také umožňuje sestavení knihovny, které mají být zahrnuty do více projektů aplikace. Následující příklad souboru projektu ukazuje klíčové části projektu knihovny pouze pro zdroje.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Odkazování na písmo v knihovně zdrojů  
 Chcete-li odkazovat na písmo v knihovně prostředků z aplikace, musíte odkaz na písmo předponu s názvem sestavení knihovny. V tomto případě je sestavení prostředku písma "FontLibrary". Chcete-li oddělit název sestavení od odkazu v rámci sestavení, použijte znak ';'. Přidáním klíčového slova Komponenta následovaném odkazem na název písma se doplní úplný odkaz na prostředek knihovny písem. Následující příklad kódu ukazuje, jak odkazovat na písmo v sestavení knihovny prostředků.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Tato sada SDK obsahuje sadu ukázkových písem OpenType, které lze použít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacemi. Písma jsou definována v knihovně pouze pro prostředky. Další informace naleznete [v tématu Ukázka sady OpenType Font Pack](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>Omezení používání písma  
 Následující seznam popisuje několik omezení balení a používání písem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v aplikacích:  
  
- **Bity oprávnění pro vkládání písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nekontrolují ani nevynucují žádné bity oprávnění pro vkládání písem. Další informace naleznete v části [písma Introduction_to_Packing.](#introduction_to_packaging_fonts)  
  
- **Místo původu písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují odkaz písma na http nebo ftp identifikátor prostředku (URI).  
  
- **Absolutní identifikátor URI pomocí balíčku: zápis:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují programově vytvořit <xref:System.Windows.Media.FontFamily> objekt pomocí "pack:" jako součást absolutního jednotného identifikátoru prostředku (URI) odkaz na písmo. Například `"pack://application:,,,/resources/#Pericles Light"` je neplatný odkaz na písmo.  
  
- **Automatické vkládání písem:** Během návrhu neexistuje žádná podpora pro vyhledávání aplikace použití písem a automatické vkládání písem do prostředků aplikace.  
  
- **Podmnožiny písem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepodporují vytváření podmnožin písem pro nepevné dokumenty.  
  
- V případech, kdy je nesprávný odkaz, aplikace přejde zpět k použití dostupné písmo.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft Typography: Odkazy, novinky a kontakty](https://docs.microsoft.com/typography/)
- [Specifikace OpenType](https://www.microsoft.com/typography/otspec/)
- [Funkce písma OpenType](opentype-font-features.md)
- [Ukázková sada písem OpenType](sample-opentype-font-pack.md)
