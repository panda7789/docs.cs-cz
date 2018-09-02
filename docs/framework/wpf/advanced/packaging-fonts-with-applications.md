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
ms.openlocfilehash: 0ad8d071a91edaef184c4cc1fa28298f8ec3d71a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391763"
---
# <a name="packaging-fonts-with-applications"></a>Balení písem s aplikacemi
Toto téma poskytuje přehled o tom balení písem za použití vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.  
  
> [!NOTE]
>  Stejně jako u většiny typů softwaru, soubory písma jsou licencované, spíše než prodává. Licence, které se vztahují na používání služeb písma se liší od dodavatele dodavatele, ale obecně většina licence, včetně těch, které pokrývají písma [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] dodává s aplikacemi a [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], nejsou povoleny jako vložený v rámci aplikace nebo jinak písma znovu distribuovat. Proto se jako vývojář, který je na vás, abyste měli jistotu, že máte potřebná licenční oprávnění pro všechny písmo, které můžete vložit do aplikace nebo jinak redistribute.  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Úvod k balení písem  
 Můžete jednoduše zabalit písma jako prostředky v rámci vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, chcete-li zobrazit text uživatelského rozhraní a dalších typů text na základě obsahu. Písma může být oddělené od nebo vložené v souborech sestavení aplikace. Můžete také vytvořit písmo pouze prostředky knihovny, která vaše aplikace může odkazovat.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] a [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] písma obsahovat příznak typ fsType, určující písma vkládání licenční práva pro písmo. Tento typ, který příznak se vztahuje pouze na vložených písem, uložených v dokumentu – it, ale neodkazuje na písma, které jsou součástí aplikace. Můžete načíst vkládání práva pro písma tak, že vytvoříte písem <xref:System.Windows.Media.GlyphTypeface> objektu a odkazování na ně jeho <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> vlastnost. Přečtěte si část "operačního systému a 2 a Windows metrik" [OpenType specifikace](https://www.microsoft.com/typography/otspec/os2.htm) Další informace o fsType příznak.  
  
 [Microsoft Typography](https://www.microsoft.com/typography/links/) webu obsahuje kontaktní informace, které pomáhají najít konkrétní písmo dodavatele nebo najít dodavatele písma pro vlastní práci.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>Přidávání písem jako položky obsahu  
 Přidat písma pro vaši aplikaci ve formě obsahu položky projektu, které jsou oddělené od soubory sestavení aplikace. To znamená, že nejsou obsahu položky vloženy jako prostředky v rámci sestavení. Následující příklad souboru projektu ukazuje, jak definovat položky obsahu.  
  
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
  
 Aby se zajistilo, že aplikace může používat písma v době běhu, písma musí být přístupné v adresáři nasazení vaší aplikace. `<CopyToOutputDirectory>` Prvku v souboru projektu aplikace umožňuje automaticky kopírovat písem do adresáře nasazení aplikace během procesu sestavení. Následující příklad souboru projektu ukazuje, jak kopírovat písma do adresáře nasazení.  
  
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
  
 Následující příklad kódu ukazuje, jak odkazovat na aplikace písmo jako položka obsahu – odkazovaná položka obsahu musí být ve stejném adresáři jako soubory sestavení aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Přidávání písem jako položky prostředků  
 Přidat písma do aplikace jako zdroj položek projektu, které jsou vloženy do souborů sestavení aplikace. Pomocí samostatných podadresář zdrojů pomáhá uspořádat soubory projektu aplikace. Následující příklad souboru projektu ukazuje, jak definovat písma jako položky prostředků v samostatném podadresáři.  
  
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
>  Když přidáte písma jako prostředky pro vaši aplikaci, ujistěte se, že nastavujete `<Resource>` elementu a ne `<EmbeddedResource>` element v souboru projektu vaší aplikace. `<EmbeddedResource>` Není podporován – element pro akci sestavení.  
  
 Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odkazování na písma položky prostředků z kódu  
 Aby bylo možné odkazovat písma položky prostředků z kódu, je nutné zadat odkaz na prostředek písma dvou částí: základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; a odkaz na umístění písma. Tyto hodnoty se použijí jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metody. Následující příklad kódu ukazuje, jak odkazovat na písmo prostředků v projektu podadresář s názvem `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mohou zahrnovat podadresář aplikace, ve které se nachází zdroj písma. V takovém případě není potřeba zadávat adresář odkaz na umístění písma, ale by měl zahrnovat jeden z předních "`./`", označující písma prostředků je ve stejném adresáři určeném základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Následující příklad kódu ukazuje alternativní způsob odkazuje na položku prostředků písma – je ekvivalentní předchozí příklad kódu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odkazování na písma z podadresáře stejné aplikace  
 Můžete umístit obě aplikace obsahu a zdrojové soubory v rámci stejné uživatelské podadresáře projektu aplikace. Následující příklad souboru projektu zobrazí stránku obsahu a zdroje písma, které jsou definovány ve stejném podadresáři.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Protože obsah aplikace a písma jsou ve stejném podadresáři, písmo odkaz je relativní vzhledem k obsahu aplikace. Následující příklady ukazují způsob vytvoření odkazu prostředku písem aplikace, když je písmo ve stejném adresáři jako aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Vytváření výčtu písem v aplikaci  
 Výčet písma jako položky prostředků ve vaší aplikaci, použijte buď <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> nebo <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metody. Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metoda vrátí kolekci <xref:System.Windows.Media.FontFamily> objekty z písma umístění aplikace. V tomto případě aplikace obsahuje podadresář s názvem "resources".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metoda vrátí kolekci <xref:System.Windows.Media.Typeface> objekty z písma umístění aplikace. V tomto případě aplikace obsahuje podadresář s názvem "resources".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Vytvoření prostředků knihovny písma  
 Můžete vytvořit pouze prostředky knihovny, který obsahuje pouze písma – není součástí tohoto typu projektu knihovny žádný kód. Vytvoření knihovny jen pro prostředek je běžná technika pro oddělení prostředků od kódu aplikace, která je používá. Také to umožňuje sestavení knihovny, které mají být zahrnuty s více projekty aplikací. Následující příklad souboru projektu ukazuje nejdůležitějších částí projektu pouze prostředky knihovny.  
  
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
 K odkazování písma v knihovně prostředků z vaší aplikace, musíte přidat předponu písma odkaz s názvem sestavení knihovny. V takovém případě je sestavení prostředků písmo "FontLibrary". K oddělení názvu sestavení z odkazu v rámci sestavení, použijte znak ";". Přidání klíčového slova "Součást", za nímž následuje odkaz na název písma dokončí úplný odkaz na prostředek knihovny písma. Následující příklad kódu ukazuje, jak odkazovat na písmo v sestavení knihovny prostředků.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  Tato sada SDK obsahuje sadu ukázkových [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem, které můžete použít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací. Písma jsou definovány v knihovně pouze prostředky. Další informace najdete v tématu [Ukázková sada písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Omezení týkající se použití písem  
 Následující seznam popisuje několik omezení na balení a použití písem v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:  
  
-   **Písmo vkládání bity oprávnění:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace zkontrolovat nebo jakékoli písmo vkládání bity oprávnění vynutit. Zobrazit [Introduction_to_Packing písma](#introduction_to_packaging_fonts) části Další informace.  
  
-   **Lokality původu písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují písma odkaz na http nebo ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  
  
-   **Absolutní identifikátor URI pomocí balíčku: zápis:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace vytvářet neumožňují <xref:System.Windows.Media.FontFamily> prostřednictvím kódu programu pomocí "aktualizací Service pack:" jako součást absolutní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz na písmo. Například `"pack://application:,,,/resources/#Pericles Light"` je odkaz na neplatné písmo.  
  
-   **Vložení písma Automatické:** v době návrhu, neexistuje žádná podpora pro vyhledávání aplikace použití písem a automaticky vložení písma do aplikace prostředků.  
  
-   **Podsady písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepodporují vytváření podsady písma pro nepevnou dokumenty.  
  
-   V případech, kde je nesprávný odkaz, aplikace přejde k použití dostupné písmo.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [Typografie společnosti Microsoft: Odkazy, zpráv a kontakty](https://www.microsoft.com/typography/links/)  
 [Specifikace OpenType](https://www.microsoft.com/typography/otspec/)  
 [Funkce písma OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Ukázková sada písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
