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
ms.openlocfilehash: 318972c20f6461489226e19b3e517ba0ac069b28
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933368"
---
# <a name="optimizing-performance-text"></a>Optimalizace výkonu: Text

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zahrnuje podporu pro prezentaci textu obsahu pomocí ovládacích prvků s bohatou [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkcí. Vykreslování textu můžete obecně rozdělit ve třech vrstvách:

1. Použití objektů <xref:System.Windows.Media.GlyphRun>apřímo. <xref:System.Windows.Documents.Glyphs>

2. <xref:System.Windows.Media.FormattedText> Použití objektu.

3. Použití ovládacích prvků na nejvyšší úrovni, například <xref:System.Windows.Controls.TextBlock> objektů a. <xref:System.Windows.Documents.FlowDocument>

Toto téma poskytuje doporučení pro výkon vykreslování textu.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Vykreslování textu na úrovni glyfů

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje rozšířenou podporu textu včetně značek na úrovni glyfů s přímým přístupem <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytit a uchovat text po formátování. Tyto funkce poskytují kritickou podporu pro různé požadavky na vykreslování textu v každém z následujících scénářů.

- Zobrazení dokumentů s pevným formátem

- Scénáře tisku.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako jazyk tiskárny zařízení.

  - Zapisovač dokumentů Microsoft XPS.

  - Předchozí ovladače tiskárny, výstup z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací do pevného formátu.

  - Formát zařazování tisku.

- Reprezentace dokumentu s pevným formátem, včetně klientů pro předchozí verze Windows a dalších výpočetních zařízení.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>a <xref:System.Windows.Media.GlyphRun> jsou navržené pro scénáře s pevným formátem a prezentace a tisku. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje několik prvků pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře <xref:System.Windows.Controls.Label> , jako například <xref:System.Windows.Controls.TextBlock>a. Další informace o rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénářích najdete v tématu [Typografie v](typography-in-wpf.md)subsystému WPF.

Následující příklady ukazují, jak definovat vlastnosti pro <xref:System.Windows.Documents.Glyphs> objekt v. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Objekt představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> V příkladech se předpokládá, že písma Arial, Courier New a Times New Roman se nainstalují do složky **C:\WINDOWS\Fonts** v místním počítači.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Použití DrawGlyphRun

Pokud máte vlastní ovládací prvek a chcete vykreslit glyfy, použijte <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> metodu.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje také služby nižší úrovně pro vlastní formátování textu prostřednictvím použití <xref:System.Windows.Media.FormattedText> objektu. Nejúčinnější způsob, jak vykreslování textu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nástroji, je vygenerování textového obsahu na úrovni glyfu pomocí <xref:System.Windows.Media.GlyphRun> <xref:System.Windows.Documents.Glyphs> a. Náklady na tuto efektivitu však představují ztrátu snadného použití formátovaného textu, což jsou integrované funkce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ovládacích prvků, <xref:System.Windows.Controls.TextBlock> například a <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Objekt FormattedText

<xref:System.Windows.Media.FormattedText> Objekt umožňuje nakreslit víceřádkový text, ve kterém je každý znak v textu možné formátovat individuálně. Další informace najdete v tématu [Kreslení formátovaného textu](drawing-formatted-text.md).

Chcete-li vytvořit formátovaný text, <xref:System.Windows.Media.FormattedText.%23ctor%2A> zavolejte konstruktor pro <xref:System.Windows.Media.FormattedText> vytvoření objektu. Po vytvoření počátečního formátovaného textového řetězce můžete použít rozsah stylů formátování. Pokud vaše aplikace chce implementovat své vlastní rozložení, <xref:System.Windows.Media.FormattedText> je objekt lepší volbou než použití ovládacího prvku, <xref:System.Windows.Controls.TextBlock>jako je například. Další informace o <xref:System.Windows.Media.FormattedText> objektu naleznete v tématu [Kreslení formátovaného textu](drawing-formatted-text.md) .

<xref:System.Windows.Media.FormattedText> Objekt poskytuje možnost formátování textu na nízké úrovni. Můžete použít více stylů formátování na jeden nebo více znaků. Například můžete zavolat <xref:System.Windows.Media.FormattedText.SetFontSize%2A> metodu a a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> změnit tak formátování prvních pět znaků v textu.

Následující příklad kódu vytvoří <xref:System.Windows.Media.FormattedText> objekt a vykreslí ho.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Ovládací prvky FlowDocument, TextBlock a Label

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje několik ovládacích prvků pro vykreslení textu na obrazovku. Každý ovládací prvek je zaměřený na jiný scénář a má svůj vlastní seznam funkcí a omezení.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument má dopad na výkon větší než TextBlock nebo popisek

Obecně platí, že <xref:System.Windows.Controls.TextBlock> element by měl být použit, pokud je vyžadována podpora omezeného textu, jako je například krátká [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]věta v. <xref:System.Windows.Controls.Label>dá se použít, když je potřeba podpora minimálního textu. Element je kontejner pro opětovné zpracování dokumentů, které podporují bohatou prezentaci obsahu, a proto má větší dopad na výkon než <xref:System.Windows.Controls.TextBlock> použití ovládacích prvků nebo <xref:System.Windows.Controls.Label>. <xref:System.Windows.Documents.FlowDocument>

Další informace o <xref:System.Windows.Documents.FlowDocument>najdete v tématu [Přehled flowového dokumentu](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Nepoužívejte TextBlock v FlowDocument

Prvek je odvozen z <xref:System.Windows.UIElement>. <xref:System.Windows.Controls.TextBlock> Element je odvozen z, což je méně <xref:System.Windows.UIElement>nákladné pro použití než objekt odvozený od <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Run> Pokud je to možné <xref:System.Windows.Documents.Run> , použijte <xref:System.Windows.Controls.TextBlock> místo pro <xref:System.Windows.Documents.FlowDocument>zobrazení textového obsahu v.

Následující ukázka kódu ukazuje dva způsoby nastavení textového obsahu v rámci <xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Nepoužívejte rutinu Run k nastavení vlastností textu

Obecně platí, že <xref:System.Windows.Documents.Run> použití v <xref:System.Windows.Controls.TextBlock> rámci je větší výkon než při použití explicitního <xref:System.Windows.Documents.Run> objektu. Pokud používáte <xref:System.Windows.Documents.Run> , abyste mohli nastavit vlastnosti textu, nastavte tyto vlastnosti přímo <xref:System.Windows.Controls.TextBlock> na místo.

Následující ukázka kódu znázorňuje tyto dva způsoby nastavení vlastnosti text, v tomto případě <xref:System.Windows.Controls.TextBlock.FontWeight%2A> vlastnost:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

V následující tabulce jsou uvedeny náklady na zobrazení 1000 <xref:System.Windows.Controls.TextBlock> objektů s a bez explicitního <xref:System.Windows.Documents.Run>.

|**Typ TextBlock**|**Čas vytvoření (MS)**|**Čas vykreslování (MS)**|
|------------------------|------------------------------|----------------------------|
|Vlastnosti textu pro nastavení spuštění|146|540|
|Vlastnosti textu nastavení TextBlock|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Vyhněte se vazbě na vlastnost Label. Content.

Představte si situaci, kdy <xref:System.Windows.Controls.Label> máte objekt, který se často aktualizuje <xref:System.String> ze zdroje. Když data <xref:System.Windows.Controls.Label> sváže <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.String> elementu se zdrojovým objektem, může docházet ke špatnému výkonu. Pokaždé, když <xref:System.String> se zdroj aktualizuje, Starý <xref:System.String> objekt se zahodí a nový <xref:System.String> se znovu vytvoří – protože <xref:System.String> objekt je neměnný, nedá se změnit. To zase způsobí, že <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Label> objekt zahodí původní obsah a znovu vygeneruje nový obsah, aby zobrazil nový <xref:System.String>.

Řešení tohoto problému je jednoduché. <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> Pokud není nastavená na vlastní <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> hodnotu, nahraďte pomocí data a datovou vlastnost navázáním na zdrojový řetězec. <xref:System.Windows.Controls.Label>

|**Vlastnost vázaná na data**|**Čas aktualizace (MS)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock. text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Hypertextový odkaz

<xref:System.Windows.Documents.Hyperlink> Objekt je element obsahu toku na úrovni inline, který umožňuje hostovat hypertextové odkazy v rámci obsahu toku.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Kombinování hypertextových odkazů v jednom objektu TextBlock

Můžete optimalizovat použití více <xref:System.Windows.Documents.Hyperlink> prvků seskupením mezi <xref:System.Windows.Controls.TextBlock>sebou. To pomáhá minimalizovat počet objektů, které vytvoříte v aplikaci. Například můžete chtít zobrazit více hypertextových odkazů, například následující:

MSN domů &#124; můj MSN

Následující příklad kódu ukazuje více <xref:System.Windows.Controls.TextBlock> prvků, které slouží k zobrazení hypertextových odkazů:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

Následující příklad kódu ukazuje efektivnější způsob zobrazení hypertextových odkazů, tentokrát pomocí jediného <xref:System.Windows.Controls.TextBlock>:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Zobrazení podtržení na hypertextových odkazech pouze u událostí MouseEnter

<xref:System.Windows.TextDecoration> Objekt je vizuální ozdobné, které lze přidat do textu. může však být náročné na výkon při vytváření instancí. Pokud provedete rozsáhlé použití <xref:System.Windows.Documents.Hyperlink> elementů, zvažte zobrazení podtržení pouze při aktivaci události, jako je <xref:System.Windows.ContentElement.MouseEnter> například událost. Další informace najdete v tématu [určení, zda je hypertextový odkaz podtržený](how-to-specify-whether-a-hyperlink-is-underlined.md).

Následující obrázek ukazuje, jak událost MouseEnter aktivuje podtržený hypertextový odkaz:

![Hypertextové odkazy zobrazující TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

Následující ukázka kódu ukazuje, že <xref:System.Windows.Documents.Hyperlink> je definován s podtržením a bez něj:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

V následující tabulce jsou uvedeny náklady na výkon při zobrazení <xref:System.Windows.Documents.Hyperlink> 1000 prvků s podtržením a bez něj.

|**Cíl**|**Čas vytvoření (MS)**|**Čas vykreslování (MS)**|
|-------------------|------------------------------|----------------------------|
|S podtržením|289|1130|
|Bez podtržení|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Funkce formátování textu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje služby formátování formátovaného textu, například automatické dělení slov. Tyto služby mohou ovlivnit výkon aplikace a měly by být použity pouze v případě potřeby.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Vyhnout se zbytečnému použití dělení slov

Automatické dělení slov najde zarážky spojovníků pro řádky textu a umožňuje další pozice zalomení řádků v <xref:System.Windows.Controls.TextBlock> objektech a. <xref:System.Windows.Documents.FlowDocument> Ve výchozím nastavení je funkce Automatické dělení slov v těchto objektech zakázaná. Tuto funkci můžete povolit nastavením vlastnosti IsHyphenationEnabled objektu na `true`. Povolení této funkce ale způsobí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , že se spustí interoperabilita modelu objektu komponenty (com), což může mít vliv na výkon aplikace. Doporučuje se, abyste automatické dělení nepoužívali, pokud ho nepotřebujete.

### <a name="use-figures-carefully"></a>Pečlivě používejte obrázky

<xref:System.Windows.Documents.Figure> Element představuje část obsahu toku, která může být absolutně umístěna v rámci stránky obsahu. V některých případech může dojít <xref:System.Windows.Documents.Figure> k automatickému přeformátování celé stránky, pokud je její poloha v konfliktu s obsahem, který je už stanovený. Můžete minimalizovat možnost zbytečného přeformátování buď seskupením <xref:System.Windows.Documents.Figure> prvků vedle sebe, nebo jejich deklaraci v blízkosti horního okraje obsahu ve scénáři s pevnou velikostí stránky.

### <a name="optimal-paragraph"></a>Optimální odstavec

Funkce optimálního odstavce <xref:System.Windows.Documents.FlowDocument> objektu odděluje odstavce tak, aby byly prázdné znaky distribuovány co nejrovnoměrněji. Ve výchozím nastavení je funkce optimálního odstavce zakázána. Tuto funkci můžete povolit nastavením <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> vlastnosti objektu na. `true` Povolení této funkce však ovlivní výkon aplikace. Doporučuje se, abyste funkci optimálních odstavců nepoužívali, pokud ji nepotřebujete.

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
