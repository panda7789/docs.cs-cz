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
ms.openlocfilehash: f60668f1bdac6607383b2ddf5c5ab1e41e31862b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-fonts-with-applications"></a>Balení písem s aplikacemi
Toto téma obsahuje základní informace o na balíček písma s vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.  
  
> [!NOTE]
>  Stejně jako u většiny typů softwaru písma souborů jsou licenci, a nikoli prodávána. Licence, které budou řídit použití písem lišit od dodavatele dodavatele, ale obecně většina licence, včetně těch, který po sobě zakrývá písma [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] poskytuje s aplikacemi a [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], zakázat písem vložených v aplikacích nebo jinak hodnota znovu distribuovat. Proto jako vývojář, který je vaší povinností ujistit, že máte požadovanou licenci práva pro libovolného písma, které vložení v rámci aplikace nebo jinak znovu distribuovat.  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Úvod do balení písem  
 Můžete snadno sbalit písem jako prostředky v rámci vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace zobrazíte text v uživatelském rozhraní a dalších typů text na základě obsahu. Písma může být oddělené od nebo vložené v rámci soubory sestavení aplikace. Můžete také vytvořit pouze písma knihovny, která vaše aplikace, můžete odkazovat.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]a [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] písem obsahovat typ příznak fsType, určující písma vložení licenční práva pro písmo. Tento typ, který příznak se vztahuje pouze na vložená písma, které jsou uložené v dokumentu – it však neodkazuje na písem v aplikaci. Můžete načíst vložení práva pro písmo vytvořením písma <xref:System.Windows.Media.GlyphTypeface> objekt a odkazování na jeho <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> vlastnost. Informace naleznete v sekci "OS/2 a Windows metrik" z [OpenType specifikace](http://www.microsoft.com/typography/otspec/os2.htm) Další informace o příznak fsType.  
  
 [Microsoft Typography](http://www.microsoft.com/typography/links/) webový server obsahuje kontaktní informace, které vám může pomoct najít dodavatele zvolené písmo k dispozici nebo najít dodavatele písma pro vlastní pracovní.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>Přidání písem jako položky obsahu  
 Písma můžete přidat do vaší aplikace jako obsahu položky projektu, které jsou oddělené od soubory sestavení aplikace. To znamená, že obsahu položky nejsou vloženy jako prostředky v rámci sestavení. Následující příklad souboru projektu ukazuje, jak k definování položek obsahu.  
  
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
  
 Aby se zajistilo, že aplikace můžete použít písma v době běhu, písma musí být dostupný v adresáři nasazení aplikace. `<CopyToOutputDirectory>` Element v souboru projektu aplikace umožňuje automaticky kopírovat písma k adresáři nasazení aplikace během procesu vytváření. Následující příklad souboru projektu ukazuje, jak zkopírovat do adresáře nasazení písem.  
  
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
  
 Následující příklad kódu ukazuje, jak chcete-li písmo aplikace jako položku obsahu – odkazovaná položka obsahu musí být ve stejném adresáři jako soubory sestavení aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Přidání písem jako položky prostředků  
 Písma můžete přidat do vaší aplikace jako položky projektu prostředků, které jsou vloženy do souborů sestavení aplikace. Používání samostatné podadresáři pro prostředky přispívá k uspořádání souborů projektu aplikace. Následující příklad souboru projektu ukazuje, jak definovat jako položky prostředků v samostatných podadresáři písem.  
  
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
>  Když přidáte písem jako prostředky do vaší aplikace, ujistěte se, jsou nastavení `<Resource>` elementu a ne `<EmbeddedResource>` element v souboru projektu aplikace. `<EmbeddedResource>` Element pro akce sestavení není podporován.  
  
 Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odkazy na písma prostředků položky z kódu  
 Chcete-li odkazovat na položky prostředků písma z kódu, je nutné zadat odkaz na prostředků písma dvě části: základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; a odkaz na umístění písma. Tyto hodnoty jsou použity jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metoda. Následující příklad kódu ukazuje, jak odkazovat na prostředky písma aplikace v podadresáři projektu s názvem `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] může zahrnovat podadresář aplikace, kde se nachází prostředků písma. V takovém případě není potřeba zadávat adresář umístění odkaz na písma, ale by měl zahrnovat jako úvodní "`./`", což naznačuje písma prostředek je ve stejném adresáři určeného základní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Následující příklad kódu ukazuje alternativní způsob odkazující na položce prostředků písma – je ekvivalentní k předchozí příklad kódu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odkazy na písma z stejném podadresáři aplikace  
 Můžete umístit obě aplikace obsahu a zdrojové soubory ve stejném podadresáři uživatelem definované projektu aplikace. Následující příklad souboru projektu zobrazuje stránku obsahu a definované ve stejném podadresáři prostředky písma.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Vzhledem k tomu, že obsah aplikace a písma jsou ve stejném podadresáři, odkaz písma je relativní vzhledem k obsahu aplikace. Následující příklady ukazují, jak odkazovat prostředků písma, pokud písmo je ve stejném adresáři jako aplikace.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Vytváření výčtu písem v aplikaci  
 Zobrazení výčtu písem jako položky prostředků ve vaší aplikaci, použijte buď <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> nebo <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metoda. Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metoda vrátí kolekci <xref:System.Windows.Media.FontFamily> objekty z umístění písma aplikace. V takovém případě aplikace obsahuje podadresáři s názvem "zdroje".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metoda vrátí kolekci <xref:System.Windows.Media.Typeface> objekty z umístění písma aplikace. V takovém případě aplikace obsahuje podadresáři s názvem "zdroje".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Vytvoření prostředku knihovny písma  
 Můžete vytvořit pouze prostředky knihovny, která obsahuje pouze písma – bez kódu je součástí tento typ projektu knihovny. Vytvoření pouze knihovny je běžné technika pro oddělení prostředky z aplikační kód, který používá je. To také umožňuje sestavení knihovny zahrnuty s více projekty aplikací. Následující příklad souboru projektu ukazuje části klíče projektu knihovny jen prostředků.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Odkazy na písma v knihovně prostředků  
 Chcete-li písmo v knihovně prostředků z vaší aplikace, musíte přidat předponu odkaz na písma s názvem sestavení knihovny. V takovém případě je sestavení prostředků písma "FontLibrary". Chcete-li samostatné název sestavení z odkazu v rámci sestavení, použijte znak ';'. Přidání následuje odkaz na název písma – klíčové slovo "Component" dokončení úplné odkaz na prostředek knihovny písma. Následující příklad kódu ukazuje, jak chcete-li písmo v sestavení prostředků knihovny.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  Tato sada SDK obsahuje sadu ukázka [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma, která můžete použít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Písma jsou definovány v knihovně jen prostředků. Další informace najdete v tématu [ukázkové sadě písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Omezení využití písma  
 Následující seznam popisuje několik omezení na balení a použití písem v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:  
  
-   **Vložení bity oprávnění písma:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací zkontrolujte nebo vynutit jakéhokoli písma vložení bity oprávnění. Najdete v článku [Introduction_to_Packing písem](#introduction_to_packaging_fonts) části Další informace.  
  
-   **Lokality písem původu:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují písma odkaz na protokolu http nebo ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  
  
-   **Absolutní identifikátor URI pomocí balíčku: zápis:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace neumožňují vytvářet <xref:System.Windows.Media.FontFamily> objektu programově pomocí "pack:" jako součást absolutní [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz na písmo. Například `"pack://application:,,,/resources/#Pericles Light"` je odkaz na neplatný písma.  
  
-   **Vkládání automatické písem:** během doby návrhu, neexistuje žádná podpora pro vyhledávání aplikace použití písem a automaticky vložení písem v prostředky aplikace.  
  
-   **Písmo podmnožin:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nepodporují vytvoření podmnožiny písma pro přenosné dokumenty.  
  
-   V případech, kde je nesprávný referenční, aplikace se vrátí k používání dostupné písmo.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [Typografii Microsoft: Odkazy, novinky a kontakty](http://www.microsoft.com/typography/links/)  
 [Specifikace OpenType](http://www.microsoft.com/typography/otspec/)  
 [Funkce písem OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Ukázkové sadě písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
