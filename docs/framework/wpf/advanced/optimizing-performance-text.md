---
title: 'Optimalizace výkonu: Text'
ms.date: 03/30/2017
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
ms.openlocfilehash: db0738008766343fa19454cac14e75b318663f34
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352766"
---
# <a name="optimizing-performance-text"></a>Optimalizace výkonu: Text
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje podporu pro prezentaci textový obsah prostřednictvím plně funkční [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ovládacích prvků. Lze obecně rozdělit vykreslování textu ve třech vrstvách:  
  
1.  Použití <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> objekty přímo.  
  
2.  Použití <xref:System.Windows.Media.FormattedText> objektu.  
  
3.  Použití vysoké úrovně ovládacích prvků, jako <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty.  
  
 Toto téma obsahuje doporučení ohledně výkonu pro vykreslování textu.  
  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Vykreslení textu na úrovni glyfů  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] podporuje rozšířené textové včetně úrovni piktogramu značky s přímým přístupem k <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytit a zachovat po formátování textu. Tyto funkce umožňují podpory se zásadním jiným textovým požadavky na vykreslování v každém z těchto scénářů.  
  
-   Zobrazování dokumentů pevného formátu.  
  
-   Tisk scénáře.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako jazyk tiskárny zařízení.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Předchozí ovladače tiskárny, výstup z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací na pevném formátu.  
  
    -   Formát zařazování tisku.  
  
-   Reprezentace pevného formátu dokumentu, včetně klientů k předchozím verzím sady [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a další výpočetní zařízení.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> jsou navrženy pro prezentaci pevného formátu dokumentu a tisku scénáře. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje několik elementů pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře, jako <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.TextBlock>. Další informace o rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře, naleznete v tématu [Typografie v rozhraní WPF](typography-in-wpf.md).  
  
 Následující příklady ukazují, jak definovat vlastnosti <xref:System.Windows.Documents.Glyphs> objekt [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Objekt představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. V příkladech se předpokládá, že Arial Kurýrní nové a časy New Roman písma jsou nainstalovány v **C:\WINDOWS\Fonts** složky na místním počítači.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>Pomocí DrawGlyphRun  
 Pokud máte vlastní ovládací prvek a chcete se vykreslují glyfy, použijte <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> metody.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje služby nižší úrovně pro formátování prostřednictvím vlastního textu <xref:System.Windows.Media.FormattedText> objektu. Nejúčinnější způsob vykreslení textu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je generováním textový obsah na úrovni piktogram pomocí <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun>. Ale náklady na této efektivity je ztráta snadno použitelné RTF, které jsou integrované funkce z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ovládací prvky, jako například <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>Objekt FormattedText  
 <xref:System.Windows.Media.FormattedText> Objekt umožňuje nakreslit více řádky textu, ve kterém každý znak v textu jednotlivě naformátovaná. Další informace najdete v tématu [kreslení textu ve formátu](drawing-formatted-text.md).  
  
 Chcete-li vytvořit formátovaný text, zavolejte <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktor k vytvoření <xref:System.Windows.Media.FormattedText> objektu. Po vytvoření počáteční formátovaný řetězec, můžete použít celou řadu formátování styly. Pokud aplikace chce implementovat vlastní rozložení, pak bude <xref:System.Windows.Media.FormattedText> objekt je vhodnější než použití ovládacího prvku, jako například <xref:System.Windows.Controls.TextBlock>. Další informace o <xref:System.Windows.Media.FormattedText> objektu, najdete v článku [kreslení textu ve formátu](drawing-formatted-text.md) .  
  
 <xref:System.Windows.Media.FormattedText> Objekt, který poskytuje nízké úrovně funkce pro formátování textu. Můžete změnit více styl na jeden nebo více znaků. Například lze zavolat i <xref:System.Windows.Media.FormattedText.SetFontSize%2A> a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody, chcete-li změnit formátování prvních pěti znaků v textu.  
  
 Následující příklad kódu vytvoří <xref:System.Windows.Media.FormattedText> objektu a vykreslí je.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument TextBlock a ovládací prvky popisku  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje více ovládacích prvků pro vykreslení textu na obrazovce. Každý ovládací prvek je zacílený na jiný scénář a má svůj vlastní seznam funkcí a omezení.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument ovlivňuje výkon více než prvku TextBlock nebo popisek  
 Obecně platí <xref:System.Windows.Controls.TextBlock> element by měl použít, pokud je text omezená podpora vyžadovat, například stručný větu v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> lze použít, když je nutné podporovat minimální text. <xref:System.Windows.Documents.FlowDocument> Elementu je kontejner pro znovu přizpůsobitelným dokumenty, které podporují bohatý prezentační obsahu a proto má větší dopad na výkon než při použití <xref:System.Windows.Controls.TextBlock> nebo <xref:System.Windows.Controls.Label> ovládacích prvků.  
  
 Další informace o <xref:System.Windows.Documents.FlowDocument>, naleznete v tématu [přehled toku dokumentů](flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>Vyhněte se použití TextBlock v FlowDocument  
 <xref:System.Windows.Controls.TextBlock> Element je odvozen od <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.Run> Element je odvozen od <xref:System.Windows.Documents.TextElement>, což je méně nákladný než <xref:System.Windows.UIElement>-odvozenému objektu. Pokud je to možné, použijte <xref:System.Windows.Documents.Run> spíše než <xref:System.Windows.Controls.TextBlock> pro zobrazení textu v obsahu <xref:System.Windows.Documents.FlowDocument>.  
  
 Následující příklad kódu ukazuje dva způsoby nastavení obsahu textu v rámci <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Vyhněte se použití spuštění můžete nastavit vlastnosti textu  
 Obecně platí, pomocí <xref:System.Windows.Documents.Run> v rámci <xref:System.Windows.Controls.TextBlock> je vyšší výkon než bez použití explicitní náročné <xref:System.Windows.Documents.Run> objektu. Pokud používáte <xref:System.Windows.Documents.Run> Pokud chcete nastavit vlastnosti text, nastavte tyto vlastnosti přímo na <xref:System.Windows.Controls.TextBlock> místo.  
  
 Následující příklad kódu znázorňuje tyto dva způsoby nastavení vlastnosti textu, v tomto případě <xref:System.Windows.Controls.TextBlock.FontWeight%2A> vlastnost:  
  
 [!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 Následující tabulka zobrazuje náklady na zobrazení 1000 <xref:System.Windows.Controls.TextBlock> objekty s a bez explicitního <xref:System.Windows.Documents.Run>.  
  
|**TextBlock – typ**|**Čas vytvoření (ms)**|**Vykreslení doba (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Nastavení vlastností textu|146|540|  
|TextBlock – nastavení vlastností textu|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Vyhněte se datová vazba ovládacího prvku vlastnost Label.Content  
 Představte si situaci, kdy máte <xref:System.Windows.Controls.Label> objekt, který se často aktualizuje z <xref:System.String> zdroje. Při vytváření datových vazeb <xref:System.Windows.Controls.Label> elementu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.String> zdrojový objekt, může dojít ke špatnému výkonu. Pokaždé, když zdroj <xref:System.String> se aktualizuje, starý <xref:System.String> objekt je zrušený a nový <xref:System.String> se znovu vytvoří – protože <xref:System.String> objektu je neměnný, nelze ji změnit. To pak způsobí, že <xref:System.Windows.Controls.ContentPresenter> z <xref:System.Windows.Controls.Label> objekt zrušíte jeho starý obsah a znovu vygenerovat nový obsah zobrazit nové <xref:System.String>.  
  
 Řešení tohoto problému je jednoduché. Pokud <xref:System.Windows.Controls.Label> není nastavená na vlastní <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> hodnota, nahraďte <xref:System.Windows.Controls.Label> s <xref:System.Windows.Controls.TextBlock> a svázat data jeho <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost zdrojový řetězec.  
  
|**Data svázána vlastnost**|**Čas aktualizace (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Hypertextový odkaz  
 <xref:System.Windows.Documents.Hyperlink> Je objekt, který vám umožní hostitele hypertextové odkazy do plovoucího obsahu toku na úrovni vložení obsahu elementu.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Kombinovat hypertextové odkazy do jednoho objektu TextBlock  
 Můžete optimalizovat použití více <xref:System.Windows.Documents.Hyperlink> prvky jejich seskupením společně v rámci stejného <xref:System.Windows.Controls.TextBlock>. Pomůžete tím minimalizovat počet objektů, které vytvoříte ve vaší aplikaci. Chcete třeba zobrazit více hypertextové odkazy, jako je následující:  
  
 Domovská stránka služby MSN &#124; Moje MSN  
  
 Následující příklad kódu ukazuje více <xref:System.Windows.Controls.TextBlock> prvků, které slouží k zobrazení hypertextové odkazy:  
  
 [!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 Následující příklad kódu ukazuje efektivnější způsob zobrazení hypertextové odkazy, tentokrát pomocí jediného <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Ukazuje na hypertextové odkazy pouze na události MouseEnter podtržení  
 A <xref:System.Windows.TextDecoration> objektu je vizuální dekoru, můžete přidat do textu, však může být pro vytvoření instance náročné na výkon. Pokud provedete rozsáhlé používání šířky <xref:System.Windows.Documents.Hyperlink> prvky, vezměte v úvahu zobrazující podtržení jenom v případě, že se aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí. Další informace najdete v tématu [podtržený zadejte hypertextového odkazu](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
 ![Hypertextové odkazy zobrazení TextDecorations](./media/textdecoration03.png "TextDecoration03")  
Povolí, v MouseEnter hypertextový odkaz  
  
 Následující ukázkový kód <xref:System.Windows.Documents.Hyperlink> definována a nemusíte podtržení:  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Následující tabulka zobrazuje náklady na zobrazení 1000 <xref:System.Windows.Documents.Hyperlink> elementy a nemusíte podtržení.  
  
|**Hypertextový odkaz**|**Čas vytvoření (ms)**|**Vykreslení doba (ms)**|  
|-------------------|------------------------------|----------------------------|  
|S podtržení|289|1130|  
|Bez podtržení|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Funkce formátování textu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje služby, jako je automatické dělení slov RTF. Tyto služby mohou ovlivnit výkon aplikace a by měla sloužit pouze v případě potřeby.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Vyhněte se zbytečným použití dělení slov  
 Automatické dělení slov vyhledá spojovník zarážky řádků textu a umožňuje další zalomení pozice pro řádky v <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty. Ve výchozím nastavení je funkce Automatické dělení slov zakázaná v těchto objektů. Tuto funkci lze povolit nastavením vlastnosti objektu IsHyphenationEnabled na `true`. Povolení této funkce však způsobí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k zahájení [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] vzájemná funkční spolupráce, což může ovlivnit výkon aplikace. Doporučuje se, že je velmi riskantní používat automatické dělení slov pokud ho potřebujete.  
  
### <a name="use-figures-carefully"></a>Používejte opatrně, obrázky  
 A <xref:System.Windows.Documents.Figure> element reprezentuje část plovoucího obsahu, který může být absolutně umístěné v rámci stránky obsahu. V některých případech <xref:System.Windows.Documents.Figure> může způsobit celé stránky automaticky přeformátovat pokud jeho pozice koliduje s obsahem, který již byl podle předem. Můžete minimalizovat zbytečné přeformátování buď seskupením možnost <xref:System.Windows.Documents.Figure> prvky vedle sebe nebo deklarace v horní části obsahu ve scénáři velikost pevné stránky.  
  
### <a name="optimal-paragraph"></a>Optimální odstavce  
 Funkci optimální odstavce <xref:System.Windows.Documents.FlowDocument> objekt rozložen odstavce tak, aby se jako rovnoměrně distribuuje prázdné znaky. Ve výchozím nastavení optimální odstavec je zakázaná. Tuto funkci lze povolit nastavením objektu <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> vlastnost `true`. Povolení této funkce však ovlivňuje výkon aplikace. Je doporučeno, je velmi riskantní používat funkci optimální odstavec pokud ho potřebujete.  
  
## <a name="see-also"></a>Viz také:
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
