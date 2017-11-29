---
title: "Optimalizace výkonu: Text"
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
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 43fe1f9fa5189a3dfd5f700660f0528592382510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-text"></a>Optimalizace výkonu: Text
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zahrnuje podporu pro prezentaci textového obsahu prostřednictvím bohaté funkce [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ovládací prvky. Obecně lze rozdělit vykreslování textu v tři vrstvy:  
  
1.  Pomocí <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> objekty přímo.  
  
2.  Pomocí <xref:System.Windows.Media.FormattedText> objektu.  
  
3.  Použití vysoké úrovně ovládacích prvků, například <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty.  
  
 Toto téma obsahuje doporučení výkonu vykreslování textu.  
  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Vykreslení textu na úrovni glyfy  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu rozšířené textové včetně značek glyfy úrovni s přímým přístupem k <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytávat a zachovat po formátování textu. Tyto funkce podporují kritické jiným textovým vykreslování požadavky v každé z následujících scénářů.  
  
-   Zobrazování dokumentů pevného formátu.  
  
-   Tisk scénáře.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako jazyk tiskárny zařízení.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Předchozí ovladače tiskárny, výstup z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace do pevné formátu.  
  
    -   Formát zařazování tisku.  
  
-   Reprezentace-formátovat dokument, včetně klientů pro předchozí verze [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a dalších výpočetních zařízení.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>a <xref:System.Windows.Media.GlyphRun> jsou navrženy pro tiskové scénáře a prezentace-formátovat dokument. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje několik elementy pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře, jako <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.TextBlock>. Další informace o rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře, najdete v článku [typografii v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
 Následující příklady ukazují, jak definovat vlastnosti <xref:System.Windows.Documents.Glyphs> objekt v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Objekt představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. V příkladech se předpokládá, že písem Arial, Kurýrní nové a časy New Roman jsou nainstalovány ve **C:\WINDOWS\Fonts** složky v místním počítači.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>Pomocí DrawGlyphRun  
 Pokud máte vlastní ovládací prvek a chcete vykreslit glyfů, použijte <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> metoda.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také poskytuje nižší úrovně služby pro vlastní text formátování prostřednictvím <xref:System.Windows.Media.FormattedText> objektu. Nejúčinnější způsob vykreslování textu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je vygenerováním textový obsah na úrovni glyfy pomocí <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun>. Náklady na této efektivity je však ztrátu snadno použitelný RTF, které jsou integrované funkce služby [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ovládací prvky, jako například <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>Objekt FormattedText  
 <xref:System.Windows.Media.FormattedText> Objekt umožňuje kreslení víceřádkový text, ve kterém lze jednotlivé znaky v textu jednotlivě formátovat. Další informace najdete v tématu [kreslení textu ve formátu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
 Chcete-li vytvořit formátovaný text, zavolejte <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktor k vytvoření <xref:System.Windows.Media.FormattedText> objektu. Po vytvoření počáteční formátovaný textový řetězec, můžete použít řadu formátování stylů. Pokud aplikace chce implementovat vlastní rozložení, pak se <xref:System.Windows.Media.FormattedText> objekt je vhodnější než pomocí ovládacího prvku, jako třeba <xref:System.Windows.Controls.TextBlock>. Další informace o <xref:System.Windows.Media.FormattedText> objektu, najdete v části [kreslení textu ve formátu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md) .  
  
 <xref:System.Windows.Media.FormattedText> Objekt poskytuje možnost formátování textu, nízké úrovně. Více formátování styly můžete aplikovat na jeden nebo více znaků. Například může volat i <xref:System.Windows.Media.FormattedText.SetFontSize%2A> a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody pro změnu formátování prvních 5 znaků v textu.  
  
 Následující příklad kódu vytvoří <xref:System.Windows.Media.FormattedText> objektu a vykreslí je.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument TextBlock a ovládací prvky popisek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje více ovládacích prvků pro kreslení textu na obrazovce. Každý ovládací prvek je zaměřena na jiný scénář a má svou vlastní seznam funkcí a omezení.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument ovlivňuje výkon více než TextBlock nebo popisek  
 Obecně <xref:System.Windows.Controls.TextBlock> element byste měli použít, pokud text omezenou podporu vyžadovat, například stručný věty v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>můžete použít, když je potřebná podpora minimální text. <xref:System.Windows.Documents.FlowDocument> Element je kontejner pro znovu přizpůsobitelným dokumenty, které podporují bohaté prezentace obsahu a proto má dopad na vyšší výkon než při použití <xref:System.Windows.Controls.TextBlock> nebo <xref:System.Windows.Controls.Label> ovládací prvky.  
  
 Další informace o <xref:System.Windows.Documents.FlowDocument>, najdete v části [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>Nepoužívejte TextBlock v FlowDocument  
 <xref:System.Windows.Controls.TextBlock> Element je odvozený od <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.Run> Element je odvozený od <xref:System.Windows.Documents.TextElement>, což je levnější než <xref:System.Windows.UIElement>-odvozené objektu. Pokud je to možné, použijte <xref:System.Windows.Documents.Run> místo <xref:System.Windows.Controls.TextBlock> pro zobrazení obsahu v textu <xref:System.Windows.Documents.FlowDocument>.  
  
 Následující příklad kódu ukazuje dva způsoby nastavení textového obsahu v rámci <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Nepoužívejte spustit nastavení vlastností textu  
 Obecně platí, pomocí <xref:System.Windows.Documents.Run> v rámci <xref:System.Windows.Controls.TextBlock> je další výkon náročné než není použití explicitního <xref:System.Windows.Documents.Run> objektu vůbec. Pokud používáte <xref:System.Windows.Documents.Run> aby bylo možné nastavit vlastnosti textu, nastavte tyto vlastnosti přímo na <xref:System.Windows.Controls.TextBlock> místo.  
  
 Následující příklad kódu ukazuje tyto dva způsoby nastavení vlastnosti typu text, v takovém případě <xref:System.Windows.Controls.TextBlock.FontWeight%2A> vlastnost:  
  
 [!code-xaml[Performance#PerformanceSnippet12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 V následující tabulce jsou náklady na zobrazení 1000 <xref:System.Windows.Controls.TextBlock> objekty s i bez explicitního <xref:System.Windows.Documents.Run>.  
  
|**Typ TextBlock**|**Čas vytvoření (ms)**|**Vykreslení čas (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Spustit nastavení vlastností textu|146|540|  
|Nastavení vlastností textu TextBlock|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Vyhněte se datové vazby pro vlastnost Label.Content  
 Představte si situaci, kdy máte <xref:System.Windows.Controls.Label> objekt, který je často aktualizována z <xref:System.String> zdroje. Pokud datová vazba <xref:System.Windows.Controls.Label> elementu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost, která má <xref:System.String> zdrojový objekt, může dojít k nižšímu výkonu. Pokaždé, když zdroji <xref:System.String> aktualizuje, starý <xref:System.String> objekt je zrušených a nové <xref:System.String> se znovu vytvoří – protože <xref:System.String> objekt se nedá změnit, nelze jej změnit. To, se pak způsobí, že <xref:System.Windows.Controls.ContentPresenter> z <xref:System.Windows.Controls.Label> objekt zrušíte jeho původní obsah a znovu vygenerovat nový obsah zobrazíte nové <xref:System.String>.  
  
 Řešení tohoto problému je jednoduché. Pokud <xref:System.Windows.Controls.Label> není nastavený na vlastní <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> hodnotu, nahraďte <xref:System.Windows.Controls.Label> s <xref:System.Windows.Controls.TextBlock> a vazby dat jeho <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost, která má zdrojový řetězec.  
  
|**Data vázaný vlastnost**|**Čas aktualizace (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Hypertextový odkaz  
 <xref:System.Windows.Documents.Hyperlink> Je objekt na úrovni toku obsahu element, který umožňuje hostitele hypertextové odkazy v rámci toku obsahu.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Kombinování hypertextové odkazy v jeden objekt TextBlock  
 Můžete optimalizovat použití více <xref:System.Windows.Documents.Hyperlink> elementy tím, že je společně v rámci stejné <xref:System.Windows.Controls.TextBlock>. To pomůže minimalizovat počet objektů, které vytvoříte v aplikaci. Můžete například zobrazit více hypertextové odkazy, například následující:  
  
 Domovská stránka MSN &#124; Moje MSN  
  
 Následující příklad kódu ukazuje několik <xref:System.Windows.Controls.TextBlock> elementy, které slouží k zobrazení hypertextových odkazů:  
  
 [!code-xaml[Performance#PerformanceSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 Následující příklad kódu ukazuje efektivnější způsob zobrazení hypertextové odkazy, tentokrát pomocí jedné <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xaml[Performance#PerformanceSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Zobrazuje podtržení na hypertextové odkazy jenom na MouseEnter – události  
 A <xref:System.Windows.TextDecoration> objektu je visual dekoru, který můžete přidat na text, však může být náročné vytvořit instanci výkonu. Pokud provedete rozsáhlé používání šířky <xref:System.Windows.Documents.Hyperlink> prvky, zvažte zobrazující podtržení jenom v případě, že aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí. Další informace najdete v tématu [určit, zda hypertextový odkaz je podtržený](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
 ![Hypertextové odkazy zobrazující objekty TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hypertextový odkaz, které jsou uvedeny na MouseEnter  
  
 Následující kód ukazuje ukázka <xref:System.Windows.Documents.Hyperlink> definované s i bez podtržení, které:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Následující tabulka uvádí náklady výkonu zobrazení 1000 <xref:System.Windows.Documents.Hyperlink> elementy a bez podtržení.  
  
|**Hypertextový odkaz**|**Čas vytvoření (ms)**|**Vykreslení čas (ms)**|  
|-------------------|------------------------------|----------------------------|  
|S podtržení|289|1130|  
|Bez podtržení|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Funkce formátování textu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje RTF služby, jako je automatické dělení slov. Tyto služby mohou ovlivnit výkon aplikace a musí být použit pouze v případě potřeby.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Vyhněte se použití nepotřebné dělení  
 Automatické dělení slov vyhledá pomlčka zarážky řádků textu a umožňuje pozic další zalomení řádků v <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty. Ve výchozím nastavení je funkce automatického dělení slov v tyto objekty zakázán. Můžete povolit tuto funkci nastavením vlastnosti objektu IsHyphenationEnabled `true`. Povolení této funkce však způsobí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahájíte [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] interoperabilitu, která může ovlivnit výkon aplikace. Doporučuje se, že nepoužijete automatické dělení slov Pokud to potřebujete.  
  
### <a name="use-figures-carefully"></a>Pečlivě dodržujte následující obrázky  
 A <xref:System.Windows.Documents.Figure> element reprezentuje část obsah toku, který může být absolutně umístěný v rámci stránky obsahu. V některých případech <xref:System.Windows.Documents.Figure> může způsobit celou stránku automaticky přeformátuje, pokud jeho pozice koliduje s obsahem, který je již umístěné na více systémů. Můžete minimalizovat možnost nepotřebné přeformátování pomocí buď seskupení <xref:System.Windows.Documents.Figure> elementy vedle sebe, nebo je deklarace v horní části obsahu ve scénáři stránka pevnou velikost.  
  
### <a name="optimal-paragraph"></a>Optimální odstavce  
 Funkci optimální odstavce <xref:System.Windows.Documents.FlowDocument> objekt rozložen odstavců tak, aby prázdné místo je rozděleno rovnoměrně možné. Funkce optimální odstavce je ve výchozím nastavení vypnutá. Můžete povolit tuto funkci nastavením objektu <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> vlastnost `true`. Povolení této funkce však ovlivňuje výkon aplikace. Doporučuje se, že použijete funkci optimální odstavce Pokud to potřebujete.  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a vytvoření bitové kopie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Chování objektů](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další doporučení výkonu](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
